---
layout: post
title:  "DEEP GRADIENT COMPRESSION"
date:   2018-04-25 11:00:00 +0900
tag: [Deep Learning]
---

## [DEEP GRADIENT COMPRESSION: REDUCING THE COMMUNICATION BANDWIDTH FOR DISTRIBUTED TRAINING](https://arxiv.org/pdf/1712.01887.pdf) 을 분석하고 구현하기 위해 작성함.


# 1 INTRODUCTION

Large-scale distributed training improves the productivity of training deeper and larger models (Chilimbi et al., 2014; Xing et al., 2015; Moritz et al., 2015; Zinkevich et al., 2010).

Synchronous stochastic gradient descent (SGD) is widely used for distributed training.

By increasing the number of training nodes and taking advantage of data parallelism, the total computation time of the forward-backward passes on the same size training data can be dramatically reduced.

However, gradient exchange is costly and dwarfs the savings of computation time (Li et al., 2014; Wen et al., 2017), especially for recurrent neural networks (RNN) where the computation-to-communication ratio is low.

Therefore, the network bandwidth becomes a significant bottleneck for scaling up **distributed training**.

This bandwidth problem gets even worse when distributed training is performed on mobile devices, such as federated learning (McMahan et al., 2016; Koneckkuuuˇny` et al., 2016).

Training on mobile devices is appealing due to better privacy and better personalization (Google, 2017), but a critical problem is that those mobile devices suffer from even lower network bandwidth, intermittent network connections, and expensive mobile data plan.

Deep Gradient Compression (DGC) solves the communication bandwidth problem by compressing the gradients, as shown in **Figure 1**. 

To ensure no loss of accuracy, DGC employs **momentum correction** and **local gradient clipping** on **top of the gradient sparsification** to maintain model performance.

DGC also uses **momentum factor** masking and **warmup training** to overcome the staleness problem caused by reduced communication.


We empirically verified Deep Gradient Compression on a wide range of tasks, models, and datasets: CNN for image classification **(with Cifar10 and ImageNet)**, RNN for language modeling (with Penn Treebank) and speech recognition (with Librispeech Corpus). 

These experiments demonstrate that gradients can be compressed up to 600× without loss of accuracy, which is an order of magnitude higher than previous work (Aji & Heafield, 2017).

