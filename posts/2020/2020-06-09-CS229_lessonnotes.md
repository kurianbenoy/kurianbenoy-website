---
aliases:
- /myself/2020/06/09/CS229_lessonnotes
categories:
- myself
date: '2020-06-09'
layout: post
title: CS229 - Lesson Notes

---

> This is just a post for myself to write notes while watching videos, so it may contain lot
of typos and some mistakes. 

Pre-requisities:

- Understanding basic programming
- probability basics: random variable, 
- basic linear algebra: matrix, product, eigen vector

Aim: To do an awesome project by the end of project and gain basics useful forever.

I am already familar with basics of programming, in case of probability, I know about bayes theoreum, yet there are more
topics which I don't, so cheatsheets for now. I am not familar with linear algebra much now, yet I remeber taking Rachel
lectures to learn about SVD, NMF etc.

In the less Andrew covered following topics:
- Difference b/w CS229, CS230, CS229A?
- Classification
- Regression
- History(Arthur Samuel, chess program)
- Deep learning(automated car moving)

eg: given age, tumour size - 2 feature input, predict if tumour is malignant(classif)
                                                                         

## Lesson2

Andrew started off by theoratically representing, linear regression. He explained about gradient descent, and talked
about the ambiguity of big enough data now(~1-10 million datapoints now). In case of a batch gradient descent, we use
entire training data fully, even for 1 parameter update. 

Some mathematical properites:

∇A means derivate of a
trace AB = trace BA
tr ABC = tr CAB
`cost = 0.5*np.sum(A[i] - y[i])**2`


Proofs are clearly explained in the lecture notes. In end, he showed derivation of Newton equation which reaches the
optimal convergence point in a single update(only for linear reg). The contour and loss curver visualisation to show
effect of learning was awesome.

## Lesson3

Andrew talks about locally weighted regression method where, each points is fitted in a straight depending on it's curve
and dependance. It used for low-dim data with less features and is an example of non-parametric learing algorithm.

Topics like:
- Likelihood
- why least square formula?
- maximum likelehod 

## Read: Why understanding backprop is necessary?

## Lesson7 (Kernels in SVM)

- use optimisation problem

Representation theoreum proof, ie 

||wb||^2-> denoting kernels with objective function

can't understand: dual optimization, convex optimization, etc

ie Kernel trick:
Kernel function(x,z) = Phi(x)Transpose* Phi(z)

ie K(z,z) = (x T z)^2
