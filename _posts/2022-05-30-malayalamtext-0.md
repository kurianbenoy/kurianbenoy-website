---
title: Starting an open source project - Malayalam Text Classifier
type: post
tags: [malayalamtextmodels, malayalam, NLP , opensource, ML, Deep learning]
readtime: true
published: true
---

> TLDR: Kurian has commited to start an open source project for Text classification task in Malayalam which is going to be build as open source under [SMC community](https://smc.org.in/). 

## Why I am starting this project?

I have been doing fastai course from 2018. Yet I have been taking it seriously probably, only after I bought the book [Deep Learning for Coders with FastAI & Pytorch](https://kurianbenoy.com/2021-06-10-Fast-group/) almost one year back. This year I had took the [fastai v5 course](https://itee.uq.edu.au/event/2022/practical-deep-learning-coders-uq-fastai), and I feel it's time to follow an advice which I have heard multiple times.

> Important: Jeremy Howard, who is teaching this course and wrote the book prompts you to take what you learned and apply it to something that has meaning for you. (This is something that most of those who’ve found any success with the course [emphasise repeatedly](https://sanyambhutani.com/how-not-to-do-fast-ai--or-any-ml-mooc-/).)

## Problem Domain

According to [huggingface tasks page](https://huggingface.co/tasks/text-classification):

> Text Classification is the task of assigning a label or class to a given text. Some use cases are sentiment analysis, natural language inference, and assessing grammatical correctness.

Malayalam is a highly inflectional and agglutinative language compared to other languages. The quantitative complexity of Malayalam classification was [explained in this paper](https://kavyamanohar.com/documents/tsd_morph_complexity_ml.pdf). Computer still doesn't seem to have understood basic behaviour of the language to do text classification and Malayalam being a language which morphologically complex makes it even more difficult.

Very few people seems to have applied techniques in deep learning in Malayalam, and it seems to be a good place to see if really deep learning techniques can be applied in my mother tongue, Malayalam. Lot of progress in other languages have happend and in general NLP, yet it's a good time to see if it really works in Indic languages like Malayalam.


## Why Text classification is interesting?

I beleive working on task like `Text classification` is way more difficult when we are working in low-resource languages like Malayalam. Yet when working in problems like this, you realize what are things you take granted in English language.

In English language, there are plenty of labelled datasets on any problem set you want. Lot of articles and blogs have written on how to apply various NLP techniques in English. When it comes to Malayalam, there are just handful of people who have tried and applied this in Malayalam.

> Note to myself: Will is more important than Skill and it's important to tenatious here.

I believe this is here, it's very important to believe in one's tenacity and try out new things in a field where very less research happening, and there is no proper open datasets for researchers to work. This is why I feel this project can be challenging, and my approach is to see if the latest transformer approaches can do something or not.

## Previous  work: Vaaku2Vec

The most important work in Malayalam text classification as far as I know is [Vaaku2Vec project - State-of-the-Art Language Modeling and Text Classification in Malayalam Language](https://github.com/adamshamsudeen/Vaaku2Vec).

According to their github README:

> We trained a Malayalam language model on the Wikipedia article dump from Oct, 2018. The Wikipedia dump had 55k+ articles. The difficuly in training a Malayalam language model is text tokenization, since Malayalam is a highly inflectional and agglutinative language. In the current model, we are using nltk tokenizer (will try better alternative in the future) and the vocab size is 30k. The language model was used to train a classifier which classifies a news into 5 categories (India, Kerala, Sports, Business, Entertainment). Our classifier came out with a whooping 92% accuracy in the classification task.

It was revolutionary at that time, to see deep learning techniques applied to get SOTA in Malayalam. IndicNLP as an organisation did a lot of work, from working on projects like Word2vec, Vaakk2vec etc. They worked on creating a Named entity recognition dataset for Malayalam etc. They conducted Devsprints in colleges like Model Engineering colleges, and presented their work in Pycon India and Kochi Python. Most of work was done by [Adam Shamsudeen](https://www.linkedin.com/in/adamshamsudeen/) and [Kamal K Raj](https://www.linkedin.com/in/kamalkraj/).

<iframe width="560" height="315" src="https://www.youtube.com/embed/rgCXWaKzMKU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## What's the plan for project?

> Important: Cervantes once wrote that "the journey is better than the inn", which means meaning that the process is more valuable than the destination.

At moment, the project doesn't have any concrete goals and it's just me who is working in my free time.

I have created a [few issues](https://github.com/smc/malayalam-text-classifier/issues) and my next blogpost will be on creating a baseline model on a private dataset which a few kind folks shared with me. I expect the dataset creation to be a iterative task, and looking forward to blog what I work and stumple upon in each stage of project.

When I was looking for where I want to create this open source project, I choose [Swathanthra Malayalam Community](https://smc.org.in/) because:


- I feel SMC as an organization played a pivotal part in revolutionizing Malayalam computing and has strong community presence. They have made lot of work by creating fonts, helping in internationalization efforts, ...
- People like [Santhosh Thottingal](https://thottingal.in/) and [Kavya Manohar](https://kavyamanohar.com/) has helped me a lot in my previous failed attempt to [build TTS with  deep learning in Malayalam](https://github.com/kurianbenoy/MTTS).
- Some of the open source projects made by SMC still survives like website of [Malayalam Speech Corpus](https://msc.smc.org.in/) which is impressive to me.

I would like to thank the following people for all the support and motivation they have given me in starting this open source project in this occasion:

1. [Alex Strick van Linschoten](https://twitter.com/strickvl/)
2. [Santhosh Thottingal](https://twitter.com/santhoshtr) and  [Kavya Manohar](https://twitter.com/kavya_manohar)
3. [Ashwin Jayaprakash](https://twitter.com/fanbyprinciple)
