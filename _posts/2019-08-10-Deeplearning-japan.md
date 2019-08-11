---
title: Deep Learning for Japanese Classical Literature
layout : post
comments: true
---

Japan is a country which has been one of my place. Konnichiwa is only word I know in Japanese which means a greeting
like How are you. This article is a short summary of the [research paper](https://arxiv.org/abs/1812.01718) authored by
Tarin Clanuwat, Mikel Bober-Irizar, Asanobu Kitamoto, Alex Lamb, Kazuaki Yamamoto, David Ha. 

The main idea of this paper is to release Kuzhushiji(Cursive Japanese Language) dataset to get perspective ML researchers to 
use technology to understand the language as now most Japanese natives can't understand this language and read books
written or published over 150 years. In General Catalog of National Books, there is over 1.7 million books and about 3
millions unregistered books yet to be found. It's estimated that there are around a billion historical documents written
in Kuzhushiji language over a span of centuries.

### Kuzhushiji Dataset

The Japanese language can be divided into two types of systems:

- Logographic systems, where each character represents a word or a phrase (with thousands of characters). A prominent logographic system is Kanji, which is based on the Chinese System.

- Syllabary symbol systems, where words are constructed from syllables (similar to an alphabet). A prominent syllabary system is Hiragana with 49 characters (Kuzushiji-49), which prior to the Kuzushiji standardization had several representations for each Hiranaga character.

The Kuzushiji dataset includes characters in both Kanji and Hiranaga, based on pre-processed images of characters from 35 books from the 18th century. It includes 3 parts:

a) Kuzhushiji MNIST:

A replacement for MNIST, yet there are fewer than 49 letters needed to fully Kuzhushiji Hirangana.
We have about 10 rows to represent MNIST dataset which in typical case is from 0-9 in Handwriting dataset. Currently we
choose 10 rows of Hirangana when creating dataset

b) Kuzhushiji 49: 

A larger much imbalanced dataset containing 49 hirangana characters with about 150,000 images for dataset.

c) Kuzhushiji Kanji: 

A total of 3832 classes of characters are in this dataset with about 140, 426 images. This dataset is not created merely
for classification images, instead for more creative experimental task.

### Experiments

**Classification Baselines**

- gives 98% and 97.33% accuracy for dataset on using PreActResnet18 + manifold mixup
- sketch RNN

**Algorithm**
1. Train two seperate variational autoencoder on pixel version of KanjiVG and Kuzhushiji-Kanji
2. Train mixture density network to mode P(Znew | Zold) as mixture of gaussians.
3. Train sketch RNN to generate Kanji VGG strokes conditioned on either znew or z~new ~P(Znew|Zold)
