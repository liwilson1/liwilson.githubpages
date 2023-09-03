---
title: "Zero-Out Attack on VGG-16 Image Classification"
date: 2023-08-31T14:35:42+12:00
author: "Liam"
draft: false
ShowToc: true

cover:
    image: "https://www.kaggleusercontent.com/kf/141402973/eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0..nCsNAwZk9dCv0XTODRR8Nw.IgGNfBgBuenV_nvoEGQxG2aW3kz-cRg4lfIuwKmJCTWAz2Bw3--IhSAWXEubJDt1yHo5px0jm625nZ9DwKviw_tpnV8Th0lwwPOYP0awwVPgA4xWQgD_x6YXhG8PARIK2b4zSMutZHrz5v7s3MEfNdarRBawNzDD9oymzWzapxqVCOpwtqTzI5y_ocQA_V9X5Zsl2dfh4006A8z1xbI5l6_Ew08Fe1UJ8Q_BGWwWFVS8G36TnT9Wn0qVRiF4z9Ci6rp7VyGe9iLLsPnYWtKZN-H0XOw9mI-xThUQhILQvmG5QMNo5x_uwyVDUvR68xJGGGZnWfEfCPCN2h6Jgq1Oe-382buaRwj1OUJeuOrdX1lBQPnXv0vYTLLlgllBlylKA4J3H1JiYxFe0H9MaKozZsWWpNxP8iRHB8qvoWGW6QWen6ue3xGq3jVqrSCZ6g70XB3HuljA3UMz1_cotYAOziPwePw0tj18zZpL_TA38XYpz6ul9jJ9_96Q5m66ijrh7gRYad_CtrLa8lLmuAKhqNBqGMU9iGjjNwe6F9JZEOsf6pfkTJjwTgdIbU_UNjCf4__d70pKFpLluK2Q3ig6DhNLSKz5Qyoset1Q0joU4-iqE-fqG_hVP-ocNfJO0hkq59oEdNM-Ih7dXjQTDuIXyA.l8t9yj26KxURmxMa7VZ83A/__results___files/__results___19_0.png"
    alt: aaa # alt text
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