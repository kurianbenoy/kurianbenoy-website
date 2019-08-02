---
layout: post
title: Seminar ideas
comments: true
---
[Draft]Final Year Project Ideas

How closer we are to automous eyes?

We are currently working in projects and works with greater impact:
- CNN(can even beat a human in Imagenet challenge)
CNN is an architecture in my opinion which uses Max pooling to increase the image size, and use a filter to obtain the output from each layer. At the end you have fully connected layers which are capable of producing obtaining what the image is in typical CNN. fc for a single digit is 9.

Stacked Capsule Encoders(suitable for the final year seminar)
- very interesting paper, get into more details of it.
https://akosiorek.github.io/ml/2019/06/23/stacked_capsule_autoencoders.html

In summary, a Stacked Capsule Autoencoder is composed of:
- the PCAE encoder: a CNN with attention-based pooling, 
- the OCAE encoder: a Set Transformer, 
- the OCAE decoder: 
K
MLPs, one for every object capsule, which predicts capsule parameters from Set Transformer’s outputs, 
K×M
constant 3×3
matrices representing constant object-part relationships, 
and the PCAE decoder, which is just M
constant part templates, one for each part capsule. 
SCAE defines a new method for representation learning, where an arbitrary encoder learns viewpoint-equivariant representations by inferring parts and their poses and groups them into objects. This post provides motivation as well as high-level intuitions behind this idea, and an overview of the method. The major drawback of the method, as of now, is that the part decoder uses fixed templates, which are insufficient to model complicated real-world images. This is also an exciting avenue for future work, together with deeper hierarchies of capsules and extending capsule decoders to three-dimensional geometry. If you are interested in the details, I would encourage you to read the original paper: A. R. Kosiorek, S. Sabour, Y.W. Teh and G. E. Hinton, “Stacked Capsule Autoencoders”, arXiv 2019.

## Deep Learning for Classicial Japanese(seminar)

https://arxiv.org/abs/1812.01718

{% if page.comments %}
{% endif %}
