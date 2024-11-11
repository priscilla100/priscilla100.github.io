---
title: "Adversarial Attack on Data Attribution"
tags: ["Trustworthy", "Data Attribution"]
date: 2024-09-09 00:00:00 -0500
priority: -20240909
path: "research/Adversarial-Attack-on-Data-Attribution"
excerpt: "We consider the *adversarial attack* on training data attribution methods."
selected: true
cover: "./preview.png"
venue: "ATTRIB Workshop @NeurIPS 2024"
links:
- name: "arXiv"
  url: "https://arxiv.org/abs/2409.05657"
authors:
- name: "Xinhe Wang"
- name: "***Pingbang Hu***"
  url: "https://pbb.wtf/"
- name: "Junwei Deng"
  url: "https://theaperdeng.github.io/"
- name: Jiaqi Ma
  url: "https://jiaqima.github.io/"
---

> [arXiv](https://arxiv.org/abs/2409.05657)

## Brief Summary

Data attribution aims to quantify the contribution of individual training data points to the outputs of an AI model, which has been used to measure the value of training data and compensate data providers. Given the impact on financial decisions and compensation mechanisms, a critical question arises concerning the adversarial robustness of data attribution methods. However, there has been little to no systematic research addressing this issue. In this work, we aim to bridge this gap by detailing a threat model with clear assumptions about the adversary's goal and capabilities, and by proposing principled adversarial attack methods on data attribution. We present two such methods, *Shadow Attack8 and *Outlier Attack*, both of which generate manipulated datasets to adversarially inflate the compensation. The Shadow Attack leverages knowledge about the data distribution in the AI applications, and derives adversarial perturbations through *shadow training*, a technique commonly used in membership inference attacks. In contrast, the Outlier Attack does not assume any knowledge about the data distribution and relies solely on black-box queries to the target model's predictions. It exploits an inductive bias present in many data attribution methods --- outlier data points are more likely to be influential --- and employs adversarial examples to generate manipulated datasets. Empirically, in image classification and text generation tasks, the Shadow Attack can inflate the data-attribution-based compensation by at least 200%, while the Outlier Attack achieves compensation inflation ranging from 185% to as much as 643%.

## Citation

```bibtex
@article{wang2024adversarial,
  title   = {Adversarial Attacks on Data Attribution},
  author  = {Wang, Xinhe and Hu, Pingbang and Deng, Junwei and Ma, Jiaqi W},
  journal = {arXiv preprint arXiv:2409.05657},
  year    = {2024}
}
```
