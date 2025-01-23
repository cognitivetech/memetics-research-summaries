# Enhance Multimodal Model Performance with Data Augmentation: Facebook Hateful Meme Challenge Solution

[Enhance Multimodal Model Performance with Data Augmentation: Facebook Hateful Meme Challenge Solution](https://arxiv.org/abs/2105.13132)

## Table of Contents
- [Abstract](#abstract)
- [1. Introduction](#1-introduction)
- [2. Method](#2-method)
- [3. Experiments and Results](#3-experiments-and-results)
	- [3.1. Model Screening](#31-model-screening)
	- [3.2. Fine Tuning](#32-fine-tuning)
- [4. Conclusion and Future Work](#4-conclusion-and-future-work)

## Abstract

**Hateful Content Detection Using Deep Learning:** Hateful Memes Challenge Solution
* **Contributors:** Yang Li, Zinc Zhang, and Hutchin Huang (Georgia Institute of Technology)
* Email addresses: yli3297@gatech.edu, zzhang889@gatech.edu, hhuang400@gatech.edu

**Abstract:**
- Hateful content detection: significant improvement using deep learning in this area (Facebook Hateful Memes Challenge)
- Utilization of multi-modal pre-trained models VilBERT and Visual BERT for detection
- Data augmentation used to enhance model performance
- Enlarging training data set resulted in a more than 2% boost in AUROC with the Visual BERT model
- Achieved impressive results: 0.7439 AU-ROC, 0.7037 accuracy on test set
- Code available at: https://github.com/yangland/hatefulchallenge.


## 1. Introduction

**Hateful Memes Challenge**
- Data set from Facebook introduces messages with both text and image (Figure 1)
- Traditional NLP and image processing methods struggle due to uni-modal nature

**Investigation under Facebook’s MMF Framework:**
- Evaluate performances of multi-modal models
- Propose modal turning options for solutions

**Hateful Memes Dataset**:
- Contains 10,000 meme records
- Cannot be used solely for training due to small size and need for comprehensive background knowledge
- Requires further tuning for specific hateful meme identification task

**Multimodal Learning Model**:
- Connects images, natural language, and attention between them
- Representation model is task-agnostic
- Needs additional turning for the hateful meme challenge

**Visual Question Answering (VQA) and Visual Common Sense Reasoning (VCR):**
- Tasks tested in ViLBERT Research
- Require cross-attention between text and image
- Background knowledge base not present in current information

**Potential Applications**:
- Help social media companies like Facebook and Twitter by automating inappropriate post identification
- Guide publishers, media, and individual users to prevent potentially harmful content publication
- Improve reasoning and common sense for visual-text contents

**Data Sets Used**:
- Hateful Memes dataset from official Facebook Challenge website
- Four development sets: train (8500 labeled samples), dev seen (500 labeled), dev unseen (540 labeled), test seen (1000 unlabeled), and test unseen (2000 unlabeled)
- Pretrained models from Facebook’s MMF framework: COCO, COCO17, Conceptual Captions, VQA2.


## 2. Method

**Approach Overview:**
* Divided into two parts: model screening and fine tuning
* Model screening: compare pre-trained models on Hateful Memes dataset using same training routine
* Compare models qualitatively and quantitatively through accuracy and AUROC
* Utilized models from MMF's "model zoo": MMBT, VilBERT, Visual BERT, mmf transformer, FUSIONS (ConcatBERT, Late Fusion)
* Workflow: Figure 2

**Model Screening:**
* Part of approach to compare pre-trained models on Hateful Memes dataset
* Same training routine with fixed epoch of 3,000
* Qualitative and quantitative analysis using accuracy and AUROC
* Prevent overfitting by exploiting "early stop" option provided by MMF framework
* Use different loss functions like focal loss to handle difficult examples
* Freeze several front-end parts of the models due to resource constraints

**Fine Tuning:**
* Part of approach focused on fine-tuning selected pre-trained models from model screening part
* Prevent overfitting by using "early stop" option and changing loss functions (e.g., focal loss)
* Use a powerful workstation with NVIDIA GeForce RTX 3090 GPU for experiments
* Each experiment takes approximately 50-150 minutes runtime under early stop setup
* Freeze several front-end parts of the models to save time.


## 3. Experiments and Results

**Experiments and Results:**

- Local testing on development set
- Validation set: dev unseen
- Higher AUROC or accuracy as evaluation metric
- Binary classification task
- Evaluation metric: Area Under the Receiver Operating Characteristic Curve (AUROC)
  - Formula: $$\text{AUROC} = \int_0^1 TPR(x)(1-FPR(x)) dx$$
  - $TPR$: True Positive Rate, $FPR$: False Positive Rate.

### 3.1. Model Screening

**Model Screening Results**

**First Round of Testing**:
- 7 pre-trained models tested
- Learning curves presented as 3 groups in Figure 3
- Early stop function implemented for experiments
- All converged

**Performance Scores**:
- Validation accuracy and AUROC scores listed in Table 1
- ViLBERT and Visual BERT performed best (0.72 AUROC)
- MMBT family second best (0.7 AUROC)
- Unimodal models (image, text) performed worst (0.6 AUROC)

**Unimodal Models Limitations**:
- Unable to incorporate information from the other modal
- Lacking ability to create a cross-modal attention relationship

**MMBT Improvements**:
- Significant improvement over unimodal models
- BERT-like multimodal architectures
- Self-attention over both text and image modalities
- Pre-trained individually, but interact at multiple levels via self-attention

**ViLBERT vs. Visual BERT**:
- ViLBERT: BERT architecture extended to multi-modal two-stream model
  - Performs well on VQA, VCR, and other vision-language tasks
  - Learns semantically meaningful alignment between vision and language
- VisualBERT: Incorporates BERT with pre-trained object proposal systems (e.g., Faster-RCNN)
  - Multiple Transformer layers process text and image inputs
  - Uses visual embeddings to pass object information from image input to multiple transformer layers

**Reasons for Better Performance**:
1. Multimodal pre-training
2. Ability to use multiple transformer layers to closely connect image and text inputs
3. Potential enhancement with larger pretraining dataset or incorporation of related downstream application data

### 3.2. Fine Tuning

**Fine Tuning Phase**

**Implemented Methods**:
- Use Focal loss instead of naive binary cross entropy loss
- Enlarge the train set by adding new labeled samples

**Focal Loss**:
- Balances the ratio between positive and negative samples
- Controlled by hyperparameters α and γ
  - α: controls the weight of positive/negative samples
  - γ: focusing parameter, adjustes training strength on hard-to-classify samples

**Impact of Negative Samples**:
- Positive samples account for about 30% of the dataset, not considered imbalanced
- Focal loss is effective when negative samples are dominant

**Enlarging the Train Set**:
- Collecting labeled memes manually is reliable but time-consuming
- Merging dev seen data into train set, adding 100 samples
- Using keywords to collect additional 1500 images and texts through Google Image, Pinterest, and Huawei Cloud OCR

**Results of Fine Tuning Phase**:
- ViLBERT and Visual BERT performance peak within 1-2 thousand iterations and gradually corrupt afterwards
- Enlarging the train set with dev seen data and additional images improves both models' performance

**Challenges**:
- Overfitting still exists, but slightly delayed compared to initial learning curve
- Pure black background samples may harm model performance


## 4. Conclusion and Future Work

**Conclusion and Future Work**
- Proposed an approach for detecting **hateful memes** in a small multimodal dataset from Facebook
- Set up a common workflow to evaluate the performance of different models
- Concluded that **Visual BERT** and **ViLBERT** are better models for this challenge
- Adjusted fine-tuning strategy, proving **data augmentation** is effective for both Visual BERT and ViLBERT
- Achieved 0.7439 **AUROC** with an accuracy of 0.7037 on the challenge test set

**Future Work**:
- Expand the dataset by:
  - Collecting more samples with multiple characteristics
  - Using automatic or semi-automatic methods to increase the number of data sets several times the original
- Implement **data augmentation techniques**:
  - Color-related operations (e.g., color jitter, inversion, channel swap, deblurring)
  - Shape-related techniques (e.g., rotation, perspective transforming)
  - GAN-based techniques (e.g., SRNet) to replace text on an image while keeping its original style


---

Thank you to arXiv for use of its open access interoperability.