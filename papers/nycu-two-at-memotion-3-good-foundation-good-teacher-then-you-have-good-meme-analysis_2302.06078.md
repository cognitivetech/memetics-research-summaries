# Memotion 3.0 Shared Task Solution using Cooperative Teaching Model (CTM) and Cascaded Emotion Classifier (CEC)

[NYCU-TWO at Memotion 3: Good Foundation, Good Teacher, then you have Good Meme Analysis](https://arxiv.org/abs/2302.06078)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Task Description](#3-task-description)
- [4 Methodologies](#4-methodologies)
- [5 Experiment and Discussion](#5-experiment-and-discussion)
- [6 Conclusions \& Future Work](#6-conclusions--future-work)

## Abstract

**Paper Title:** Memotion 3.0 Shared Task Solution using Cooperative Teaching Model (CTM) and Cascaded Emotion Classifier (CEC)

**Authors:** Yu-Chien Tang, Kuang-Da Wang, Ting-Yun Ou, Wen-Chih Peng

**Affiliation:** National Yang Ming Chiao Tung University, Hsinchu, Taiwan

**Abstract:**
- Robust solution for Memotion 3.0 Shared Task
- Goal: Classify emotion and intensity expressed by memes (images with captions)
- Multi-modal features essential for solving the task
- Use CLIP[1] to extract aligned image-text features
- Propose a novel framework: Cooperative Teaching Model (CTM) for Task A, Cascaded Emotion Classifier (CEC) for Tasks B&C
- CTM based on knowledge distillation for better sentiment prediction in Task A
- CEC leverages emotion intensity suggestion from Task C to classify emotions more precisely in Task B
- Experiments: 2nd place ranking for Task A and B, 4th place ranking for Task C, weighted F1-scores: 0.342 (Task A), 0.784 (Task B), 0.535 (Task C)
- Results demonstrate the robustness and effectiveness of the proposed framework
- Code released at github1

**Keywords:** Emotion classification, meme, multi-modal network, multi-task learning, foundation model

**Footnotes:**
- [1] CLIP: https://arxiv.org/abs/2010.11928 (Accessed November 20, 2022)
- github1: https://github.com/tommytyc/Memotion-DeFactify-AAAI-2023 (Accessed November 20, 2022)


## 1 Introduction

**Meme Definitions:**
- **Definition 1**: An amusing or interesting item (picture, video) that spreads widely online through social media
- **Definition 2**: An idea, behavior, style, or usage that spreads from person to person within a culture

**Understanding Meme Sentiment:**
- Careful analysis of meme content can provide better understanding of post content on social media
- Multi-modal nature makes it challenging to determine emotion and intensity from image content or caption alone
- Downstream tasks such as sentiment analysis can benefit from high-quality multi-modal representation

**CLIP Model:**
- Pre-trained CLIP model used for retrieving rich information from images and text
- Able to align multi-modal features in high-dimensional embedding space

**Sentiment Labels and Scales:**
- Sentiment labels and scales are hierarchical (e.g., humor contains funny, very funny, hilarious)
- Two different models: CTM and CEC, for Task A and Task C respectively

**Task A:**
- Different types of sentiment composed of varying proportions of positive and negative emotions
- Introduce CTM with knowledge distillation framework to achieve better performance on Task A

**Task C:**
- Hierarchical characteristics of emotions considered in model architecture
- Predict emotion intensity for Task C and use it as a suggestion to classify the emotion for Task B
- Leverages prediction from Task C to improve performance on both tasks.


## 2 Related Work

**Memes and Understanding**
- People communicate using memes on social media through images with embedded short texts
- Analyzing sentiment in memes requires extracting features from both text and images
- Multi-modal deep neural networks used for sentiment analysis of memes: multi-task classification networks, multi-modal models [4,5]
- Previous studies adopt fusion techniques to aggregate features from text and images [6,7], but don't address hierarchical sentiment labels

**Vision-Language Pre-training**
- Multi-modal models combining modules from different fields: ConVIRT [8], CLIP [1], CoCa [9]
- ConVIRT uses paired descriptive text to learn medical visual representations
- CLIP has impressive performance on zero-shot transfer model with downstream tasks using image-text pairs data and modification of ConvIRT architecture
- Google research team proposed CoCa: an image-text encoder-decoder foundation model pre-trained with contrastive loss and captioning loss [9]
- CLIP used as multi-modal feature encoder for meme analysis in this challenge

**Knowledge Distillation**
- Technique used in model compression [11,12]
- Extract knowledge from complex model to another simple model for better performance and robustness
- Vanilla setting: teacher-student concept with large deep neural network training a smaller student neural network
- Self-distillation: same architecture for teacher and student models [13]
- Cooperative Teaching Model based on self-distillation provides teacher with additional information for easier learning.


## 3 Task Description

**Memotion 3.0 Dataset**
- **Shared task** at Semeval 2020 (iteration 3)
- Consists of: training dataset, validation dataset, testing dataset (ratio: 5:1:1)
- Each sample includes an image and corresponding captions extracted by OCR system

**Tasks**:
- **Task A: Sentiment Analysis**
  * Given a meme image and caption, classify sentiment into three labels: positive, neutral, negative
  * Label distribution: 25% (17:83) in training set, 42% in validation set, 39% in testing set
- **Task B: Emotion Classification**
  * Given a meme image and caption, identify types of emotion the meme belongs to
  * Emotions: humorous, sarcastic, offensive, motivational
  * Each meme can express more than one emotion
  * Label distribution (in percentage):
    + Humorous: 14% in training set, 86% in validation set, 7% in testing set
    + Sarcastic: 21% in training set, 79% in validation set, 8% in testing set
    + Offensive: 61% in training set, 39% in validation set, 43% in testing set
    + Motivational: 88% in training set, 12% in validation set, 97% in testing set
- **Task C: Scales/Intensity of Emotion Classes**
  * Goal is to quantify the intensity of each emotion
  * Labels: humorous, sarcastic, offensive, motivational
  * Intensity scales from 0 to 3 for humorous, sarcastic, and offensive; 0 and 1 for motivational.


## 4 Methodologies

**Meme Encoder**
* Two types of encoders used: Swin Transformer and CLIP model
* Swin Transformer pre-trained on ImageNet-21k, fine-tuned on Memotion task dataset
* CLIP model has image and text encoders aligned in contrastive manner
* Feature Extraction Pipeline extracts features from meme images and captions using both encoders

**Task A: Cooperative Teaching Model (CTM)**
* Overview: CTM consists of two teacher models and one student model
* Goal: Classify memes into three categories based on sentiment
* Neutral category considered as representing both positive and negative sentiment
* Knowledge distillation used to help student model learn from teachers

**Teacher Model**
* Input includes features of meme images, captions, and additional information for training
* Learns how to classify sentiment (positive or negative) for students to learn from
* Regularized by Gaussian distribution to ensure realistic output probability distribution

**Student Model**
* Goal: Approximate teacher model's output as much as possible
* Trained with Gaussian noise added to meme embeddings for disturbance
* Minimizes standard deviation to increase student confidence in judgment
* Records student predictions during training phase as threshold for determination of negative or positive class during inference

**Loss Function (Task A)**
* Binary cross-entropy loss between teacher model's predictions and corresponding pre-labels
* Kullback–Leibler divergence to regularize teacher models output distribution
* Mean square error between student model's predictions and teacher model's predictions
* Standard deviation of probability distribution from the student model for same meme with different Gaussian noises

**Tasks B & C**
* Combined framework: Fusion layer combines multi-modal information, predicts scales for each emotion class in Task B using MLPs
* Prediction output of Task C used as suggestion for Task B
* Binary cross-entropy loss and softmax cross-entropy loss used to optimize both tasks.


## 5 Experiment and Discussion

**CLIP Model Pre-Training**
- **Pre-trained on:** MET-Meme, Memotion 1.0, Memotion 3.0
- **Memotion 2.0**: Not used as it was not available online
- **CLIP model frozen**: Not fine-tuned in downstream tasks
- **Swin Transformer**: Fine-tuned in downstream tasks for better feature capture
- **Hardware**: Experiments conducted on a machine with an Nvidia GTX 3060 GPU

**Task A: Sentiment Analysis and Emotion Classification**
- **Neutral classification**: Implicit positive or negative sentiment, appears when good student and bad student predictions are both smaller than their thresholds
- **Inference phase**: Add judgmental statement to correctly classify negative sentiment hidden in neutral

**Competition Results**
| Team   | Task A (F1) | Task B (F1) | Task C (F1) |
| ------- | -----------: | ----------: | ----------: |
| NYCU-TWO | **0.342**    | 0.783       | 0.535      |
| CUFE     | 0.337        | **0.743**   | 0.530      |
| Baseline | 0.328        | 0.797       | 0.598      |
| wentaorub | 0.344      | 0.676       | **0.570**   |
| NUAA-QMUL-AIIT | 0.333   | 0.722       | 0.539     |
| CSECU-DSG | 0.332      | 0.747       | 0.522      |

**Ablation Study**
- **CTM Variants**: 1) w/o TR (teacher model), 2) w/o TD (default threshold), 3) simple classifier, 4) w/o C (cascaded architecture)
- **Observations**: All designs contribute to the corresponding tasks; teacher model and student model with learned thresholds need to cooperate for improved performance. Merging three categories into binary pre-label needs to work with teacher model and student model for best results.
- **Language**: Performance can improve if same language used for pre-training, but no appropriate Hinglish dataset found.
- **CEC Variants**: Task-specific networks outperform cascaded emotion classification architecture, but can be a reference for similar tasks.


## 6 Conclusions & Future Work

**Team NYCU\_TWO's Approach to Classifying Emotions from Social Media**

**Multi-modal Feature Extraction**:
- Powerful pipeline integrating CLIP (Contrastive Language-Image Pre-training)

**Framework Overview**:
- Incorporates two models:
  - **Cooperative Teaching Model**: for Task A
  - **Cascaded Emotion Classifier**: for Tasks B&C

**Performance**:
- Competitive results at the end of the challenge, demonstrating effectiveness of framework

**Future Work**:
1. **Low-resource Hinglish problem**:
   - Pretrained language model not trained on Hinglish data as much as English
   - Extracted caption embeddings do not fully reflect rich semantic information (sentiment)
   - Aggregating state-of-the-art methods for low-resource languages may address the issue
2. **Aligning Problem of CLIP Model in Memes**:
   - Unlike common image-text datasets, captions are not supplementary to meme images
   - CLIP model can pull similar semantic meaning images and texts closer, but not in meme pairs
   - Designing a better contrastive learning objective for meme image-text pre-training is an interesting survey topic.

---

Thank you to arXiv for use of its open access interoperability.
