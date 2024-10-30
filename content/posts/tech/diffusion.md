---
title: "Diffusion"
date: 2024-10-29T10:55:23+08:00
lastmod: 2024-10-29T10:55:23+08:00
author: ["Zijian Liang"]
keywords: 
- Generative
categories: 
- Generative
tags: 
- Generative
- tech
description: "Swiss army knife of Diffusion"
weight:
slug: ""
draft: false # 是否为草稿
comments: true
reward: false # 打赏
mermaid: false # 是否开启mermaid
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
showbreadcrumbs: true # 顶部显示路径
math: true
cover:
    image: "posts/tech/image/diffusion.gif" # 图片路径：posts/tech/123/123.png
    caption: "" # 图片底部描述
    alt: ""
    relative: false
---

# Score-based generative modeling with stochastic differential equations (SDEs)

As we already discussed, adding multiple noise scales is critical to the success of score-based generative models. By generalizing the number of noise scales to infinity 
[21]
, we obtain not only higher quality samples, but also, among others, exact log-likelihood computation, and controllable generation for inverse problem solving.

In addition to this introduction, we have tutorials written in Google Colab to provide a step-by-step guide for training a toy model on MNIST. We also have more advanced code repositories that provide full-fledged implementations for large scale applications.

How can we represent a stochastic process in a concise way? Many stochastic processes (diffusion processes in particular) are solutions of stochastic differential equations (SDEs). In general, an SDE possesses the following form:

$$
d\mathbf{x} = \mathbf{f}(\mathbf{x}, t) dt + g(t) d\mathbf{w},
$$