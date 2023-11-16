---
title: "Modeling Fair Redistricting Commissions"
tags:
- "Game Theory"
- "Fairness"
date: Jan. 2023 - Apr. 2023
path: "research/Modeling-Fair-Redistricting-Commissions"
excerpt: "We resolved *Gerrymandering* by a simple (dumb) voting scheme..."
selected: true
cover: "./preview.png"
links:
  - name: "Paper"
    url: "./research/Modeling-Fair-Redistricting-Commissions/paper.pdf"
  - name: "Poster"
    url: "./research/Modeling-Fair-Redistricting-Commissions/poster.pdf" 
---

## Introduction

In the last semester of my bachelor's journey, I decided to take a course about algorithmic game theory. In the end, we did this fun, small project with [Henry Fleischmann](https://hfleischmann3.github.io./), where we managed to design a mechanism that addresses the *gerrymandering*[^1] problem, proving it has the desired properties. The following is a quick summary of our project.

> The [report](./paper.pdf) and the [poster](./poster.pdf) for this project are available.

## The Model

We describe our model of the problem. Our goal is to design a *fair* rule to get a redistricting map based on a selected group of commissioners while being aware that

1. There are three types of commissioners, i.e., independent commissioners, Democrats, and Republicans.
2. Some groups of commissioners might collude together, trying to manipulate the outcome.

### Social-Choice Function

The usual model of a voting scheme is known as the [*social-choice function*](https://en.wikipedia.org/wiki/Social_choice_theory#Social_choice_functions) under the context of algorithmic game theory. The basic idea is to collect everyone's preferences profile and return a final result, and in our project, we want to design a social-choice function that collects commissioners' preferences for maps and returns one at the end.

### Fairness

As one might expect, defining *fairness* is not a trivial thing to do. In our example, we want to achieve at least the following.

#### Group Strategy Proof

The *group strategyproofness* is a generalized notion of [strategyproofness](https://en.wikipedia.org/wiki/Strategyproofness), where even if a group of voters colludes to misreport their preferences, there's no way they can improve their utility (i.e., achieving their goal such as selecting a map that is biased to a particular party). In other words, even if a group of people can collude, being truthful is the best strategy.

#### Unbiased

We want to always select an unbiased map such that no particular party benefits.  We refer to such an unbiased map as a *neutral map*. Notice that this is a desired property directly controlling the outcome of the voting rule to produce a *fair* outcome.

We see that by combining group strategyproofness and unbiased map property, there's no way to manipulate the mechanism.

## Positional-Scoring Rule

Now we describe our technical contribution.  Assuming that we have three maps, biased toward Democrats, Republicans, and neutral respectively. Then, by considering a simple [positional-scoring rule](https://en.wikipedia.org/wiki/Positional_voting) with score $\langle 1, 0, -1\rangle$ on commissioners' preference on these three types of maps, we prove the following.

### Main Theorem

**Theorem** *Supposes that the commission is composed of an equal number of Democrats and Republicans and at least one Independent commissioner, $w_D$, or $w_R$.[^2] Then, the positional-scoring voting rule with scores $\langle 1, 0, -1\rangle$, respectively, is group strategy-proof and chooses a neutral map.*

[^2]: We assume that even an independent commissioner has his/her preference as a *weak* Democrat/Republican. This is a fair assumption since the preference of an independent commissioner is expected to be either "*neutral map*$\succ$*Democrats map*$\succ$*Republicans map*" (i.e., weak *Democrats*, $w_D$) or "*neutral map*$\succ$*Republicans map*$\succ$*Democrats map*" (i.e., weak *Republicans*, $w_R$).

The equal number of Democrats and Republicans is referred to as the *balanced* case.[^3]

[^3]: It's possible to relax the result to the unbalanced case with some adjustments to the scoring. See the paper for details.
