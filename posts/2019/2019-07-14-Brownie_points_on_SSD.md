---
aliases:
- /Deep Learning/linux/python/2019/07/14/Brownie_points_on_SSD
author: Kurian Benoy
categories:
- python
- linux
- Deep Learning
date: '2019-07-14'
layout: post
title: Brownie points on Single Shot Multibox Detector

---

In this article, I am going to talk about Single Shot Multibox Detector(SSD) which one of the algorithms which does object detection. SSD is known for detecting objects in real time faster compared to other algorithms.

*If you are new to object detection, it can be simply defined as understanding what all are the objects in an frame. There are number of other algorithms like RCNN, fast RCNN, faster RCNN which perform object detection. Yet the problem is usually most of algorithms suck in real time performance.*

- Extremely good in detecting objects of large size in real time
- creates anchors through forward pass and obtains the result  in the sufficient ways
- 8732 boxes on building on base network of vgg16
- According to original research paper, we are able to obtain 74% mAP at 59 FPS for PASCALVOCC2007 test
- It created by single shot, multi box, detector
- loss = confidence loss + location loss
- Always classification loss should be small
- quite fast detection results
- SSD-500 and SSD-300 are of two types. The difference between both models are that: SSD300 uses 300px size images while SSD500 uses 512px size.
- a real time detector compared to faster R-CNN, faster RCNN, fast RCNN
- SSD architecture builds on the venerable VGG-16 architecture, but discards the fully connected layers. The reason VGG-16 was used as the base network is because of its strong performance in high quality image classification tasks and its popularity for problems where transfer learning helps in improving results. Instead of the original VGG fully connected layers, a set of auxiliary convolution layers (from conv6 onwards) were added, thus enabling to extract features at multiple scales and progressively decrease the size of the input to each subsequent layer.
- Multi Box an Inception-style convolution network is used. The 1x1 convolutions that you see below help in dimensionality reduction since the number of dimensions will go down (but “width” and “height” will remain the same).
- confidence loss is computed by cross-entropy
-  The major difference between SSD and other detector algorithms, is the usage of region proposals which uses ground truth information which needs to be assigned to specific outputs in fixed set of Detector algorithms.
- For each default box, we predict both shape offsets and confidences for all object categories
- For a feature layer of size m*n where the kernel is applied, it produce an o/p layer which uses `3*3*p` small kernels.
- For each feature maps, it creates a set of kernels which can do unprecedented things, like understanding the relationship of what object needs to be recognised in Internet

### References

- [SSD Original Paper](https://arxiv.org/abs/1512.02325)
- [Review-SSD](https://towardsdatascience.com/review-ssd-single-shot-detector-object-detection-851a94607d11)
