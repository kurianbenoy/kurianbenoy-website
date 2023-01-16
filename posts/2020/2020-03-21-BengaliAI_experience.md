---
aliases:
- /coding/kaggle/2020/03/21/BengaliAI_experience
author: Kurian Benoy
categories:
- coding
- kaggle
date: '2020-03-21'
layout: post
readtime: true
title: Bengali AI Competition Experience

---

Thanks to Kaggle and Bengali AI for organising this competition. I would like to congratulate all the winners of this competition.

```
Public LB:  0.9749(Rank 297)
Private LB: 1473
```

I  joined this competition when it was started, yet only got actively involved in this competition after @seesee  released his public notebooks on using TPUs. At that time, I was participating in Kaggle’s flower recognition competition(Playground) and was able to understand what @see--- Notebook did.

After a bit of fine-tuning, with hyperparameters(changing to EfficientNet B4) and training for 30 epochs, I was able to get a score of 0.9729. I was all excited because it was the first time I got a higher score than the best available public kernels available(in a live competition) at that time +  I didn’t make many changes to original kernel.

Last 7 days of the competition was full of excitement for me(as my college was shut down due to Covid-19 situation in Kerala, India). After getting this initial result, I read through almost all the posts in discussions.I tried a variety of ideas and organised them as github issues(suggestion from my teammate). I tried to implement augmentations like Mixup, Cutmix, Gridmask etc(Thanks to @cdeotte, @xiejialun  Notebook from Flower classification with TPUs notebooks). I tried training on all the architectures of EfficientNet from B3 to B7. I started retraining my models with weights from already available model, yet for me always retraining on weights made my model perform worst.

For me this competition was like @init27 saying, kaggle competition felt like a 100 Mile sprint where you are competing against people on Supercars (GrandMasters with a LOT of experience) while I was running barefoot.

I tried changing with other architectures like Densenet 169, 121. Yet single models based on this approach was not so effective. After doing all these experiments for the last 4-6 days, I was not able to improve my model, any further. It gave me a feel when all the Kaggle grandmasters and masters were able to implement ideas and do things quickly, I was not able to perform so well. I saw a lot of failed ideas, and even after reading lots of papers I was not able to transform certain augmentations into Tensorflow for BengaliAI competition from Flower Classification with TPUs competition.

On the final day of competition, I trained my model with EfficientNetB4 for 30 epechs, with step learning rate and decay. And I was able to obtain my highest score of 0.9749 in public LB(which was able to have a better score than the best public kernel available then). I tried ensembling weights with Densenet, but it didn’t work out any good. 

For me, this competition was a huge learning experience for me and I was able to spend about 100+ hours for this competition and learned a lot of new things from experienced folks here. I would like to thank @hengck23  for encouraging to share the solution. 

Obviously, after the competition, I got a lot of new insights which I am trying to ponder and experiment more in the coming days(both in Tensorflow and Pytorch).
