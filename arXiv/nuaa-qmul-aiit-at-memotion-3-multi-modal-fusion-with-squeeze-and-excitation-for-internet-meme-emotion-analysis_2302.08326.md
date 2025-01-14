# NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis

[NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis](https://arxiv.org/abs/2302.08326)

## Table of Contents
- [NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis](#nuaa-qmul-aiit-at-memotion-3-multi-modal-fusion-with-squeeze-and-excitation-for-internet-meme-emotion-analysis)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 System Overview](#3-system-overview)
- [4 Experimental Setup](#4-experimental-setup)
- [5. Results](#5-results)
- [6 Conclusion](#6-conclusion)

## NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis

**NUAA-QMUL-AIIT Team at Memotion 3 Shared Task**

**Participation**:
- Description of participation in the Memotion 3 shared task on meme emotion analysis

**Proposed Method: Squeeze-and-Excitation Fusion (SEFusion)**
- Novel multi-modal fusion method proposed for emotion classification in memes
- Simple fusion method using fully connected layers, reshaping, and matrix multiplication
- Learns a weight for each modality and applies it to its own modality feature

**Performance**:
- Ranked first on Task A
- Ranked fifth on Task B
- Ranked second on Task C

**SEFusion Features**:
- Flexibility to fuse any features from different modalities

**Resources**:
- Source code published on GitHub: https://github.com/xxxxxxxxy/memotion3-SEFusion

**Keywords**:
- Multi-modal fusion
- Internet meme
- Emotion analysis
- Squeeze-and-Excitation


## 1 Introduction

**Internet Meme Analysis:**
* Automated processing helps filter online information overload
* Internet memes: concise, humorous means of sharing info via images and text
* Prevalent on social media platforms
* Combines image and text modalities for communication
* Limited research on meme analysis, focusing mainly on text
* Challenges in effective combination of text and image features
* Existing fusion methods use attention mechanisms to map modalities (text and image) [1]
* Determining weight variation for each modality essential
* Multiplication and aggregation of weights with associated embeddings
* Hu et al.'s approach: squeeze-and-excitation block for learning channel dependencies in images
* Proposed method, Squeeze-and-Excitation Fusion (SEFusion), combines text features and image features extracted from internet memes.

**Background:**
* Memotion 3 shared task description and prior work on emotion classification in memes not covered in this summary.

**Proposed Method: SEFusion**
* Novel multi-modal fusion method proposed for internet meme analysis
* Utilizes squeeze-and-excitation block to learn modal dependencies of multimodal data [2]
* Cannot be applied directly to fuse features of different modalities, hence adopted for adaptation [3]

**Results:**
* Top rank in Task A of Memotion 3 shared task with F1 score: 0.3441
* Second place on Task C.


## 2 Background

**Memotion 3 Shared Task**
- Third edition of Memotion series focused on meme emotion analysis [7]
- Consists of three subtasks:
  1. **Task A**: Classify internet meme based on expressed emotion (positive, negative, neutral)
  2. **Task B**: Identify type of emotion in internet memes (sarcastic, humorous, offensive, motivational) as multi-label classification task
  3. **Task C**: Quantify scales of each type identified in Task B

**Related Work on Meme Emotion Analysis**
- Mainly focuses on emotion classification and detecting hateful memes [10]
- Text meme analysis:
  - Wu et al. [11]: Add slang and sentiment lexica for improvement
  - Amalia et al. [12]: Use OCR Tesseract to extract text, then Naive Bayes classifier for emotion detection (75% accuracy)
- Humorous text meme recognition:
  - Costa et al. [13]: Use Maximum Entropy classifier (high performance for negative class, lower for positive)
- Hateful meme detection:
  - Sabat et al. [14]: Use BERT and VGG-16 for processing texts and images, apply early and late fusion methods
  - Nayak and Agrawal [15]: Employ machine learning models for hate detection
  - Ouaari et al. [16]: Utilize neural networks to extract features, train sentiment classifier
  - Fersini et al. [17]: Detect misogynous memes using unimodal and multimodal approaches

**Meme Emotion Analysis Research Summary**:
- Traditional machine learning, contemporary deep learning models, and feature fusion methods used [10]
- No existing research combining features of different modalities automatically [17]


## 3 System Overview

**System Overview**

**Breaking Down the Task into Subtasks**:
- Shared task consists of 3 subtasks:
    - **A**: Classify a meme as positive, negative, or neutral
    - **B1-4**: Classify a meme as humorous/not, sarcastic/not, offensive/not, motivational/not, and quantify its funniness, sarcasm level, offensiveness, and motivation level
    - **C1-4**: Same as B1-4, but with different models
- Observed no difference between B4 and C4, so reduced to 8 subtasks

**Feature Extraction**:
- **Text Features**: Use TweetEval pre-trained model to extract features, average them
- **Image Features**: Use CLIP-ViT pre-trained model to extract features, perform L2 normalization

**SEFusion Fusion**:
- Squeeze: Perform dimension reduction on text and image features, concatenate into 𝑧
- Excitation: Apply gating mechanism with sigmoid activation to capture modal dependencies
- Final fusion: Multiply s with the reshaped X' to obtain the fused features

**Classification**:
- Use fully connected layers with sigmoid/softmax activation to generate class probabilities


## 4 Experimental Setup

**Dataset**
- Used for experiments: Memotion 3 task dataset [22]
- Contains: image, text, and label fields
- Total samples: 10,000 (7,000 training, 1,500 validation, 1,500 testing)

**Distribution of Labels**
- **Positive**: 2,275 (33%) in train, 341 (23%) in validation, 586 (39%) in test (total: 3,202 or 32%)
- **Neutral**: 2,970 (42%) in train, 579 (39%) in validation, 533 (36%) in test (total: 4,082 or 40%)
- **Negative**: 1,755 (25%) in train, 580 (39%) in validation, 381 (25%) in test (total: 2,716 or 27%)
- **Sum**: 7,000 train, 1,500 validation, 1,500 test (total: 10,000)

**Task A Label Distribution**
| Humor (task B1) | Sarcastic (task B2) |
|---|---|
| 5,990 (86%) in train, 1,401 (93%) in validation, 1,389 (93%) in test (total: 5,524 or 79%) | 1,010 (14%) in train, 99 (7%) in validation, 111 (7%) in test (total: 1,476 or 12%) |
| **Not**: 1,010 (14%) in train, 99 (7%) in validation, 111 (7%) in test (total: 1,476 or 21%) | **Slightly**: 3,393 (48%) in train, 973 (65%) in validation, 928 (62%) in test (total: 1,953 or 65%) |
| **Mildly**: 2,038 (29%) in train, 375 (25%) in validation, 406 (27%) in test (total: 3,021 or 43%) | **Moderately**: 3,760 (54%) in train, 762 (51%) in validation, 804 (54%) in test (total: 4,286 or 91%) |
| **Very**: 559 (8%) in train, 53 (4%) in validation, 55 (4%) in test (total: 667 or 8%) | **Severely**: 191 (3%) in train, 28 (2%) in validation, 11 (1%) in test (total: 220 or 2%) |
| **Sum**: 7,000 train, 1,500 validation, 1,500 test (total: 7,000) | **Sum**: 1,500 validation, 1,500 test (total: 1,500) |

**Task B Label Distribution**
| Offensive (task B3) | Motivational (task B4) |
|---|---|
| **Yes**: 2,736 (39%) in train, 859 (57%) in validation, 825 (55%) in test (total: 830 or 12%) | **Yes**: 2,736 (39%) in train, 43 (3%) in validation, 56 (4%) in test (total: 2,755 or 37%) |
| **No**: 4,264 (61%) in train, 641 (43%) in validation, 675 (45%) in test (total: 6,170 or 88%) | **No**: 6,170 (88%) in validation, 1,457 (97%) in test (total: 7,627 or 97%) |
| **Sum**: 7,000 train, 1,500 validation, 1,500 test (total: 7,000) | **Sum**: 1,500 validation, 1,500 test (total: 1,500) |

**Parameter Setting**
- Logit Adjustment strategy used to overcome dataset imbalance [23]
- Use `sparse_categorical_crossentropy_with_prior` as loss function in Keras
- Add prior distribution of labels to the loss function: use training set label distribution

**Implementation**
- Utilize Keras, a python deep learning library, for model structure building
- Use TweetEval [18] and CLIP-ViT [19] APIs from huggingface for text and image representation acquisition

**Evaluation Metrics**
- Use weighted-F1 as evaluation metric (official metric proposed by organizers)
- Calculate weighted-F1 score: mean of all per-class F1 scores while considering each class's support


## 5. Results

**Model Performance Summary**

**Evaluation Scores**:
- Model achieved 1st score on Task A evaluation
- Model achieved 2nd score on Task C evaluation

**Weighted-F1 and Average-weighted-F1 Scores**:
- Shown in Table 5
- Performance of models is under-fitting except for Task C1 and C3
    - Evaluation scores on training set lower than validation set
- Model over-fit for Task C3, should cut layers
- Task C1 has a little over-fitting, extent acceptable

**Table 5 Summary**:
- Weighted-F1 and average-weighted-F1 scores for SEFusion
- Note: Weighted-F1 score of Task B4 test set differs from submission answer
    - Checked code, found incorrect model loaded

**Task B3 Performance**:
- Lower performance than other sub-tasks in Task B
- All Task B sub-tasks are binary classification, should be easier
- Weighted-F1 score near 0.5, general baseline for binary classification
- Conclusion: Identifying offensive memes is very hard using existing features


## 6 Conclusion

**SEFusion: A Novel Multi-Modal Fusion Method for Emotion Classification in Internet Memes**

**Proposed Method**:
- SEFusion: a method to combine text and image features jointly for emotion classification in internet memes
- Ranks first on task A and second on task C in the Memotion 3 task

**Methodology**:
- Extract features from memes
- Apply **squeeze and excitation**, simple operations using fully connected layers, reshaping, and matrix multiplication, to fuse text and image features
- Flexible method that can be used to fuse other sets of features extracted through other models
- Can fuse more than two types of features as long as the dimension is reshaped correctly

**Limitations and Future Research**:
- Model learned weight vector for each modality, but the weight did not apply to the corresponding modality
- Will consider unifying the feature dimension of different modalities before performing SEFusion
- Internet meme emotion analysis is still in its infancy
- Performance slightly above baseline model, room for improvement
- Calls for more research, ideally jointly working with adjacent tasks of detecting sentiment and hateful content from memes.

