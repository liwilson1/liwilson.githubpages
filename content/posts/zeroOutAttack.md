---
title: "Zero-Out Attack on VGG-16 Image Classification"
date: 2023-08-31T14:35:42+12:00
author: "Liam"
draft: false
ShowToc: true

cover:
    image: "comparison.png"
    alt: Comparison figure of zero-out method # alt text
    caption: VGG-16 predictions before and after applying the zero-out method to an image. [The Kaggle notebook for this demonstration](https://www.kaggle.com/code/liamwkaggle/zero-out-attack) # display caption under cover
    relative: true # when using page bundles set this to true
    hidden: false # only hide on current single page
params:
    ShowBreadCrumbs: 
    ShowPostNavLinks: true
---

## Glossary
### Image classification
Image classification is the task of assigning an input image one label from a fixed set of categories.

### Transfer learning
Transfer learning is a machine learning technique where a model trained on one task is re-purposed on a second related task. It is a popular approach for image classification as there
are many pre-trained models available for use.

### VGG-16
![VGG-16 structure](https://miro.medium.com/v2/resize:fit:470/1*3-TqqkRQ4rWLOMX-gvkYwA.png#center)
VGG-16 is a convolutional neural network architecture that was the runner-up in the ImageNet Large Scale Visual Recognition Challenge 2014. It is a popular model for transfer learning.


## Zero-Out Attack
The zero-out attack is our method of attacking an image classification model built using transfer learning. The attack involves changing the pixels in an image so that each value in the output of the last layer of the pre-trained model becomes zero.

When the output of the last layer is close to zero, the classification model on top of the pre-trained model will have a hard time classifying the image, as it hasn't gained any knowledge from the pre-trained model.

### Demonstration
To show that it works, I have put together a Kaggle notebook that applys the method to an Albatross image and then predicts its class using the VGG-16 model. The notebook can be found [here](https://www.kaggle.com/code/liamwkaggle/zero-out-attack). VGG-16 correctly identifies the image as an Albatross with a probability of 0.99. After the attack, it's top prediction is a bucket with a 0.0045 probability.

## Next steps
We are working on a defense against a zero-out attack, and then creating a new similar method that can bypass the defense.