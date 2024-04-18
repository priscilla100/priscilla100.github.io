---
title: "Travel the Same Path: A Novel TSP Solving Strategy"
tags:
- "Deep Learning"
- "Optimization"
date: Jan. 2022 - Apr. 2022
path: "research/TSP-a-novel-TSP-solving-strategy"
excerpt: "Exploring a novel approach to ***exactly*** solve an NP-hard combinatorial optimization problem by using *imitation learning*."
selected: false
cover: "./preview.png"
links:
  - name: "GitHub"
    url: "https://github.com/sleepymalc/Travel-the-Same-Path"
  - name: "arXiv"
    url: "https://arxiv.org/abs/2210.05906"
---

## Introduction

I stepped upon an interesting paper: [*Exact Combinatorial Optimization with Graph Convolutional Neural Networks*](https://arxiv.org/abs/1906.01629) a while ago. In this work, the authors provided a novel methodology for solving mixed integer linear programming with the help of machine learning leveraging the insight of *speeding up only a specific part of the **exact** algorithm might preserve exactness*.[^1]

[^1]: There are a bunch of similar works out there trying to achieve this, however, by the nature of machine learning algorithms, all of them fail to provide an exact solution.

This idea is interesting enough, so I decided to implement it and turn it into a small project. I focused on a specific, well-known TCS problem: the [traveling salesman problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem), also known as *TSP*.

> The [report](https://arxiv.org/abs/2210.05906) and the [code](https://github.com/sleepymalc/Travel-the-Same-Path) for this project are available.

### Preliminary

We will utilize GCNN (Graph Convolutional Neural Network), a particular kind of GNN, together with imitation learning to solve TSP. In particular, we focus on the generalization ability of models trained on small-sized problem instances.

#### Integer Linear Programming Formulation of TSP

We first formulate TSP in terms of integer linear programming.[^2] Given an undirected weighted group $\mathcal{G} = (\mathcal{E}, \mathcal{V})$,
we label the nodes with numbers $1, \ldots, n$ and define
$$
	x_{ij}\coloneqq \begin{dcases}
		1, & \text{if }(i, j)\in \mathcal{E}^\prime                       \\
		0, & \text{if } (i, j)\in \mathcal{E}\setminus\mathcal{E}^\prime,
	\end{dcases}
$$
where $\mathcal{E}^\prime\subset \mathcal{E}$ is a variable which can be viewed as a compact representation of all variables $x_{ij}$, $\forall i, j$.
Furthermore, we denote the weight on edge $(i, j)$ by $c_{ij}$, then for a particular TSP problem instance, we can formulate the problem as
$$
	\begin{aligned}
\min & \sum_{i=1}^{n}\sum *{j\neq i,j=1}^{n}c*{ij}x_{ij} &  &                      \\
& \sum_{i=1,i\neq j}^{n}x_{ij}=1                    &  & j=1,\ldots ,n;       \\
& \sum_{j=1,j\neq i}^{n}x_{ij}=1                    &  & i=1,\ldots ,n;       \\
		     & u_{i}-u_{j}+nx_{ij}\leq n-1                        &  & 2\leq i\neq j\leq n; \\
		     & 1\leq u_{i}\leq n-1                                &  & 2\leq i\leq n;       \\
		     & x_{ij}\in \{0,1\}                                  &  & i,j=1,\ldots ,n;     \\
		     & u_{i}\in \mathbb{Z}                                &  & i=2,\ldots ,n
	\end{aligned}
$$
given by Miller-Tucker-Zemlin.

[^2]: The formation detail is omitted here.

#### Branch and Bound

We then solve TSP as the above ILP formulation by **branch and bound**. It's possible to do branch and bound sufficiently by choosing a good branch strategy,
and since branching and bound involves *performing a series of branching strategies*, we model this as **Markov Decision Process (MDP)** in its nature.

Now, our goal is clear: We want to learn from an expert (in this case, a SOTA modern solver $\texttt{SCIP}$), which is typically called **imitating learning**.

### Pipeline

Our learning pipeline is as follows. We first create some random TSP instances and turn them into ILP,
then we use imitation learning to learn how to choose the **branching target** at each branching.
Our GNN model produces a set of actions with the probability corresponding to each possible action (in our case, which variable to branch). We then
use **Cross-Entropy Loss** to compare our prediction to the result produced by $\texttt{SCIP}$ and complete one iteration.

<div align="center">
	<img src="./figures/pipeline.png"/>
</div>

#### Graph Convolutional Neural Network (GCNN)

One may wonder where the GNN is involved in our methodology, is it used to model the topology of the nodes of a particular TSP instance?

The answer is **no**. The GCNN is our model which learns how to perform branching given the state of the problem (e.g., given the current state of the explored
recursion tree of the branch and bound algorithm). Intuitively, in the pipeline graph above,

* Top-left corresponds to TSP instances (red dots corresponding to actual cities in the TSP problem).
* Bottom-left corresponds to our model (black dots corresponding to a node in our GCNN).

Now, it should be clear how we utilize GNN to help us solve this TSP problem: We use GCNN to learn a
strong branching strategy and use it to do branching whenever needed.

### Experimental Result

We look at the walltime needed for the model trained on TSP10/TSP15 and tested on TSP25 for 100 instances (ordered by the walltime of $\texttt{SCIP}$).

<div align="center">
	<img src="./figures/result/tsp10/normal.png" width="50%"/>
	<img src="./figures/result/tsp15/normal.png" width="50%"/>
</div>

If we zoom in to the first 80 and last 20 instances, we have the following.
<div align="center">
	<img src="./figures/result/tsp10/zoom-first80.png" width="50%"/>
	<img src="./figures/result/tsp10/zoom-last20.png" width="50%"/>
	<img src="./figures/result/tsp15/zoom-first80.png" width="50%"/>
	<img src="./figures/result/tsp15/zoom-last20.png" width="50%"/>
</div>

#### Generalization Ability

We observe that our TSP10 and TSP15 imitation models outperform the $\texttt{SCIP}$ solver on baseline test instances, and **successfully generalize to TSP15, TSP20, and TSP25**. They perform significantly better on average than $$\texttt{SCIP}$$ in difficult-to-solve TSPs as compared to easier instances. They also perform better in cases of larger test instances like TSP20 and TSP25 as compared to TSP10 and TSP15. This might be due to an inherent subset structure between TSP10 and TSP20 instances, and similarly, TSP15 and TSP25 instances which might not be the case for smaller test sizes.[^3]

[^3]: Unlike other problems, when we formulate TSP as an ILP, the problem size is growing **quadratically**. In other words, when we look at the model performance, the generalization ability from TSP10 to TSP25 is not a $2.5\times$, but rather a $6\times$ generalization in our formulation. By adapting this methodology to a more sophisticated algorithm that formulates TSP linearly, the generalization ability should remain, and the performance will be even better in terms of TSP sizes.

#### Bottlenecks and Future Work

There is a huge performance difference between our proposed model (also $\texttt{SCIP}$) and the SOTA TSP solver, $\texttt{Concorde}$. Since the proposed model's backbone is the branch and bound algorithm, by formulating TSP into an ILP, we lost some useful problem structures that can be further exploited by algorithms used in $\texttt{Concorde}$. But the existence of a similar pattern of growth in solving time for more difficult instances of larger TSP sizes even for $\texttt{Gurobi}$ and $\texttt{Concorde}$ is promising, as our imitation model applied to these solvers should lead to similar time improvements.[^4]

[^4]: A major bottleneck is that SOTA solvers like $\texttt{Gurobi}$, or $\texttt{Concorde}$, are often licensed, hence not open-sourced. This results in the difficulty of utilizing a stronger baseline and learning from which to get further improvement.

### Conclusion

For nearly all exact optimization solving algorithms, there is some kind of *exhaustion* going on, which usually involves decision-making when executing the algorithm.

> For example, the cutting plane algorithm also involves decision-making on variables when it needs to choose a variable to cut.

Hence, it's possible to generalize this methodology to not only the branch and bound algorithm but a wide range of the existing exact optimization algorithms.
