---
layout: post
title: Seminar ideas
comments: true
---


We are currently working in projects and works with greater impact:
- CNN(can even beat a human in Imagenet challenge)
CNN is an architecture in my opinion which uses Max pooling to increase the image size, and use a filter to obtain the output from each layer. At the end you have fully connected layers which are capable of producing obtaining what the image is in typical CNN. fc for a single digit is 9.

## 1. Stacked Capsule Encoders(suitable for the final year seminar)

- [blogpost](https://akosiorek.github.io/ml/2019/06/23/stacked_capsule_autoencoders.html)
- [research paper](https://arxiv.org/pdf/1906.06818.pdf)

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

- [Paper](https://arxiv.org/abs/1812.01718)

## Data Augmentation using Learned transformations for one-shot medical image segmentation

- [paper](https://arxiv.org/pdf/1902.09383v2.pdf)

Update: on August 7

Finally the paper of Deep Learning for Classical Japenese got selected by sir. 


<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://https-kurianbenoy-github-io.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>

