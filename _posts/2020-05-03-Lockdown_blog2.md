---
title: Day 2, Assignments, Beef and Kaggle
type: post
---

**ബീഫ്** is like one of best food items's which everyone in my family buys, and after 2 weeks of Easter, we finally
bought it. The curry and Kappa biryani which my Amma cooked was so awesome and it made my day.


### What's domain shift?

*domain shift*; this is where the type of data that our model sees changes over time. For instance, an insurance company may use a deep learning model as part of their pricing and risk algorithm, but over time the type of customers that they attract, and the type of risks that they represent, may change so much that the original training data is no longer relevant.

Out of domain data, and domain shift, are examples of the problem that you can never fully know the entire behaviour of your neural network. They have far too many parameters to be able to analytically understand all of their possible behaviours. This is the natural downside of the thing that they're so good at — their flexibility in being able to solve complex problems where we may not even be able to fully specify our preferred solution approaches. The good news, however, is that there are ways to mitigate these risks using a carefully thought out process. The details of this will vary depending on the details of the problem you are solving, but we will attempt to lay out here a high-level approach summarized in <<deploy_process>> which we hope will provide useful guidance.

### Assignments (Data Mining)

Answer the following questions:
1. Briefly outline how to compute the dissimilarity between objects described by the
following types of variables:
(a) Numerical (interval-scaled) variables
(b) Asymmetric binary variables
(c) Categorical variables
(d) Ratio-scaled variables
(e) Nonmetric vector objects

2. Given two objects represented by the tuples (22, 1, 42, 10) and (20, 0, 36, 8):
(a) Compute the Euclidean distance between the two objects.
(b) Compute the Manhattan distance between the two objects.
(c) Compute the Minkowski distance between the two objects, using q = 3.

**Answer**

a) For interval-scaled variables like weight, height etc first standardise the variable. It can be done by calculating
the mean and doing a standardised measurement like Z-score.

After standardization, the dissimilarity (or similarity) between
the objects described by interval-scaled variables is typically
computed based on the distance between each pair of
objects. The most popular distances are:

- Eulers distance
- Manhattan distance
- Minkowski distance

b) For asymmetric binary variables, the disimilarity and similarity can be calculated with jaccard coefficent such:

similarity(jaccard(i,j)) = q/(q+r+s)
disimilarity(jaccard(i,j) = p/(q+r+s)

B. Dissimilarity in Ordinal Variable
This kind of variable has multiple values but in
predefined order. As it is in order difference between two
simultaneous variables is always same. The difference
between two ordinal variables is always multiplication of
difference between two simultaneous variable and difference
in their order.
Let c1 and c2 be two ordinal categorical tuples. d(s) be
the difference between two simultaneous tuples and d(o) be
the difference between order of c1 and c2. The distance d(c1;
c2) is as shown in equation
d (c1, c2) = d(s) * d(o)
C. Dissimilarity in Nominal Variable
This kind of variable has multiple categories also not in
order. So there is difficulty in calculating difference between
nominal variables. In this case we use dependant variables on
categorical attribute. Dependant attribute directly represent
value of categorical data.
Let c1 and c2 be two nominal categorical tuples. tdep1 and
tdep2 be the corresponding dependant variables. The distance
d(c1, c2) is as shown in equation
d (c1, c2) = (tdep1 - tdep2)

A. Dissimilarity in Dichotomous Variable
Dichotomous variables are designed to give an either/or
response. As it has only two values, variables either different
or same. So they add same amount of dissimilarity percentage
in cluster formulation. Let c1 and c2 be two dichotomous
categorical tuples. Then distance d (c1, c2) is as shown in
following equation
d (c1, c2) = 0/1

Question2

Given A=(22,1,42,10) & B = (20,0,36,8)

Euclidiean distances = (22-20)**2 + (1-0)**2 + (42-36)**2 + (2)**2
                     = 4+4+1+ 36
                     = sqrt(45)

Manhattan distance = [22-20]+[1]+[6]+[2]
                   = 11

Minkowski distance = cuberoot(2**3+ 1**3 + 6**3 + 2**3)
                    = 6.15344


Next, yesterday Shahul and I talked about fakers in Kaggle. There are now a lot of fakers and 2 month grandmasters in
Kaggle, and most of them are from our country only(India). It makes sometimes you a bit angry, because when I write a
notebook, it's very few times I get a upvote. While fakers go on DMing in LinkedIn for upvotes, and do other practises
as well. Shahul made a excellent point noting that there are fakers in all the platform, but if we stay honest we will
be rewarded with knowledge.

So till next time `:wq`
