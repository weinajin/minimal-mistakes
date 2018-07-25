---
title:  "Human learning as an analogy of machine learning"
date:   2018-07-24 10:00:00
comments: true
excerpt: "We have accumulated abundant intuition in human learning. Maybe such intuition is transferable to guide machine learning practice at the macro level."
tags:
  - [deep learning, computer vision]
---


These days, during my reading of computer vision papers, I discover a recurrent theme: to orient CNN-based network to a specific CV task, most papers focus on designing new architectures of the network and/or loss functions. This approach seems obvious. And the Deep Learning book also suggests:

> If gathering much more data is not feasible, the only other way to improve generalization error is to improve the learning algorithm itself.

I didn't think deeply about the rationale behind it until I read the *FlowNet* paper. *FlowNet* is a CNN invented to estimate the optical flow in videos. I was wondering if there already exists some methods to calculate optical flow, why bother to design such a sophisticated CNN architecture. It is like to calculate the mean or other straightforward statistics with a neural net, or to use a cannon to kill a mosquito. It turns out that estimating optical flow is a more difficult problem (don't know if it is an "AI-complete" problem), and *FlowNet* showed neural net is feasible for such task regarding speed and accuracy.


Although I am a novice to CV, I have the gut feeling that the research trends in CV have shifted from designing better hand-engineered features to designing better architectures that enables CNN to extract features automatically. It all began since 2012 when *AlexNet* won the ImageNet classification contest. With enough data, automatic feature extraction outperforms hand-engineering features in a number of ways: more accuracy, more adaptive to the problem, end-to-end training. One thing in common though, is that both requires extensive human design effort. It's true that deep learning models require less domain knowledge than hand-engineering approach, but still, it relies on the careful design of network architecture and/or objective function.



Investing extensive human effort in the design of better features, the rationale is obvious: we program the machine to computer step 1, 2, 3 to get the desired output. The process is like developing a new recipe, the outcome is more or less deterministic as long as you follow the procedure. The model does not care about the end goal, it is only an executive machine. In contrast, the deep neural network is less controllable by its designer (and so less interpretable). That's why many machine learning partitioners call it alchemy. Then, how does the intuition-guided design of the network will lead to the search of an optimal hypothesis in the stochastic super high-dimensional hypothesis space?

This problem kept haunting me for a few days, until one night when I was preparing a bath for my toddler son, I threw a new toy into his bathtub and plan to teach him how to play later. To my surprise, just during the several minutes of my teeth brushing, he had already played with it just as I expected! At that moment, I realized that he is no longer the little one whom I will need to teach everything step-by-step. As long as he is equipped with a ready mind, a variety of toys and a supportive environment, he is capable to accomplish desired tasks with little to no guidance.


At my son's bathtub, I suddenly began to connect my question with my son's astonishing development, and see human learning as a metaphor for machine learning. Previous CV research on features engineering is like teaching a baby to accomplish a task. Parents need to design the best steps (features) for the baby (traditional ML model). When a baby's brain developed to a certain degree (or when we change the paradigm of a model to enable it to learn on its own and equip it with enough data), a toddler (deep learning model) will discovery patterns to solve the problem by himself, and the child's patterns are also invisible and uninterpretable to parents.

For parents, some of the child's priors are not changeable, such as the gene. To facilitate the desired learning outcome, the changeable prior is the learning environment. As an analogy, for researchers, in the context that the size of the dataset can not be extended, the only prior that researchers can work on is the model architecture. Then the rest of the question becomes, how to design the learning environment (model architecture) that could best facilitate the desired learning outcome (better performance on CV tasks). I guess that could be the intuition to my question of why bother to design sophisticated CNN architecture.

When we look down into the model to observe how each parameter works to the learning outcome, it is similar to dive into the molecular level of the neuron in the child's brain to see how learning happens. We humans don't have much intuition at the micro level. But we have abundant experience at the macro level, which is the day-to-day human learning. Maybe such intuition is transferable to guide machine learning practice at the macro level.
