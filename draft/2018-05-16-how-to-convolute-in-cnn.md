---
title:  "Why deep learning for computer vision?"
date:   2018-07-23 10:00:00
comments: true
excerpt: "Design network architectures to solve computer vision tasks, why? "
tags:
  - [deep learning, computer vision]
---




These days I am reading computer vision papers. After reading a bunch of papers on image classification, object detection, segmentation, I realized the main theme emerging from the research approaches: to design CNN-based network, especially end-to-end architectures, to solve a specific CV task. I didn't think deeply about the rationale behind it until I read the FlowNet paper. FlowNet is a well-designed CNN architecture to estimate optical flow in the video. If there exist some good algorithms to calculate optical flow, why bother to design such a sophisticated CNN like FlowNet. It is like to calculate the mean or other straightforward statistics with CNN. It turns out that estimating optical flow is a much difficult problem, and FlowNet outperforms traditional computer vision methods regarding accuracy in small displacement, or even speed . ??

What kind of problem is CNN good at? The problems can't be well addressed by previous methods. Although I am quite new to CV, I have the gut feeling that the research trends in CV have shifted from designing better hand-engineered features to designing better architectures to enable CNN to extract features automatically. It all began since 2012 when AlexNet won the ImageNet classification contest. What I don't quite understand is why design different architectures or loss functions will incentify the deep learning model to approach an optimal hypothesis in the super high-dimensional hypothesis space?

This problem kept haunting me for a few days, until one night when I was preparing bath water for my toddler son. I threw a new toy into his bathtub and thought I will teach him how to play after my toothbrush. He already began to hold up the cup and observe how the water runs from different holes, which was exactly the action I was about to teach him! He is no longer the little baby whom I will need to teach for every step on how to play. As long as he is equipped with a variety of toys and environment, he can explore how to play with the new toys by himself, and acquire the desired skills and cognitive development spontaneously.

Then I connected my question with my son's story. As an analogy to human learning, previous CV research on hand-craft features is like teach an infant on how to play a toy. The adult needs to find the best route for each step: Step 1. (Run Harris algorithm to calculate descriptors) Step 2. (Detect faces based on the descriptors). Caution: Don't chew on it, or you will destroy the whole system!

Unlike babies, the machines will never grow up unless we change their paradigms. A machine equipped with enough data and a powerful learning algorithm is like a toddler whose mind is ready enough to begins to discover by himself. The rest of the question becomes, how to design the learning environment (model architecture) that could best facilitate the desired learning outcome (better performance on segmentation, object detection, etc.).

I guess that could be the intuition to my question of why bother to design sophisticated CNN architecture.

A few days later, two other readings coincidence my intuition. One is from the Deep Learning book,

 Convolution and pooling as an infinitely strong prior

Think CNN as a fully connected net with an infinitely strong prior. This prior says that the function the layer should learn contains only local interactions and is equivalent to translation and small translation (in the case of pooling layer).

Note: the structure of CNN gives prior constraints to the model before it has seen any data. The prior is based on the assumption for a specific task, such as in image classification, the detection of local features regardless of their variation is relatively crucial.


Learning is more like farming, which lets nature do most of the work. ML is all about letting data to do the heavy lifting. Farmers combine seeds with nutrients to grow crops. ML combine knowledge with data to grow programs
