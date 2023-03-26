---
aliases:
- /2022/11/07/clipcorn
categories:
- coding
- Deep learning
- experience
- kaggle
date: '2022-11-07'
layout: post
title: How well does CLIP models classify corn seeds?
image: /posts/images/clip.png
---

The OpenAI CLIP model are really impressive and how it's a foundation for stuff like stable diffusion is awesome. The thing about
 CLIP models which I am most impressed by is the wide range of applications it be used for like
[Semantic Video Search](https://huggingface.co/spaces/YiYiXu/it-happened-one-frame-2), [Zero shot image classification](https://github.com/openai/CLIP#zero-shot-prediction), [searching images in your gallery](https://wandb.ai/pcuenq/photo-finder/reports/Creating-a-Semantic-Search-Engine-for-My-Photos--VmlldzoyMDE2NzQ3) etc.

I recently [started reading CLIP paper](https://arxiv.org/abs/2103.00020) and paper claims to have very high accuracy in
image clssification accuracy. To test that claim, I thought of trying it out that in a kaggle competition I had recently participated.

The kaggle competition is a Corn image classification competition and is asking to classify images of corn seeds into following
categories:

- pure
- broken
- discolored
- silkcut

I used `open_clip`, an open source implementation of CLIP which is having higher accuracy compared to model weights released by OpenAI.

Even after using one of the best accuracy CLIP models available( ViT-H-14), it got me a classification accuracy score of 27.95% in private LB  whereas Resnet or Convnext models could have given easily above 75% score.

| Model | Public LB | Private LB | Notebook link|
| --- | --- | --- | --- |
| ViT-B-32-quickgelu | 0.16666 | 0.18397 | [link](https://www.kaggle.com/code/kurianbenoy/playing-with-clip-model?scriptVersionId=108925854) |
| ViT-H-14 | 0.28591 | 0.27955 | [link](https://www.kaggle.com/code/kurianbenoy/playing-with-clip-model?scriptVersionId=109012620) |
| Convnext model| 0.76149 | 0.75386 | [link](https://www.kaggle.com/code/kurianbenoy/fastai-baseline-albumentations?scriptVersionId=106051045) |

**UPDATE**

When I shared this results in twitter, [YiYi Xu](https://twitter.com/YiYiMarz) suggested to try out [linear probing in CLIP](https://github.com/openai/CLIP#linear-probe-evaluation). She mentioned that, I was not comparing apples to apples, as I was using a zero-shot model with CLIP to compared with a fine tuned model of convnext. In order to level up, I should use linear probing which is using training data to kind of fine tune with a logistic regression model leveraging features in CLIP model.

Based on this, I leveraged using linear probing on the dataset. As a result my updated result are the following:

| Model | Public LB | Private LB | Notebook link|
| --- | --- | --- | --- |
| Zero Shot ViT-B-32-quickgelu | 0.16666 | 0.18397 | [link](https://www.kaggle.com/code/kurianbenoy/playing-with-clip-model?scriptVersionId=108925854) |
| Zero Shot ViT-H-14 | 0.28591 | 0.27955 | [link](https://www.kaggle.com/code/kurianbenoy/playing-with-clip-model?scriptVersionId=109012620) |
| Linear probing w/ ViT-H-14 | 0.71982 |  0.72583 | [link](https://www.kaggle.com/code/kurianbenoy/playing-with-clip-model?scriptVersionId=109012620) |
| Convnext model| 0.76149 | 0.75386 | [link](https://www.kaggle.com/code/kurianbenoy/fastai-baseline-albumentations?scriptVersionId=106051045) |

Note: This article was originally published in [Kaggle discussion here](https://www.kaggle.com/competitions/kaggle-pog-series-s01e03/discussion/362326)
