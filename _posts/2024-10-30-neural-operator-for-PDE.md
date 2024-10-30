---
layout: post
title: neural operator for PDE
date: 2024-10-30
description: A novel data-driven method for solving PDE
tags: AI
categories: Algorithm
---

**Many problems in science and engineering involve solving complex partial differential equations (PDEs) repeatedly for different values of some parameters.**

## 1 Conventional PDE solvers
Take photoacoustic (PA) image reconstruction for example, one needs to solve the inverse problem w.r.t. the PA wave equation. Tradiitional analytical solvers are efficient but are based on the ideally linear and homogeneous wave equation. This approximated physical model caused degraded images. Traditional numerical solvers solve nonlinear and heterogeneous wave equations by an iterative process, which is more accurate and more time-consuming.

## 2 Data-driven methods
Data-driven methods can achieve accuracy similar to traditional numerical methods and be orders of magnitude faster. There are three kinds of neural network-based approaches for PDEs: finite-dimensional operators, neural-FEM, and neural operators.
**Finite-dimensional operators:** These approaches parameterize the PDE solution operator as a deep convolutional neural network with fixed-dimensional input and output. Such approaches are mesh-dependent and will need modifications and tuning for different resolutions and discretizations.
**Neural-FEM:** The second approach directly parameterizes the solution function as a neural network. This approach is designed to model one specific instance of the PDE, not the solution operator. It's mesh-independent, but for any new instance, it requires training a new neural network. This approach suffers from the same computational issue as classical methods: the optimization problem needs to be solved for every new instance. Furthermore, the approach is limited to a setting where the underlying PDE is known.
**Neural Operators:** Recently, a new line of work proposed learning mesh-free, infinite-dimensional operators with neural networks. It has the ability to transfer solutions between meshes. Furthermore, the neural operator needs to be trained only once. Obtaining a solution for a new instance of the parameter requires only a forward pass of the network, alleviating the major computational issues incurred in Neural-FEM methods. Lastly, the neural operator requires no knowledge of the underlying PDE, only data.

## References
Li, Zongyi, Nikola Kovachki, Kamyar Azizzadenesheli, Burigede Liu, Kaushik Bhattacharya, Andrew Stuart, and Anima Anandkumar. "Fourier neural operator for parametric partial differential equations." arXiv preprint arXiv:2010.08895 (2020).