---
title: Notes in Top Grandmasters' Kaggle Journeys and Validation
type: post
tags: ['notes', 'talks']
---

- stacking check how to use best method from kaggle blog
- How to do target encoding without ovefitting? (categorical variables - high cardinallity)

leaking targets between various folds, best way => use k folds first, then for each fold
do target encoding in each fold seperately. Train model. Split model then train
test the right way


- build validation in large datasets, much resource?

ensemble dataset, then cross validate. Don't tune on image dataset

do sampling, sample with same resolution in test dataset. Exact distribution of test cannot be found in recent kaggle
comp. One important part is get comfortable with data.

- How to understand and work in problems w/ domain knowledge?

read papers, experiment and do crazy things(and most do not worked and tried lot of new ideas)
Kaggle is all about experimentations. It's harder to get better in ML than in domain name(papa).

- Why linear models outperform gradient boosting?
(just linear regression helped in prediction), small data small models
depends on size of model usually. Predicting confidence intrevals in week 5 of Covid19 model, then
in M5 competition

- Have you created custom objective for your problem metric?

(in giba at airbus)

## Closing notes

Lot of times can be solved by trying both the things usually, that's the best. Human
intuition is always best. If you are a good datascientist, do a lot of experiments.
If you have question which is best algo, try both and choose the best.
