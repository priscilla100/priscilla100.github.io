---
title: "G.color()"
tags: ["math", "random"]
date: 2024-12-19
path: "posts/Coloring"
excerpt: 🎨 Coloring a 3-colorable graph.
cover: "./preview.png"
---

## Coloring a 3-Colorable Graph

In the Fall 2024 semester, I took an advanced graph algorithm course at University of Illinois Urbana-Champaign just for fun. The space here is too little, so I'll ask you to move to my [note](../Notes/#fall-2024) to get a better idea of the course. Here, I want to share something more specific: the final project I and [Sean Liu](https://zhxnliu.me/about/) worked on, which is basically a literature review of a cute line of work about **graph coloring**.

## The Problem

Given an undirected $3$-colorable graph $G = (V, E)$, we would like to color $G$ with the least number of colors efficiently. Recently, Professor [Kawarabayashi](https://kklab.nii.ac.jp/en/), who I know during my intern at NII, worked on this problem extensively and got several exciting results on this problem, where they are able to break the natural barrier of $\widetilde{O} (n^{0.2})$ colors down to $\widetilde{O} (n^{0.19747})$ colors [KTY24](https://arxiv.org/abs/2406.00357).

In this blog post, we will review the literature and try to grasp the high level idea of the history of the problem and how the breakthrough is made. The complete [report](./Coloring.pdf) version is also available.

### Background

This problem was first proposed by Wigderson [Wig83](https://dl.acm.org/doi/10.1145/2157.2158), and we shall see how balancing combinatorial with semi-definite programming (SDP) methods leads to a natural $O(n^{0.5})$ bound, and how this was first broken [KT17](https://dl.acm.org/doi/10.1145/3001582). We focus on the combinatorial side, specifically Blum's contributions [Blu94](https://dl.acm.org/doi/10.1145/176584.176586) that laid the groundwork for most of Kawarabayashi etal.'s later breakthroughs [KT12](https://arxiv.org/abs/1205.1254) [KT17](https://dl.acm.org/doi/10.1145/3001582) [KTY24](https://arxiv.org/abs/2406.00357).

### General Strategy

One of the most important notions in this line of work originates from Blum's *progress towards $k$-coloring* [Blu94](https://dl.acm.org/doi/10.1145/176584.176586). While deferring the exact definition, the general idea is that if it is always possible to make progress (towards some fixed $k$) for any $3$-colorable graph, then we can $\widetilde{O}(k)$-color any $3$-colorable graph in polynomial time. An interesting aspect of this line of work is that, under different regimes, two different approaches dominate one another. The best bound is obtained by balancing between them via choosing an appropriate $\Delta$: specifically, for any parameter $\Delta$, it suffices to make progress under either a minimum degree $\Delta = \Delta_{\min}$ or maximum degree $\Delta = \Delta_{\max}$ constraint [AC06](https://dl.acm.org/doi/10.1145/1132516.1132548) [BK97](https://dl.acm.org/doi/10.1016/S0020-0190(96)00190-1) [KT17](https://dl.acm.org/doi/10.1145/3001582).

## Known Results

Assuming that for a $3$-colorable graph with minimum degree $\Delta_{\min} = n^{1 - \Omega(1)}$, a series of bounds from past literature for progress follows a sequence of the form:
$$
\widetilde{O}\left(\left(n/\Delta_{\min}\right)^{i/(2i-1)}\right),
$$
including $\widetilde{O}(n/\Delta_{\min})$ by Wigderson [Wig83](https://dl.acm.org/doi/10.1145/2157.2158) for $i=1$, $\widetilde{O}((n/\Delta_{\min})^{2/3})$ and $\widetilde{O}((n/\Delta_{\min})^{3/5})$ for $i = 2$ and $3$ by Blum [Blu94](https://dl.acm.org/doi/10.1145/176584.176586), and finally $\widetilde{O}((n/\Delta_{\min})^{4/7})$ for $i = 4$ by Kawarabayashi and Thorup [KT12](https://arxiv.org/abs/1205.1254).

### Combinatorial Bounds for High Minimum Degree

The first series of bounds implied by the general bound stems from the simple observation that we may assume the minimum degree $\Delta_{\min} \geq k$ given any targeted coloring number. This is because it is trivial to color the rest of the graph after coloring vertices with a degree exceeding $k$. Hence, from the general bound for $i = [4]$, $\Delta_{\min} \geq k = (n/\Delta_{\min})^{i / (2i-1)} \iff \Delta_{\min} \geq n^{i / (3i-1)}$, which yields an $\widetilde{O}(n^{i/(3i-1)})$ bound for any $\Delta_{\min} \geq n^{i/(3i-1)}$. Thus, we get $\widetilde{O}(n^{1/2})$ for $i=1$ [Wig83](https://dl.acm.org/doi/10.1145/2157.2158), $\widetilde{O}(n^{2/5})$ and $\widetilde{O}(n^{3/8})$ for $i=2$ and $3$, respectively [Blu94](https://dl.acm.org/doi/10.1145/176584.176586), and $\widetilde{O}(n^{4/11})$ for $i=4$ [KT12](https://arxiv.org/abs/1205.1254).

### SDP Bounds for Low Maximum Degree

For $3$-colorable graphs with maximum degree $\Delta_{\max}$, Karger etal. [KMS98](https://arxiv.org/abs/cs/9812008) used SDP to achieve $O(\Delta_{\max}^{1/3})$ colors. Combining with the general bound, one can color $3$-colorable graphs with $\widetilde{O}(n^{i/(5i-1)})$ colors for $i \in [4]$ by balancing $\Delta_{\max}^{1/3}$ and $(n/\Delta_{\min})^{i/(2i-1)}$ [BK97](https://dl.acm.org/doi/10.1016/S0020-0190(96)00190-1). In particular, the following general lemma for balancing is known:

>**Lemma (Balancing [KT17](https://dl.acm.org/doi/10.1145/3001582)).** Suppose for some near-polynomial $d$ and $f$ that for any $n$, we can make progress towards an $\widetilde{O}(f(n))$ coloring for any $3$-colorable graph with either $\Delta_{\min} \geq d(n)$; or $\Delta_{\max} \leq d(n)$, then we can make progress towards $\widetilde{O}(f(n))$-coloring on any $3$-colorable graph.

This gives $\widetilde{O}(n^{1/4})$ for $i=1$ and $\widetilde{O}(n^{3/14}) = \widetilde{O}(n^{0.2142})$ for $i = 3$. We omit $i=4$ [KT12](https://arxiv.org/abs/1205.1254) as this appears much later, and further improvements on the SDP bounds have already been achieved. As the general bound converges to $\widetilde{O}((n/\Delta_{\min})^{1/2})$ from above, the bound $\widetilde{O}(n^{1/5})$ emerges as a natural barrier. Later improvements in SDP combined with Blum's result [Blu94](https://dl.acm.org/doi/10.1145/176584.176586) suggest a similar barrier: Arora etal. [AC06](https://dl.acm.org/doi/10.1145/1132516.1132548) achieved $O(n^{0.2111})$ colors based on the sparsest cut SDP [ARV09](https://dl.acm.org/doi/10.1145/1502793.1502794), while Chlamtac [Chl07](https://ieeexplore.ieee.org/document/4389537) further improved it to $O(n^{0.2072})$. Both results rely on bounds of the form $O(\Delta_{\max}^{1/3 - \varepsilon(n, \Delta_{\max})})$, where $\varepsilon(n, \Delta) > 0$ is a small value that decreases as a complex function of $\Delta$. With these new SDP results, the combinatorial bound $\widetilde{O}(n^{4/11})$ for $i=4$ yields a final bound of $\widetilde{O}(n^{0.2049})$ colors [KT12](https://arxiv.org/abs/1205.1254).

### Balancing

A more careful treatment of balancing different regimes finally leads to a breakthrough: while the general bound converges to $\widetilde{O}((n/\Delta_{\min})^{1/2})$ from above with the natural condition $\Delta_{\min} \geq n^{1/3}$, if our goal is to balance it with the SDP bounds such as $\Delta_{\max}^{1/3}$, the general bound only needs to hold when $\Delta_{\min} \geq n^{3/5}$. This idea is exploited in [KT17](https://dl.acm.org/doi/10.1145/3001582) to show that the general bound holds for $i=12$ when $\Delta_{\min} \geq n^{0.61674333}$. Combining the best current SDP bound [Chl07](https://ieeexplore.ieee.org/document/4389537), this yields an overall coloring bound of $\widetilde{O}(n^{0.19996})$, breaking the $\widetilde{O}(n^{1/5})$ barrier. The latest advancement[KTY24](https://arxiv.org/abs/2406.00357) further improves the combinatorial bound, where the limit of the general bound, i.e., $\widetilde{O}((n/\Delta)^{1/2})$, can be approached arbitrarily when $\Delta_{\min} > \sqrt{n}$:

>**Theorem[KTY24](https://arxiv.org/abs/2406.00357).** For any $3$-colorable graph with $\Delta_{\min} > n^{0.5}$, we can make progress towards a $k$-coloring for some $k = 2^{(\log \log n)^2} \sqrt{n/\Delta_{\min}}$ in polynomial time.

Combining the above theorem with the best SDP bound [Chl07](https://ieeexplore.ieee.org/document/4389537) at $\Delta_{\min} = n^{0.605073}$, an $\widetilde{O}(n^{0.19747})$-coloring can also be found in polynomial time.
