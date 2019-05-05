---
title:  "Paper Reading Notes on AI, HCI, decision-making, and explaination"
date:   2019-05-02 10:00:00
comments: true
excerpt: "My recent paper reading notes, loosely organized chronologically (mainly pasted from Mendeley)"
tags:
  - paper reading
---


1. Pearl, J. & Mackenzie, D. The book of why : the new science of cause and effect.

Apr26 - May5

I know this book from another book "possible minds" where Pearl talked about the limitations of opaque learning machines. I was fascinated by the examples Pearl gives about the transparent-vs-opacity contrast of Greek and Babylonian astronomers. Although Babylonian astronomers were masters of black-box predictions and had better accuracy to their Greek rivals. Greek astronomers, in contrast, use wild modelling strategy with metaphorical imagery. Such a model- rather than a function-based approach incubates the modern astronomy. Similar cases also occur repetitively in history, such as why the science is not born in China, instead of in the west, although the ancient Chinese has advanced the knowledge in nature. But such knowledge is only for application purpose, not for scientific discovery which requires generalization and abstraction of such knowledge.

The above examples are good motivations for explanation requirements in model ML models. Although Pearl did not provide an explicit explainable AI approach in "the book of why", it tells a complete story about the elements and development of causal inference. Current big data and DL approaches are at the level of correlation inference. In statistics, we always remind ourselves that "correlation does not imply causation". We need such frequent reminder because our brain is wired to process causality. Thus, it seems like talking about causality is a taboo in statistics. In the first half of the book, Pearl tells the story of how the Causality Revolution happened under such environment. The causal diagram, which is similar to the author's invention, Bayesian diagram, is a good tool to be coupled with the data to do causal inference. They have different ways to deal with confounders (back and front door adjustment, instrumental variables), so that with only the observational data and the causal diagram, we can make causal inference without having to conduct a randomized controlled trial! Such tools can even enable us to do counterfactual reasonings.

---

1. Darwiche, A. Human-Level Intelligence or Animal-Like Abilities? (2017).

May2

This is a high-level commentary work from the conversation of the authors with many other people in and outside AI communities, on the current trends in AI. I get to know this work from Pearl's "the book of why". It sees the current deep learning trend as the curve fitting for the cognition functions (vision, language, speech recognition). It negates the recent progress in DL and contributes them to merely the improvement of computational power and data (which is true. It points out that NN is invented long ago).

It also emphasizes on the explainability challenge in AI. A model-based approach can allow AI users to ask more questions (what if, counterfactual) that are beyond the ability of the function-based approach (rely on data-collection, input-output mapping). In this part, he quotes Judea Pearl in the book of why ch1:


> There is only one way a thinking entity (computer or human) can work out what would happen in multiple scenarios, including some that it has never experienced before. It must possess, consult, and manipulate a mental
causal model of that reality.

It points out that "the vocabulary of (existing) explanations is restricted to the function inputs" (feature attribution). These limited vocabulary face challenges when encountering novel situations. According to Pearl, "model-based explanations are also important because they give us a sense of “understanding” or “being in control” of a phenomenon".

In the end, it points out the future challenge of AI should be combining the model and function based approaches(mapping them to slow and fast human thinking, which is interesting).
