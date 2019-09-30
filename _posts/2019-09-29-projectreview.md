---
title: Pinch of old project
author: Kurian Benoy
tags: ['Image classifier', 'Medium']
---

So our projects aim was to create an app which was to:

1.Which automatically detects the plants whenever you walk in a garden and tell what plant it is.
2.On top of it if you like the plant we detected we will connect you to plant producers who sell that plant in your locality.
3.Identify plant from an image you showAs from the article, we need to collect photos of indigenous plants from my area.

I created a dataset of 10 types of Trees in Indian-continental condition with about 1000 images for each plant. I created this dataset using the [google-images-download library](https://github.com/hardikvasa/google-images-download). It's pretty straight forward to use:

```googleimagesdownload --keywords "Polar bears, baloons, Beaches" --limit 20```

I remember to download more than 100 images we need to insert an API key, or something like that. More documentation can be found [here](https://google-images-download.readthedocs.io/en/latest/examples.html).

I created an ML model using tensorflow by using a custom model which was retrained using Inceptionv3 model. retrain.py file from Tensorflow was used for this project. If
I am implementing my prject currently I would prefer to use more efficent architectures like Resnet 50, Efficent Net and others.

The model was neatly made into an App by my friend using Kotlin. Then came another issue, that is ML model was about 90-100 MBs and big size is always an issue for the app.
For model deployments, tensorflow created an API called TensorflowLITE which can substantially make your models very light about 8 MB. We dropped aim (b), as creating such
partnership didn't look feasible.

The developed apps demo for this can be found in my Linkedin Post
[here](https://www.linkedin.com/in/kurian-benoy-75642b120/detail/recent-activity/shares/) which was made one year back
and the source code of [old Machine Learning model is](https://github.com/kurianbenoy/Plantcrypto-recogniser).


