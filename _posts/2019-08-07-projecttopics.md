---
title: Final Year Project Abstract
author: Kurian Benoy
type: post
url: 2019/08/07/capstoneprojectideas/
tags: 
- academic
- capstone project
---

According to our teachers before doing a project. The following premilinary
works needs to be completed:

1. Literature Survey
2. Formulate objective
3. Formulate hypothesis/design
4. Formulate of work plan
5. Seeking funds
6. Prepare preliminary report

## College Attendance monitoring/ footfall

Currently most of the colleges does attendance monitoring manually. The 
process of automating this process looks promising in the coming years.
Using face recognition, we can mark the corresponing attendance for each
student coming to college. And the footfall of students coming to the college
in general can be monitored by object detection algorithms like RCNN, YOLO,
Retinanet, .. and choose the best of the worlds.

Paper: in folder

## Medical Image segmentation for MRI data

Image segmentation is an important task in many medical applications. Methods based on convolutional neural networks
attain state-of-the-art accuracy; however, they typically rely on supervised training with large labeled datasets.
Labeling medical images requires significant expertise and time, and typical hand-tuned approaches for data augmentation
fail to capture the complex variations in such images. We present an automated data augmentation method for synthesizing
labeled medical images. We demonstrate our method on the task of segmenting magnetic resonance imaging (MRI) brain
scans. Our method requires only a single segmented scan, and leverages other unlabeled scans in a semi-supervised
approach. We learn a model of transformations from the images, and use the model along with the labeled example to
synthesize additional labeled examples. Each transformation is comprised of a spatial deformation field and an intensity
change, enabling the synthesis of complex effects such as variations in anatomy and image acquisition procedures. We
show that training a supervised segmenter with these new examples provides significant improvements over
state-of-the-art methods for one-shot biomedical image segmentation.

paper: https://arxiv.org/pdf/1902.09383v2.pdf
github: https://github.com/xamyzhao/brainstorm

## Medical Image classification of Retiopathy 

An easy way to detect diabetic retiopathy which causes bindness to adults.

. Aravind Eye Hospital in India hopes to detect and prevent this disease among people living in rural areas where medical screening is difficult to conduct. Successful entries in this competition will improve the hospital’s ability to identify potential patients. Further, the solutions will be spread to other Ophthalmologists through the 4th Asia Pacific Tele-Ophthalmology Society (APTOS) Symposium

Currently, Aravind technicians travel to these rural areas to capture images and then rely on highly trained doctors to review the images and provide diagnosis. Their goal is to scale their efforts through technology; to gain the ability to automatically screen images for disease and provide information on how severe the condition may be.

In this synchronous Kernels-only competition, you'll build a machine learning model to speed up disease detection. You’ll work with thousands of images collected in rural areas to help identify diabetic retinopathy automatically. If successful, you will not only help to prevent lifelong blindness, but these models may be used to detect other sorts of diseases in the future, like glaucoma and macular degeneration.

Detect there what stage a disease and at what stage is the disease?
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5961805/

## How closer are we to Human eyes?

We are currently working in projects and works with greater impact:
- CNN(can even beat a human in Imagenet challenge)
CNN is an architecture in my opinion which uses Max pooling to increase the image size, and use a filter to obtain the output from each layer. At the end you have fully connected layers which are capable of producing obtaining what the image is in typical CNN. fc for a single digit is 9.



## Text to speech system for generating ADS of famous people
Clone a voice in 5 seconds to generate arbitary speech in real-time.
https://github.com/CorentinJ/Real-Time-Voice-Cloning

[paper](https://arxiv.org/pdf/1802.08435v2.pdf)
