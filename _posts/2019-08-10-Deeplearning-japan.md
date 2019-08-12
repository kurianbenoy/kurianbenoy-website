---
title: Deep Learning for Japanese Classical Literature
author: Kurian Benoy
layout : post
comments: true
---

Japan is a country which has been very unique. Konnichiwa is only word I know in Japanese which means a greeting
like How are you. This blogpost is a short summary of the [research paper](https://arxiv.org/abs/1812.01718) authored by
Tarin Clanuwat, Mikel Bober-Irizar, Asanobu Kitamoto, Alex Lamb, Kazuaki Yamamoto, David Ha. 

This research paper was presented in NIPS 2018 and is written by a team from Center for Open Data in Humanities(CODH)
National Institute of Japanese Literature(NIJL) 18 year old Kaggle Grandmaster Mikel Bober and David from Google brain.

## Abstract

- To encourage ML researchers to produce models for Social or Cultural relevance to transcribe Kuzushiji into contemporary Japanese characters.
- To release Kuzushiji MNIST dataset, Kuzushiji 49 and Kuzushiji-Kanji datasets to general public.

## Introduction

Historically, Japan and it's culture had been isolated from the west for a long period of time. Untill the Meiji
restoration in 1868, when a 15 year old emperor brought unity to whole of Japan which was earlier broken down into
regional small rulers. This caused a massive change in Japanese Language, writing and printing system. Even though
Kuzushiji had been used for over 1000 years there are very few fluent readers of Kuzushiji today (only 0.01% of modern Japanese natives).
So now most Japan natives cannot read books written and published over 150 years ago. In General Catalog of National
Books, there is over 1.7 million books and about 3 millions unregistered books yet to be found. It's estimated
that there are around a billion historical documents written in Kuzhushiji language over a span of centuries. Most of
this knowledge is now inaccessible to general public.

With this research paper, three easy to use pre-processed datasets has been released for Machine learning research to 
help in Recognising Kuzhushiji, domain transfer of contents from unseen Kuzhushiji Kanji to Modern Kanji(classical
Japanese literature). Also the baseline classification results for the same has been mentioned in this paper.

### Kuzhushiji Dataset

{% include image.html url="/imag/oldbook.png" description="Example of Kuzhishiji literature scroll, Genimonogatari Uta
Awase" %}

The Japanese language can be divided into two types of systems:

- Logographic systems, where each character represents a word or a phrase (with thousands of characters). A prominent logographic system is Kanji, which is based on the Chinese System.

- Syllabary symbol systems, where words are constructed from syllables (similar to an alphabet). A prominent syllabary system is Hiragana with 49 characters (Kuzushiji-49), which prior to the Kuzushiji standardization had several representations for each Hiranaga character.

The Kuzhushiji dataset is created by National Institute of Japanese Literature(NIJL) and is curated by Center for Open
Data in Humanities(CODH). This dataset includes characters in both Kanji and Hiranaga, based on pre-processed images of
characters from 35 books from the 18th century. It includes 3 parts:

a) Kuzhushiji MNIST:

{% include image.html url="/img/MNIST.png" description="Kuzhushiji MNIST" %}

[MNIST for handwritten digits](http://yann.lecun.com/exdb/mnist/) is one of the most popular dataset's till and is usually the hello world for Deep
Learning. As a easy to process beginner dataset, this is consist of 10 classes with 7000 images for each. Yet there are
fewer than 49 letters needed to fully represent Kuzhushiji Hirangana.
So currently we choose 10 rows of Hirangana when creating dataset with 5 letter being stacked together to form this
dataset. Each image is `28*28` pixel resolution. Kuzhushiji MNIST is more difficult compared to MNIST because for each
image the chance for a human to detect characters correctly when a single image is of small size and is stacked together of 5 rows is
very less. Also there are more challenges in  [Kuzhushiji recognition](https://www.kaggle.com/c/kuzushiji-recognition/overview/about-kuzushiji).

b) Kuzhushiji 49: 

{% include image.html url="/img/K49.png" description="Kuzhushiji 49 dataset" %}

As the name suggest, it is a much larger imbalanced dataset containing 49 hirangana characters with about 266,407
images. Both Kuzhushiji-49 and Kuzhushiji-MNIST consists of `grey images of 28*28 pixel resolution`. The training and
test is split in ratio of 6/7 to 1/7 for each classes. There are several rare characters with small no of samples such
as (e) in hirangana has only 456 images.

c) Kuzhushiji Kanji: 

{% include image.html url="/img/KK.png" description="Kuzhushiji Kanji dataset" %}

Kuzhushiji Kanji has a total of 3832 classes of characters  in this dataset with about 140,426 images. Kuzhushiji-Kanji
images are are of larger 64x64 pixel resolution and the number of samples per class range from over a thousand to only
one sample. This dataset is not created merely for classification images, i11nstead for more creative experimental task.

If you are interested in downloading the dataset with detailed documentation.

[Go here](https://github.com/rois-codh/kmnist)

### Experiments

**Classification Baselines**

- gives 98% and 97.33% accuracy for dataset on using PreActResnet18 + manifold mixup
- sketch RNN

**Algorithm**
1. Train two seperate variational autoencoder on pixel version of KanjiVG and Kuzhushiji-Kanji
2. Train mixture density network to mode P(Znew | Zold) as mixture of gaussians.
3. Train sketch RNN to generate Kanji VGG strokes conditioned on either znew or z~new ~P(Znew|Zold)
