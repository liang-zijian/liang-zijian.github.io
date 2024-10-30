---
title: "Intelligence_Parallelism (ToBeContinued)"
date: 2024-10-30T17:01:24+08:00
lastmod: 2024-10-30T17:01:24+08:00
author: ["Zijian Liang"]
keywords: 
- AISystem
categories: # 没有分类界面可以不填写
- 
tags: # 标签
- AISystem
description: ""
weight:
slug: ""
draft: false # 是否为草稿
comments: false # 本页面是否显示评论
reward: false # 打赏
mermaid: true #是否开启mermaid
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
showbreadcrumbs: true #顶部显示路径
cover:
    image: "posts/tech/img/distributed.jpg" #图片路径例如：posts/tech/123/123.png
    zoom: # 图片大小，例如填写 50% 表示原图像的一半大小
    caption: "" #图片底部描述
    alt: ""
    relative: false
---


# Introduction


Parallel Training Functionality can be divided into three components:
1. Distributed Data Parallel (DDP) is a widely adopted single-process multi-data training paradigm. **In DDP, the model is replicated on each process, with each model replica receiving different input data samples**. DDP relies on gradient communication to keep model replicas in sync and combines this with gradient computation to accelerate training.
2. RPC-based Distributed Training (RPC) supports general training structures that cannot adapt to data parallel training, such as distributed pipeline parallelism, parameter server paradigm, and combinations of DDP with other training paradigms. It helps manage the lifecycle of remote objects and automatically extends fine-grained control beyond a single compute node.
3. Provides functionality for tensor communication between processes within a group, including collective communication APIs (such as All Reduce and All Gather) and point-to-point communication APIs (such as send and receive). Although DDP and RPC have satisfied most distributed training requirements, PyTorch's intermediate representation C10d still plays a role in scenarios requiring finer-grained communication control. For example, in distributed parameter averaging, applications wish to compute the average of all model parameters after backward propagation, rather than using DDP for gradient communication. This decouples communication from computation and allows finer-grained control over communication content, though it sacrifices the performance optimizations provided by DDP.


# Data Parallism (DP)
By dividing the **dataset into multiple subsets** and processing these subsets in parallel on different compute nodes to improve computational efficiency and speed.

Each compute **node receives a complete copy of the model**.


![DP](02DataParallel01.jpg)


# Model Parallism (MP)



# Hybrid Parallism


# Reference
1. https://ilyee.github.io/2024/03/06/distributed-training/
2. https://chenzomi12.github.io/


<script src="https://giscus.app/client.js"
        data-repo="liang-zijian/liang-zijian.github.io"
        data-repo-id="R_kgDONHay6w"
        data-category="Announcements"
        data-category-id="DIC_kwDONHay684Cjycs"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="light"
        data-lang="zh-CN"
        crossorigin="anonymous"
        async>
</script>
