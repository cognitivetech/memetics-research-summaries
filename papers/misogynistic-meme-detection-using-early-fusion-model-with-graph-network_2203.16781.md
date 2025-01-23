# Misogynistic Meme Detection using Early Fusion Model with Graph Network

[Misogynistic Meme Detection using Early Fusion Model with Graph Network](https://arxiv.org/abs/2203.16781)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 System Overview](#3-system-overview)
- [4 Experimental Setup](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Conclusion](#6-conclusion)

## Abstract

**Poirot at SemEval-2022 Task 5: Misogynistic Meme Detection using Early Fusion Model with Graph Network**

**Background:**
- Upsurge in memes as entertainment medium
- Memes have crossed boundary into online harassment against women
- Need to alleviate problem through early fusion model for misogynistic meme prediction and identification (SemEval-2022 Task 5)

**Challenge:**
- Combination of different modalities: image and text
- Model receives meme image with text transcription, target vector

**Approach:**
- Early fusion model for misogynistic meme prediction and identification
- Uses pretrained contextual representations from state-of-the-art transformer-based language models
- Pretrained image representation to get effective image representation

**Results:**
- Competitive results on both SubTask-A and SubTask-B with other competition teams
- Significantly outperforms base lines.


## 1 Introduction

**Understanding Internet Culture: Meme Analysis**

**Introduction:**
- Meme culture in virtual climate shapes pop culture, ideology, and conversational manner of the generation (Shifman, 2013)
- Importance of studying memes to understand internet culture
- High usage of social media among women (78% vs. 65% men)
- New opportunities for women online vs. replication of offline discrimination through offensive content

**Impact of Memes:**
- Originally intended for humor and irony
- Misuse as form of hatred towards women
- Sexist and offensive messages in online environment
- Profound effect on mental health, potential harmful effects on cognitive and emotional processes leading to mental illnesses (Paciello et al., 2021)

**Team Poirot's Solution:**
- Description of SemEval - 2022 Task 5 competition solution
- Focus on Multi-Modal-Multi-Task module using features from both images and text

**Ablation Studies:**
- Different modalities: importance, relative importance, training parameters
- Impact on misogynistic identification of memes

**Conclusion:**
- Changing module parameters affects predictions on misogynistic identification of memes.


## 2 Background

**Background**
- **Sub-Task A**: Identify misogynous memes as either misogynous or not
- **Sub-Task B**: Recognize type of misogyny (stereotype, shaming, objectification, violence) in potential overlapping categories
- Task difficulty increases from Sub-Task A to Sub-Task B due to identifying the type of misogyny
- Datasets provided by task organizers: memes collected from web and manually annotated via crowdsourcing platforms
- Each sample includes image and text transcription (if applicable)
- Statistical information about datasets in Table 1

**Dataset Information**
- Memes collected from the web and manually annotated via crowdsourcing platforms
- Each sample supported by an image and corresponding text transcription
- Imbalance in number of samples per label affects performance, particularly for multilabel prediction
- Training dataset information provided in Table 1

**Evaluation Criteria**
- Performance evaluated using:
  - Macro F1 score for Sub-Task A
  - Weighted F1 score for each subtask (misogynous, shaming, stereotype, objectification, violence) in Sub-Task B
  - Average F1 score of subtasks used to rank systems


## 3 System Overview

**System Overview**
- Solution system comprises two separate systems for sub-tasks
- Approach: binary (multimodal information) and multi-label

**Binary Model**
- Two modalities: image and text
- Initial stage divided into parallel streams, later joined together
- Pretrained Representation Module (ResNet-101/50) for image features extraction
  - Outputs deep feature map for each region
- Navigator Module from NTS-net decouples image into several parts and extracts meaningful regions
- Textual Stream uses SentenceBERT model for text features extraction
- Feature Extraction Module outputs a feature vector (E+D dimensions)
- Linear layer to output logits, passed on to a function to generate predictions

**Multi-Label Model**
- Same as binary model's feature extraction pipeline
- Graph Classification Module replaces final output method
  - Uses Graph Neural Networks to learn label representation and interdependencies
- Adjacency matrix created based on co-occurrence patterns in training and trial datasets
- Custom loss function with class weights to penalize imbalance in data.


## 4 Experimental Setup

**Experimental Setup**

**Baselines**:
- Provided by task organizers
- Depend on Sub-Task and use different feature sets:
  - **Sub-Task A: Misogynous Meme Identification**
    - Feature Extraction Module:
      - Text Transcription: "why is women's track and field more popular than women's weightlifting? no particular reason…"
      - Graph Classification Module:
        - **Classifiers**: Multi-Label Loss
        - Architecture:
          - Uses image features and text features from Feature Extraction, pretrained ResNet and Sentence Transformer SBert
          - Features passed through 5-layer classifier stack generated from Graph Classification Module
        - Baselines:
          - **Baseline-Text**: deep representation of text (fine-tuned sentence embedding using USE pre-trained model)
          - **Baseline-Image**: deep representation of image content (fine-tuned image classification model based on VGG-16)
          - **Baseline-IT**: concatenation of deep image and text representations (single layer neural network)
  - **Sub-Task B: Type of Misogynous Meme Identification**
    - Baselines:
      - **Baseline-Flat**: multi-label model based on concatenation of deep image and text representations for predicting if a meme is misogynous and its type
      - **Baseline-Hierarchical**: hierarchical multi-label model based on text representations for predicting if a meme is misogynous or not, and if so, its type

**Hyperparameters and Implementation Details**:
- Apply basic text pre-processing to all sentences: normalize white-space characters to spaces
- Resize images to [224,224] for uniformity and perform random crops and flips before feeding to network
- Use a 2-layer graph network for best performance
- For node features, use 300-Dimensional GloVe embeddings trained on Wikipedia Dataset


## 5 Results

**Binary vs Multi-Label Classification Results**

**Comparison of Macro and Weighted Scores**:
- Table 5 and 6 compare the macro and weighted scores for best performing models on binary classiﬁcation task and multi-label task

**Hyperparameters Used**:
- Optimizer: AdamW
- Pre-trained BERT LR: 2e-4
- Navigator Network LR: 1e-3
- Graph Learning Rate: 1e-2
- Graph Layers:
    - Layer 1 Dim: 512
    - Layer 2 Dim: 2048
    - Concatenation Parameter: 0.7

**Binary Classification Results**:
- Subtask-A:
    - ResNet-101 imagenet: 0.1 (fmacro), 0.601 (fwighted)
    - ResNet-50 nsfw: 0.2 (fmacro), 0.590 (fwighted)
    - Baseline-Text, Image, IT: 0.640, 0.639, 0.543
    - Our models outperformed baselines
- Subtask-B:
    - ResNet-101 imagenet: +SM Loss 0.641 (fwighted)
    - ResNet-50 nsfw: +SM Loss 0.632 (fwighted)
    - Baseline-Flat, Heirarchical: 0.421, 0.621
    - Our models using graph network and navigator outperformed baselines
    - ResNet-50 nsfw had poorer performance than ResNet-101 imagenet

**Multi-Label Classification Results**:
- Subtask-B:
    - Graph Depth (fwighted): ResNet-101 imagenet 2-layer: 0.644, 3-layer: 0.644, 4-layer: 0.632, 5-layer: 0.628
    - ResNet-50 nsfw: 2-layer: 0.641, 3-layer: 0.643, 4-layer: 0.629, 5-layer: 0.621
    - Increasing graph convolution layers led to performance drop due to over-smoothing

**Ablation Studies**:
- Effects of threshold values (0.1 to 0.9 in steps of 0.1):
    - Textual stream information is more important than visual stream for both classiﬁcation problems
- Effects of graph classification module depth:
    - Increasing number of layers led to performance drop due to over-smoothing
- Effects of custom loss function:
    - Custom Loss outperformed MultiLabel SoftMargin Loss (SM Loss) in experimental runs


## 6 Conclusion

**Conclusion**
- Description of systems developed for Multimedia Automatic Misogyny Identification challenge at Semeval 2022
- **SubTask-A**: framed as binary classification task, used two separate streams of information to identify misogyny
- **SubTask-B**: tried to find semantic relation between type of misogyny and their relative importance for multi-label classification
- Use of powerful, state-of-the-art pretrained models for text and images resulted in high F1 scores
- Best performing model ranked 7th out of 83 participants on SubTask-A, 38th on SubTask-B

**Future Work**
- Explore alternate approaches to model multi-label dependencies using **Knowledge-Graph** and **GAT Networks**
- Resolve oversmoothing issue when increasing depth of Graph Classification Module using effective **Normalization layers**.


---

Thank you to arXiv for use of its open access interoperability.