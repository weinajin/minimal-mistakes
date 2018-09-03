---
title:  "Tips and pitfalls of deep learning practice"
date:   2018-09-02 10:00:00
comments: true
excerpt: "Personal experience of machine learning practice"
tags:
  - [machine learning, deep learning]
---

1. Don't add activation function of the output layer. For classification, the softmax activation is incorporated with the loss function in pytorch and keras API. So we only need to feed the raw logits (rather than the sigmoid or softmax score) to the loss function.
