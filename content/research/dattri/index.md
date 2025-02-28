---
title: "dattri: A Library for Efficient Data Attribution"
tags: ["Data Attribution", "Library"]
date: 2024-09-26 00:00:00 -0500
priority: -20240926
path: "research/dattri"
excerpt: "We developed a efficient library for data attribution, aiming to streamline the development of data attribution algorithms."
selected: false
cover: "./preview.png"
venue: "NeurIPS 2024 D&B (Spotlight)"
links:
- name: "arXiv"
  url: "https://arxiv.org/abs/2410.04555"
- name: "Poster"
  url: "./research/dattri/poster.pdf"
- name: "GitHub"
  url: "https://github.com/TRAIS-Lab/dattri"
authors:
- name: "Junwei Deng*"
  url: "https://theaperdeng.github.io/"
- name: "Ting-Wei Li*"
  url: "https://tingwl0122.github.io/"
- name: "Shiyuan Zhang"
  url: "https://seanzh30.github.io/"
- name: "Yijun Pan"
- name: "Hao Huang"
- name: "Xinhe Wang"
- name: "**Pingbang Hu**"
  url: "https://pbb.wtf/"
- name: "Xingjian Zhang"
  url: "https://sites.google.com/umich.edu/xingjian-zhang/"
- name: Jiaqi Ma
  url: "https://jiaqima.github.io/"
---

> [arXiv](https://arxiv.org/abs/2410.04555) | [GitHub](https://github.com/TRAIS-Lab/dattri)

## Brief Summary

Data attribution methods aim to quantify the influence of individual training samples on the prediction of artificial intelligence (AI) models. As training data plays an increasingly crucial role in the modern development of large-scale AI models, data attribution has found broad applications in improving AI performance and safety. However, despite a surge of new data attribution methods being developed recently, there lacks a comprehensive library that facilitates the development, benchmarking, and deployment of different data attribution methods. In this work, we introduce $\texttt{dattri}$, an open-source data attribution library that addresses the above needs. Specifically, $\texttt{dattri}$ highlights three novel design features. Firstly, $\texttt{dattri}$ proposes a unified and easy-to-use API, allowing users to integrate different data attribution methods into their PyTorch-based machine learning pipeline with a few lines of code changed. Secondly, $\texttt{dattri}$ modularizes low-level utility functions that are commonly used in data attribution methods, such as Hessian-vector product, inverse-Hessian-vector product or random projection, making it easier for researchers to develop new data attribution methods. Thirdly, $\texttt{dattri}$ provides a comprehensive benchmark framework with pre-trained models and ground truth annotations for a variety of benchmark settings, including generative AI settings. We have implemented a variety of state-of-the-art efficient data attribution methods that can be applied to large-scale neural network models, and will continuously update the library in the future. Using the developed $\texttt{dattri}$ library, we are able to perform a comprehensive and fair benchmark analysis across a wide range of data attribution methods.

> This paper also appears in the ATTRIB 2024 workshop @NeurIPS.

## Citation

```bibtex
@inproceedings{deng2024dattri,
  author    = {Deng, Junwei and Li, Ting-Wei and Zhang, Shiyuan and Liu, Shixuan and Pan, Yijun and Huang, Hao and Wang, Xinhe and Hu, Pingbang and Zhang, Xingjian and Ma, Jiaqi},
  booktitle = {Advances in Neural Information Processing Systems},
  editor    = {A. Globerson and L. Mackey and D. Belgrave and A. Fan and U. Paquet and J. Tomczak and C. Zhang},
  pages     = {136763--136781},
  publisher = {Curran Associates, Inc.},
  title     = {\texttt{dattri}: A Library for Efficient Data Attribution},
  url       = {https://proceedings.neurips.cc/paper_files/paper/2024/file/f732683302d91e47610b2416b4977a66-Paper-Datasets_and_Benchmarks_Track.pdf},
  volume    = {37},
  year      = {2024}
}
```
