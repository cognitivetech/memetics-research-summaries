# AOMD: An Analogy-aware Approach to Offensive Meme Detection on Social Media

[AOMD: An Analogy-aware Approach to Offensive Meme Detection on Social Media](https://arxiv.org/abs/2106.11229)

## Table of Contents
- [Abstract](#abstract)
- [1. Introduction](#1-introduction)
- [2. Related Work](#2-related-work)
- [3. Problem De](#3-problem-de)
- [4. Solution](#4-solution)
	- [4.1. Analogy-aware Multi-modal Representation Learning Module](#41-analogy-aware-multi-modal-representation-learning-module)
	- [4.2. Attentive Multi-modal Analogy Alignment Module](#42-attentive-multi-modal-analogy-alignment-module)
	- [4.3. Supervised Learning Module](#43-supervised-learning-module)
- [5. Data](#5-data)
- [6. Evaluation](#6-evaluation)
- [7. Conclusion](#7-conclusion)

## Abstract

**Analogy-aware Approach to Offensive Meme Detection (AOMD)**

**Abstract**:
- Focuses on detecting offensive analogy memes on online social media
- Existing solutions often ignore the relation between visual and textual contents, insufficient for identifying offensive analogy memes
- Two challenges: 
    - Capturing implicit analogy conveyed by a meme
    - Aligning complex analogy across different data modalities in a meme
- Develop a deep learning based **Analogy-aware Offensive Meme Detection (AOMD)** framework to learn implicit analogy from multi-modal contents and effectively detect offensive analogy memes
- Evaluated on two real-world datasets, shows significant performance gains compared to state-of-the-art baselines

**Keywords**:
- Offensive Meme
- Analogy-aware
- Multi-modal Learning


## 1. Introduction

**Social Media and Online Harassment**
- **Prevalence of online harassment**: Approximately 44% of Americans were subjected to online hate and harassment in 2020, and 28% of online content contained severe purposeful harassment (e.g., sexual harassment, stalking, physical threats)
- **Importance of addressing online harassment**: Necessary to curb the spread of offensive information and reduce the propagation of extreme ideology on social media

**Detecting Offensive Analogy Memes on Social Media**
- **Challenges**:
  - **Analogy awareness**: Correctly capturing and understanding the analogy expressed by the meme, which may require a holistic analysis of the visual content, embedded caption, user comments, and contextual information
  - **Complex multi-modal analogy alignment**: Accurately aligning the analogy across different data modalities in a meme post (e.g., visual and textual content)
- **Existing solutions**: Limited as they only focus on direct combinations of multi-modal features from the visual content and embedded captions, ignoring the implicit relation between the visual and textual contents and the analogy they deliver together

**Proposed Approach: Analogy-Aware Obfensive Meme Detection (AOMD)**
- Developed to address the challenges of **analogy awareness** and **complex multi-modal analogy alignment** in detecting offensive analogy memes on social media
- Includes:
  - **Analogy-aware multi-modal representation learning module**: Incorporates content (image, embedded caption) and contextual information (text description, user comments) to identify the analogy expressed in the meme
  - **Attentive multi-modal analogy alignment module**: Explicitly models the relation between the visual content and textual caption in the memes


## 2. Related Work

**Related Work**

**Social Media Misbehavior**:
- Cyberbullying
- Trolling
- Hateful content
- Rumors
- Fake news
- Timely detection of cyberbullying events [18]
- Machine learning based scheme to detect troll posts [19]
- Multi-level classifier for discrimination on social media [20]
- Multi-task learning scheme to identify rumors [21]
- Deep learning framework to detect fake news [22]

**Hate Speech Detection**:
- Waseem et al. proposed critical racial theory based hate speech detection [25]
- Utilization of memes to spread offensive content observed in 2016 U.S. presidential election [5]
- Deep learning framework to detect hate speech in memes by fusing visual and linguistic contents [4]
- Multi-task learning framework to classify memes on multiple tasks [7]
- Ensemble learning approach to boost performance of identifying hateful memes [8]

**Multi-Modal Learning**:
- Attracting attention due to potential for informative features from various data types [26]
- Applications: multi-modal machine translation, visual question answering, image-text matching, video description generation [27, 28, 29, 30]
- Multi-modal machine translation with visual information [31]
- Deep representation learning to infer answers to visual questions [32]
- Semantic reasoning network for visual representation and alignment with text captions [33]
- Attention-based multi-modal fusion framework to generate video descriptions [34]

**Key Differences**:
- None of the existing solutions are dedicated to identifying and aligning analogy across data modalities in offensive memes.
- This paper proposes a co-attentive multi-modal analogy alignment scheme to extract and align analogical features from memes to identify offensive analogy memes.


## 3. Problem De
nition

**Meme Post Definition**
- Contains three major components: **meme (Mi)**, **text description (Di)**, and **user comments (Ui)**
- Example in Figure 2

**Meme Definition**
- Image attachment of a meme post
- Consists of two parts:
  - **Visual content (MVni)**
  - **Embedded caption (MCni)**

**Visual Content Definition**
- Imagery content in the meme that depicts visual perceptions

**Embedded Caption Definition**
- Text superimposed or naturally contained in the meme

**Text Description Definition**
- Optional text description of the meme post (marked as empty string if not available)

**User Comments Definition**
- Set of user comments associated with the post

**Offensiveness Definition**
- Meme post is considered offensive (asyi= 1) if:
  - Visual content and/or embedded caption convey offensive or prejudicial information
  - Text description available
- Otherwise, considered non-offensive (asyi= 0)

**Objective**: Investigate analogy embedded in the meme and identify its offensiveness given:
- **Meme content (Mi)**
- **Text description (Di)**
- **User comments (Ui)**

Formal notation:
- P = {P1, ..., Pn} is a set of N meme posts on social media
- Each Pifor 1≤i≤N is defined as Pi = (Mi; Di; Ui; yi)
- The goal is to find:
  - arg max⁵ yi  ℰPr(yi  = yijPi) for all Pi2P, where:
    - yi: ground truth label of the meme's offensiveness
    - ^yi: estimated label of the meme's offensiveness


## 4. Solution

**AOMD Framework for Offensive Analogy Meme Detection**

* Three components:
  1. **Analogy-aware Multi-modal Representation Learning**: Extracts visual, textual, and contextual features from meme posts.
  2. **Attentive Multi-Modal Analogy Alignment**: Captures the analogical relation between multi-modal content in the meme.
  3. **Supervised Learning Module**: Identifies offensive analogy memes using a supervised approach.


### 4.1. Analogy-aware Multi-modal Representation Learning Module

**Multi-modal Representation Learning Module**

**Overview**:
- Extract key features from each element of a meme post
- Learn the representation of each element across different data modalities

**Visual Content Extraction**:
- Focus on local object-level and global image-level information
- Use advanced Faster R-CNN model to extract local visual objects and their positions
- Extract global image-level visual feature using a pre-trained convolutional neural network (ResNet50)

**Embedded Caption Extraction**:
- Use optical character recognition (OCR) tool to extract word tokens from meme
- Record position of each word token's bounding box
- Use clustering algorithm to capture word-to-phrase association in embedded captions
- Learn fixed-length vector representation of each word token cluster using LSTM word sequence encoder

**Contextual Information Extraction**:
- Focus on text description and user comments
- Adopt same LSTM encoder as caption extraction to extract linguistic features from text description and user comments


### 4.2. Attentive Multi-modal Analogy Alignment Module

**Attentive Multi-modal Analogy Alignment Module (AMAM)**

**Multi-Modal Features Extraction**:
- Visual content features extracted using pre-trained models like object detection
- Embedded captions processed using language models like BERT
- Contextual information considered for understanding meme context

**Challenges in Multi-Modal Learning**:
- Previous methods rely on uni-modal data pre-training (e.g., images, text)
- Ignore analogical relation between visual and textual content
- Difficulty detecting offensive analogy memes

**AMAM Overview**:
- Develops an **analogy-aware attention mechanism** to effectively integrate information from different components in the meme posts
- Goal: learn useful features from visual objects and word token clusters that identify the analogy of offensive memes

**AMAM Architecture**:
1. Concatenate vector representations of visual objects and word token clusters with normalized bounding box positions (Equation 8)
2. Compute pairwise affinity matrix E using tanh function, C|V, and weight parameters W (Equation 9)
3. Perform co-attention to compute attention maps Mv and Mc for visual objects and word token clusters, respectively (Equations 10 & 11)
4. Calculate attention weights ív and íc using softmax function (Equation 11)
5. Compute attended feature representations Fv and Fc using the attention weights (Equation 12)
6. Integrate attended feature vectors Fv, Fc with other learned feature representations (Fg), contextual information (Fd, Fu) for supervised learning

**Goal**: Detect offensive analogy memes using attentively extracted features from visual content, embedded captions, and contextual information.


### 4.3. Supervised Learning Module

**AOMD Framework Overview**

**Components:**
- Two-layer feed-forward neural network (MLP)
- Softmax output layer
- Input: learned features [Fv, Fi, Fg, Fd, Fu] from previous sections

**Objective:**
- Binary classification of memes as offensive or non-offensive

**Loss Function:**
- Cross-entropy loss (Equation 14)
- Minimize the difference between ground truth y and predicted probability ^y

**Training Phase:**
1. Input: meme post set P
2. Output: ^y
3. Initialize: F = {Fv, Fi, Fg, Fd, Fu}
4. For each Pi in P do:
   - Initialize Tc[i], Fvi, Tw[i], Fw[i], Fd[i]; Fu[i]
5. For each Tw[i] in Tw[i]:
   - Assign to Tc[i] instead of Si (Equation 13)
6. Extract Ci from Tc[i]
7. Compute [Fv, Fi, Fg, Fd, Fu] = F
8. End for
9. Learn by optimizing L() (Equation 14) using AdamW optimizer

**Classification Phase:**
1. Input: meme post set P
2. Output: ^y
3. Initialize: ^y = []
4. For each Pi in P do:
   - Apply neural network model (Equation 13) to predict yi
   - Assign predicted probability to ^y[i]
5. End for
6. Output: ^y


## 5. Data

**Data Collection for Offensive Memes**

**Observations**:
- Mainstream social media platforms (e.g., Twitter) contain a massive amount of memes, but collection of offensive memes has experienced a "long tail issue" - only a small portion of collected memes are actually offensive
- Existing datasets for offensive memes (e.g., MultiOFF, SemEval-2020) lack text descriptions and user comments which are essential for detecting offensive memes

**Data Collection Process**:
- Collected own datasets for comprehensive evaluation of the proposed AOMD scheme
- Data sources: 
  - **Memes**, memes, and more Memes" group on Gab
  - r/NewOffenativeMemes subforum on Reddit
- For each meme post, collected:
  - Meme content
  - Text description
  - User comments
- Invited three independent annotators to label the offensiveness of each meme based on the embedded analogy
- Ground-truth labels decided by majority vote of annotators
- Interannotator agreement (Fleiss Kappa score): Gab - 0.47, Reddit - 0.51

**Dataset Summary**:
- Datasets are not balanced (non-offensive memes more common than offensive ones)
- 63.2% and 99.5% of meme posts in the Gab and Reddit datasets contain contextual information, respectively

| **Gab Dataset** | **Reddit Dataset** |
| --- | --- |
| Total Number of Collected Meme Posts: 1,965 | Total Number of Collected Meme Posts: 1,094 |
| Number of Offensive Meme Posts: 672 (34.2%) | Number of Offensive Meme Posts: 380 (34.7%) |
| Number of Meme Posts Containing Analogy: 891 (45.3%) | Number of Meme Posts Containing Analogy: 522 (47.7%) |
| Number of Meme Posts Containing Contextual Information: 1,242 (63.2%) | Number of Meme Posts Containing Contextual Information: 1,089 (99.5%) |


## 6. Evaluation

**Evaluation of AOMD Framework**

**Comparison with Baselines:**
- **WSCNet**: Convolutional neural network based scheme for sentiment analysis of visual content [46]
  * Input: Meme image
  * Output: Detection of offensive analogy meme
- **HateSpeech**: Lexicon-based approach for hate speech detection on social media [47]
  * Input: Embedded caption of each meme post
  * Output: Detection of offensive analogy meme
- **MultiOFF**: Transfer learning based approach using pre-trained visual and linguistic features [5]
  * Input: Same as AOMD but excludes contextual information
- **HatePixel**: Multi-layer perceptron classifier for hate speech detection in images [4]
  * Input: Same as AOMD but excludes contextual information
- **HatefulMeme**: Multi-modal hateful meme detection framework using Visual BERT [10]
  * Input: Same as AOMD but excludes contextual information

**Evaluation Setting:**
- Use of 70%, 10%, and 20% of dataset for training, validation, and testing respectively
- Learning rate = 0.001, 1e-8 for optimizer AdamW [43]
- Batch size set to 32
- Follow network architectures presented in papers and carefully tune hyperparameters

**Evaluation Metrics:**
- **Accuracy**: Percentage of correct classifications
- **F1 Score**: Harmonic mean of precision and recall
- **Cohan's Kappa Coefficient (Kappa)**: Measures agreement beyond chance

**Results:**
- AOMD outperforms all baseline methods on both Gab and Reddit datasets for all evaluation metrics
- Significant performance gains attributed to accurate identification of analogy features from multi-modal contents and effective alignment across modalities

**Analysis of Baselines:**
- WSCNet: Ignores text embedded in meme, not robust in detecting offensive analogy memes
- HateSpeech: Focuses on textual content only, ignores semantic meanings of visual objects
- Multimodal baselines (MultiOFF, HatePixel, HatefulMeme): Fusing pre-trained features but do not capture implicit analogical relations between modalities

**ROC Curves:**
- AOMD continues to outperform all baseline methods in terms of detection performance for all classifications thresholds.

## 7. Conclusion

**AOMD: Analogy-aware Deep Learning for Offensive Analogy Memes Detection**

1. **Introduction** - Developing AOMD to capture analogy in memes and detect hidden offensiveness.
2. **Framework** - Effectively processing multiple data modalities.
3. **Evaluation** - ROC curves comparison on Gab and Reddit datasets.
4. **Results** - AOMD outperforms state-of-the-art baselines in identifying offensive analogy memes.
