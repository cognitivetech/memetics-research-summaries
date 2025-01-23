# DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis

[DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis](https://arxiv.org/abs/2008.00825)

## Table of Contents
- [DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis](#dsc-iit-ism-at-semeval-2020-task-8-bi-fusion-techniques-for-deep-meme-emotion-analysis)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Data](#3-data)
- [4 Methodology](#4-methodology)
- [5 Experiments](#5-experiments)
- [6 Discussion](#6-discussion)
- [7 Conclusion](#7-conclusion)

## DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis

**IIT-ISM at SemEval-2020: Memetic Emotion Analysis with Bi-Fusion Techniques**

- Memes analysis for sentiment and humor classification (SemEval-2020)
- Proposed system: utilizes bimodal fusion techniques
  - Leverages inter-modal dependencies
- Sentiment Classification (Task A): macro F1 score: **0.357**
- Humor Classification (Task B): macro F1 score: **0.510**
- Scales of Semantic Classes (Task C): macro F1 score: **0.312**


## 1 Introduction

**Internet Memes:**
- Increasingly abundant in multimedia content online
- Derived from news, TV shows, movies, capable of conveying ideas easily understood by masses
- Shared in various online communities and not limited to one language
- Can convey sentiment and humor as well as controversial, hateful ideologies

**SemEval 2020 Challenge:**
- Aims to study sentiment and humor in memes
- Three tasks:
  1. **Task A**: Classify the sentiment of an internet meme (positive, negative, neutral)
  2. **Task B**: Multilabel classification of a meme into four categories (sarcastic, humorous, offensive, motivational)
  3. **Task C**: Quantify extent of sarcasm, humor, and offense expressed in a meme on a scale of 0-3

**Approach:**
- Combination of state-of-the-art model architectures for processing multimodal memes through transfer learning and training from scratch
- Explore various modality fusion techniques and inter-task dependency
- Investigate model performances from relative and absolute perspectives, explore possible improvements
- Make code publicly available

**License:**
- This work is licensed under a Creative Commons Attribution 4.0 International License
- License details: http://creativecommons.org/licenses/by/4.0/


## 2 Related Work

**Meme Research: Sentiments and Analysis**

**Background:**
- New area of research on emotions in memes
- Increasing interest due to social media explosion and deep learning techniques
- Pioneering work by Vyalla & Udandarao (2020), Wang & Wen (2015)
- Scarce studies exclusively analyzing meme emotion

**Deep Learning Techniques:**
- Significantly outperform traditional methods in sentiment analysis tasks
- Textual segments: Zhang et al. (2018)
- Images and videos: Poria et al. (2017), Borth et al. (2013), You et al. (2017), Sinha et al. (2019)

**Multimodal Methods:**
- Combining textual and visual information
- Improved performance: Guillaumin et al. (2010), Zahavy et al. (2016)
- Hierarchical methods: Majumder et al. (2018), Hu et al. (2018)
- Attention-based methods: Huang et al. (2019), Moon et al. (2018)
- Previous iterations of SemEval

**Multitask Learning:**
- Akhtar et al. (2019): Emotion recognition and sentiment analysis

**Meme-Specific Research:**
- French (2017): Correlation between image-based memes and textual content
- Prajwal et al. (2019): Models to generate rich face emotion captions from memes.


## 3 Data

**Dataset Description**
- Consists of approximately 7K meme images with extracted text
- Each sample has a **sentiment annotation**: Negative (0), Neutral (1), or Positive (2)
- Another 3 semantic classes: Humor, Sarcasm, and Offence
  - Labeled as Not (0), Slightly (1), Mildly (2), or Very (3) for fine-grained labels
  - Binary column denoting whether a meme is **motivational**
- Around 2K samples form the test set
- Dataset split into **train and validation sets**: 6K and 1K samples, respectively

**Dataset Label Distributions**

| Label          | Train Set | Validation Set |
|------------------|-----------|---------------|
| Sentiment       | 519        | 1894         |
| Humor          | 1400       | 2060         |
| Sarcasm        | 1304       | 2983         |
| Offence        | 2289       | 2203         |
| Motivation     | 3844       | 2099         |


## 4 Methodology

**Meme Analysis Approaches**

**Three Main Approaches:**
- **Textual**: based on the text part of the meme
- **Visual**: based on the image of the meme
- **Combined or Fused**: unifying the textual and visual inputs in a single end-to-end model

**Textual Features:**
- BiLSTM: Long Short-Term Memory (LSTM) neural network architecture
  * Processes text in forward and backward direction for better context understanding
- RoBERTa: Bidirectional Encoder Representations from Transformers
  * Revolutionary language model based on self-supervised pretraining
  * Generalizes extremely well to downstream tasks

**Visual Features:**
- AlexNet: Convolutional Neural Network (CNN) architecture
  * Widely known and uses rectified linear unit as activation function
- ResNet: Residual Networks
  * Classic neural network used for computer vision tasks
  * Skip connections help mitigate the vanishing gradient problem

**Facial Expressions:**
- Some meme images contain faces with useful emotional information
- Attempted using pretrained ResNet block to generate predictions, but poor performance on validation set

**Multimodal Approach:**
- Process both modalities individually and then combine them for a complete representation of the meme
  - **Early Fusion**: concatenate textual and visual feature vectors before passing through softmax classifier
  - **GMU (Gated Multimodal Unit)**: learns an intermediate representation based on a combination of data from different modalities using multiplicative gates
  - **Late Fusion**: combine models at inference time by using their individual softmax prediction scores and assigning equal weights

**Multitask Learning:**
- Train separate models for each subtask, requiring 8 models in total
- Multitask learning enables training a model with multiple outputs for multiple related tasks simultaneously
- Shares hidden layers among tasks and keeps some individual layers for each output to improve generalization performance.


## 5 Experiments

**Model Training Details for Submissions**

**Training Parameters**:
- Models trained separately for Task A and subtasks of Task B & C
- Keras with TensorFlow backend on Google Colab GPU
- Use default Adam optimizer, Cross Entropy loss, and train till validation loss stops improving
- Batch size of 32

**BiLSTM Model**:
- Preprocessing: Remove punctuation, symbols, convert to lowercase, tokenize with truncated length of 64
- Input layer with embedding size 32, bidirectional LSTM layer, softmax dense layer
- Keep number of LSTM units at 32, apply dropout of 0.5 between layers
- Use appropriate class weights for loss during training

**RoBERTa Model**:
- Pretrained RoBERTa-Base model
- Input sequence length equal to longest text (199)
- Apply oversampling to make target class ratio 1 to handle class imbalance
- Fine-tune pretrained model on the dataset, using output of CLS token and a softmax layer

**AlexNet Model**:
- Resize images to 224x224 with 3 channels as input
- Convolutional layers with filter sizes [96, 128, 128, 256, 256]
- Flatten and apply 2 dense layers of size 1024 before the softmax layer
- Apply dropout of 0.4 after each layer, use class weights to handle imbalance

**ResNet Model**:
- Resize images to 256x256, retain RGB channels
- Use pretrained ImageNet weights as initialization
- Outputs followed by dense layers of sizes [768, 256] and a softmax layer
- Learning rate of 3e-4

**BiLSTM+AlexNet Model**:
- Replace softmax layer in BiLSTM and AlexNet models with a dense layer of size 64
- Concatenate outputs and pass through another dense layer of size 128 before the softmax prediction layer
- Employ class weight balancing

**RoBERTa+ResNet Model**:
- Explore three ways of information fusion: Early Fusion, GMU, Late Fusion
- For Early Fusion and GMU, use SGD optimizer and oversampling to prevent gradient vanishing and bias
- For Late Fusion, average prediction probabilities from separately trained models

**Multitask Learning (MTL) Model**:
- Use BiLSTM+AlexNet architecture with slight modifications
- Train 2 models: one for Task A with Task B, another for Task A with Task C
- Add another bidirectional LSTM layer and double the vector size for each modality to 128
- Increase joint vector size to 256, followed by 128 unit dense layers and individual softmax layers


## 6 Discussion

**Analysis of Memes Dataset and Models**

**Observations**:
- Detailed analysis of why state-of-the-art pretrained models did not perform superiorly
- Discussion on potential areas for improvement

**TF-IDF Model**:
- Used with classical machine learning classifiers like logistic regression
- Performed better than deep learning models in some cases

**Text Models**:
- **Unconventional aspects of memes**: Text scattered around images, leading to jumbled phrases due to OCR
- **BiLSTM model**: Performance not improved by pretrained GloVe embeddings
- Reason: Difference in vocabulary usage and intentional misspellings in memes

**Image Models**:
- Pretrained deep models (Inception, ResNet) did not outperform the baseline model
- **Reason**: Very little similarity between ImageNet dataset and meme images
- **Suggestion**: Use image masking techniques as a preprocessing step to replace text with background

**Overall Performance**:
- Winning macro-averaged F1 scores less than 0.36, 0.52, and 0.33 for Task A, B, C respectively
- Ample room for improvement

**Fusion Strategies**:
- Simple concatenation (Early Fusion) turned out to be the best
- Need for a better fusion strategy or learning technique to generate unified and coherent representation

**Future Work**:
- Inter-modal correspondences between language and visual data in image captioning.


## 7 Conclusion

**Meme Sentiment and Humor Analysis with Deep Learning**

1. Analyzing challenges in understanding memes using deep learning
2. Comparing performance: large pretrained models vs. simple models from scratch
3. Results: Unconventional modalities (sentiment + humor) reduce effectiveness of domain adaptation/transfer learning
4. Future work: Improving models: new techniques and approaches.


---

Thank you to arXiv for use of its open access interoperability.