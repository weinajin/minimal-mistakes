---
title:  "A friendly introduction to convolution in CNN"
date:   2018-05-16 17:00:00
comments: true
excerpt: ". "
tags:
  - cnn
---


A friendly introduction to convolution in CNN

"Convolution" is one of the most mysterious words for a novice deep learner. The first time when I opened [wikipedia on convolution](https://en.wikipedia.org/wiki/Convolution) and tried to make sense, I just got dizzy and lost. After a long time mingling with CNN and a bit on signal processing, I finally figure it out a little better. In my current understanding, the convolution is just **a fancy operation of weighted sum**. Here is the story:

To see what is a weighted sum, Let's begin with the following expression, which may remind you of algebra in high school:

y = w1 * x1+w2 * x2

y = \sum w_i * x_i

The different weights reflect how important you think of each variables x_1 and x_2. For example, if you want to calculate a class score from the midterm exam and final exam, the weights reflect how you value each exam score. **Weights reflect how important you think a variable is in a numerical perspective**. And **sum is just an operation that condenses your deliberate thought on each variable into one final value** (like the final score).

]//As a side note, I'd like to regard it as the projection from high dimensional space (where all x_i reside) to 1 dimension (y is just a dot). But if you don't understand this paragraph, you can go ahead to ignore it. It will have little to do with the whole story.

This works totally well when the number of x_i  is small. But what if the number of x_i becomes large, say 1,000,000, or even infinite, how do we assign each x_i a weight respectively?

Here are the tricks:
Instead of using a single number $y$ to describe $x$ sequence, now we use a group of numbers. That's because a single number compresses the information of too much so that it could not reflect the character of $x$ very well.

To generate a sequence of numbers out of $x$, there are many different ways. If we assign all the $x$ with the same weight, it doesn't compress nor extract any new information from "our perspective". It equals? to treating each $x_i$ equally, therefore doesn't add our additional thoughts on different characters in $x$. Another extreme is to assign each $x$ with a distinct weight. This reflects our thought on each $x_i$ in very fine detail, but it is too costly and redundant to express the weight sequence: we'll need to use as many as the numbers in $x$ to express the weights.

How to express rich weights that represent our thoughts, meanwhile keep the weight size as small as possible?
One solution is to use repetitive weight sequence. In this way, we can repeat the weight as many as the number of $x$, meanwhile, we can express it with a short sequence of numbers. If we notice there are repetitive patterns in many sequences, such as ups and downs, this approach makes more sense.

Condense the local information from x_i and its neighbors.
It's like playing a pattern matching game, which you try to identify a pattern from a large picture.

For now, we've talked a lot about the sequence, but what does it to do with convolution and image, you may ask. The above is just how to calculate convolution in 1-dimensional data. The convolution in CNN for analyzing image is exactly the same way, with the extension to 2-dimensional image data.


When I get to know more details about it, and implemented. I found it is no more than an operation.


Convolutional layer is the basic and main building block of CNN (Convolutional Neural Network). I recently began to understand more about the convolution computing after a long path. One of my recent question is:

> For the input layer, how do I convolute the RGB color image?

Unlike the grayscale image which is a matrix,

---

May 18
The convolutional layer is the basic and main building block of CNN (Convolutional Neural Network). I recently began to understand more about the convolution computing after a long path (from CNN, to signal processing, to image processing, back to CNN). This post mainly answers one of my recent questions:

> To feed a color image into the CNN, how do I convolute the image consists of 3 color channels of RGB?

The short answer is: make * the filter to be 3-dimensional * as well, and * sum up * the convoluted results to be a single channel feature map.

1. Why extend the filter to be 3-dimensional as well?
We can think it in this way: for one-dimensional signal, the filter is as designed as a 1-d array. For grayscale image, the filter is a 2-d matrix. 以此类推, for the 3-layer color image, the filter is also 3-layes accordingly.

2. Why sum up the 3 convoluted results?
The convolution computation works as follows:

The intuition of filter

The assinged weight for each grid of pixels.

Code implementation


Unlike the grayscale image which is a matrix,

June 12
What's the difference between conv over 3d and 3d CNN, how about 3d CNN with conv over 3 RGB channels (combined the two)?

#ml #AB
