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
comments: true # 本页面是否显示评论
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

并行训练的功能可以分成三个组件：

1. 分布式数据并行训练（DDP）是一种广泛采用的单程序多数据训练范式。在 DDP 中，**模型会在每个进程上复制，每个模型副本将接收不同的输入数据样本**。DDP 负责梯度通信以保持模型副本同步，并将其与梯度计算重叠以加速训练。
2. 基于 RPC 的分布式训练（RPC）支持无法适应数据并行训练的通用训练结构，例如分布式流水线并行、参数服务器范式以及 DDP 与其他训练范式的组合。它有助于管理远程对象的生命周期，并将自动微分引擎扩展到单个计算节点之外。
3. 提供了在组内进程之间发送张量的功能，包括集体通信 API（如 All Reduce 和 All Gather）和点对点通信 API（如 send 和 receive）。尽管 DDP 和 RPC 已经满足了大多数分布式训练需求，PyTorch 的中间表达 C10d 仍然在需要更细粒度通信控制的场景中发挥作用。例如，分布式参数平均，在这种情况下，应用程序希望在反向传播之后计算所有模型参数的平均值，而不是使用 DDP 来通信梯度。这可以将通信与计算解耦，并允许对通信内容进行更细粒度的控制，但同时也放弃了 DDP 提供的性能优化。



# Data Parallism (DP)

通过将**数据集划分为多个子集**并在不同计算节点上并行处理这些子集，以提高计算效率和速度。

每个计算节点都会接收到**完整的模型副本**。

![数据并行](02DataParallel01.jpg)


# Model Parallism (MP)



# Hybrid Parallism


# 参考资料
1. https://ilyee.github.io/2024/03/06/distributed-training/
2. https://chenzomi12.github.io/




