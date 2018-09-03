---
title:  "[Reading] Interpretability of Machine Learning Models"
date:   2018-08-25 10:00:00
comments: true
excerpt: "Paper reading notes"
tags:
  - annotated bibliography
---

1. J. D. Fauw et al., “Clinically applicable deep learning for diagnosis and referral in retinal disease,” Nature Medicine, p. 1, Aug. 2018.

    **two steps segmentation and classification, clinical applicable**

    This is a recent joint work from DeepMind and clinicians. Several reasons prevent the deep learning for medical imaging analysis to be applied in clinical settings and make a real-world impact. One is that the "black-box" nature of deep learning model. Doctors will need to be convinced and understand why to make such a decision before taking an advice from the AI system. The other reason is some of the current deep learning techniques do not address the real-world clinical problems and cannot incorporate the AI tools into the clinical workflow. This work provides a framework to address the two problems.

    Automated diagnosis of medical images faces two main challenges: technical variations in the imaging process, and patient-to-patient variability in disease pathological manifestations. Existing deep learning approaches tried to deal with all combinations of these variations using a single end-to-end black-box network, thus requiring millions of labeled scans. The authors **decouples the two problems**, and use a deep segmentation network (3D U-Net) to generate tissue-segmentation map that is device-independent. It is followed by a deep classification network to detect the pathology variants. The classification network is a 3D convolutional network applied dense blocks. It outputs a 14-dimensional vector consists of one of four referral decisions, and the presence or absence of multiple retinal pathologies. This decoupled framework reduces the required number of labeled data to train the network, and enables doctors to review the segmentation map for sanity check.

    IMHO, the decouple framework is a brilliant insight and similar to the doctors' interpretation process of a medical image. Doctors first identify *where* the lesion locates and *what* is the character of the lesion. Doctors and radiologist use text report to communicate such information. Here, the tissue-segmentation map acts the same role. Then doctors make a conclusion and diagnosis based on that, which is done in this paper by the classification network.

    To address the ambiguous regions in segmentation maps, the authors used ensemble learning and trained multiple instances of the segmentation network, resulting in multiple hypotheses. Analogous to multiple human experts, these segmentation maps agree in areas with clear image structures while disagreeing in ambiguous low-quality regions.

    To evaluate the framework's performance, a golden and silver standard labels are defined and acquired for the test set. The golden standard labels of the referral pathway and final diagnosis were acquired retrospectively by examining the patients' records. It was used to evaluate the performance of the model and compare it with doctors. For the referral recommendation, the accuracy rate of the model is equivalent to the highest performance of two experts, and significantly better than the rest of doctors when doctors' decisions were made solely on the images without clinical history. The silver standard labels were defined as the pathological diagnosis and were labeled by eight doctors using the majority votes. The AUROC of the model was over 99% for most of the pathologies. To generalize the model to new device images, the whole model didn't need to be retrained from scratch. Instead, only the segmentation model was retrained on 152 samples and achieved similar results to the one on the old device.




1. M. D. Zeiler and R. Fergus, “Visualizing and Understanding Convolutional Networks,” arXiv:1311.2901 [cs], Nov. 2013.

    **Visualization**

    This is an earlier and influential work that visualize the deep weights in CNN. To visualize the invariance of the kernels in a well-trained convnet, the authors devised a deconvnet. A convnet maps pixels to features, while a deconvnet does the opposite by mapping the feature activations back to input pixel space. The deconvnet is attached to each of the convnet layers with the corresponding layers of unpool, ReLu and filter to reconstruct an image from feature map. An input image first is feed to the trained convnet and features compute throughout the layers. To examine a give convnet activation, they set all other activations in the layer to 0 and pass the feature maps as input to the attached deconvnet layer. The visualization shows that as the layer goes deeper, the network tends to composite the features from the previous layer to form complex patterns. Different kernels are also responsible for different class discrimination.



1. W. Gale, L. Oakden-Rayner, G. Carneiro, A. P. Bradley, and L. J. Palmer, “Producing radiologist-quality reports for interpretable artificial intelligence,” arXiv:1806.00340 [cs], Jun. 2018.

    **generate text report from image**

    This work focuses on produce descriptive sentences to clarify the decisions of deep learning classifiers. Previous related work on generating text from medical images failed to reproduce the whole medical reports convincingly. Instead of trying to reproduce the whole reports, the authors attempt to generate formatted text explanations with consistent structure and limited vocabulary to achieve model explainability.

    To do so, the authors build an image-to-text model using RNN with a visual attention mechanism. The deep learning classifier is a trained DenseNet to classify hip fractures from frontal pelvic X-rays with a AUROC of 0.994. The input image is fed to the DensNet to generate an activation map. The activation map along with the previous hidden state of LSTM is fed to a soft attention to retrieve the relevant information for the next step, and after a dropout layer are fed to a two-layer LSTM. In each timestep, the LSTM output a word embedding of the next generated word.

    The generated text showed a high level of reproduction accuracy measured with BLEU score. A usability test shows that doctors prefer the text to saliency maps alone, but the combination of visualizations and the generated text is better than either alone.
