---
title:  "Nested cross validation explained"
date:   2018-08-25 17:00:00
comments: true
excerpt: "Using two-round cross validation for model selection and performance evaluation."
tags:
  - machine learning
---

It is natural to come up with cross-validation (CV) when the dataset is relatively small. The basic idea of cross-validation is to train a new model on a subset of data, and validate the trained model on the remaining data. Repeat the process multiple times and average the validation error, we get an  estimate of the generalization performance of the model. Since the test data is untouched during each training, we kind of use the whole dataset to estimate the generalization error, which will reduce the bias. However, since it will train multiple models instead of one, the drawback of CV is that quite computational expensive.

It is necessary to make it clear that, the aim of CV is **not to get one or multiple trained models for inference**, but to **estimate an unbiased generalization performance**. This may be quite confusing at beginning, since the outcome of the common train/validate/test split approach are a trained model with tuned hyperparameter (on train/validate set), plus a generalization estimation of performance (on trainval/test set).

Why bother to have a validation set? Why not just use the test set for the two tasks of hyperparameter tuning(model selection) and estimation at once? The problem is, if we use the test set multiple times for different trained models, during our selection of the optimal model, the test set actually "leaks" information, and thus unpure. When we later apply the model to real-world data, the model will probably have larger error than on the test set. That being said, when using the test set for both model selection and estimation, it tends to overfit the test data, and the estimation tends to be optimistic.

When doing one round CV to evaluate the performance of different models, and select the best model based on the CV results, it is similar to the above case of using test set both for model selection and estimation. Thus, when we want to perform model selection and generalization error estimation, we have to separate the two tasks by using two test set for each task. That's why we have the validataion and test set, and the version in CV is a nested or two-round cross validation.



As the hyperparameter tuning and model performance estimation are two steps in the train/validate/test approach,

When related to the real world application, doing one round CV is usually not good enough, because builing a model usually involves two steps: 1) tune  hyperparameters, and 2) evaluate the final performance. Doing one round CV for the two purposes is problematic, which I will explain later.

Of course, we can also achieve the two purposes without CV. The more common way is to split the whole dataset into three sets: training, validation, and test set. We first put aside the test set to keep it untouched. We use the **validation set** served as the test set to guide the **model selection and hyperparameter tuning** process. After we selected the model with the optimal performance on the validation set, we use the **test set** only once to **evaluate generalization performance** on unseen data. The test set is be a good estimation of the generization error when we further implement the model as real world applications.

The common cross Validation


Dateset Functionality
Validation set model selection and hyperparameter tuning
Test set evaluation of generalization error

avoid using the same set for model selection/hyperparameter tuning and evaluation. validation for hyeprparameter tuning; test set for model performance evaluation.

in case of small dataset, nested cross validation.
https://stats.stackexchange.com/questions/266225/step-by-step-explanation-of-k-fold-cross-validation-with-grid-search-to-optimise

inner loop:


outer loop:


Questions
1. Can I use the best hyperparameter selected in the first outer fold, and use it for the rest of the outer k-1 fold? So that to save the outer k-1 * inner k times' training.
I think the answer is no.

2. What if the inner CV selected different models (hyperparameters)?
ensemble learning, esimate of the performance and error from multiple models

Benchmark overfit

All the inner CV will select the same model when the model is stable. I think it is more likely to get multiple models within each run of CV. But I'm not quite sure how to report the optimal hyperparameters in the paper.

---
### References

[1] T. Hastie, J. Friedman, and R. Tibshirani, “Model Assessment and Selection,” in The Elements of Statistical Learning: Data Mining, Inference, and Prediction, T. Hastie, J. Friedman, and R. Tibshirani, Eds. New York, NY: Springer New York, 2001, pp. 193–224.


[2] G. C. Cawley and N. L. C. Talbot, “On Over-fitting in Model Selection and Subsequent Selection Bias in Performance Evaluation,” Journal of Machine Learning Research, vol. 11, no. Jul, pp. 2079–2107, 2010.

---
Again, this post reflects my current understanding of the cross validation. Please correct me if you identify any problems.
