# NUAA-QMUL at SemEval-2020 Task 8: Utilizing BERT and DenseNet for Internet Meme Emotion Analysis

[NUAA-QMUL at SemEval-2020 Task 8: Utilizing BERT and DenseNet for Internet Meme Emotion Analysis](https://arxiv.org/abs/2011.02788)

## Table of Contents

- [NUAA-QMUL at SemEval-2020 Task 8: Utilizing BERT and DenseNet for Internet Meme Emotion Analysis](#nuaa-qmul-at-semeval-2020-task-8-utilizing-bert-and-densenet-for-internet-meme-emotion-analysis)
- [Utilizing BERT and DenseN et for
Internet Meme Emotion Analysis](#utilizing-bert-and-densen-et-forninternet-meme-emotion-analysis)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 System overview](#3-system-overview)
- [4 Experimental setup](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Conclusion](#6-conclusion)- [Utilizing BERT and DenseN et for\nInternet Meme Emotion Analysis](#utilizing-bert-and-densen-et-for-ninternet-meme-emotion-analysis)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 System overview](#3-system-overview)
- [4 Experimental setup](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Conclusion](#6-conclusion)

## Utilizing BERT and DenseN et for\nInternet Meme Emotion Analysis

**Contribution to SemEval-2020 Task 8: Internet Meme Emotion Analysis**

**Authors**: Xiaoyu Guo (Nanjing University of Aeronautics and Astronautics), Jing Ma (Nanjing University of Aeronautics and Astronautics), Arkaitz Zubiaga (Queen Mary University of London)

**Abstract**:
- Description of system for Internet meme emotion analysis in SemEval 2020 Task 8
- Learning multi-modal embeddings from text and images to classify memes by sentiment
- Model learns text embeddings using **BERT** and extracts features from images with **DenseNet**
- Combines both features through concatenation
- Compares results with **DenseNet**, **ResNet**, **BERT**, and **BERT-ResNet**
- Image classification models have potential to help in meme classification
- DenseNet outperforms ResNet, but adding text features is not always helpful for Memotion Analysis.


## 1 Introduction

**Meme Emotion Analysis**

**Background:**
- **SemEval2020 Task 8**: Meme emotion analysis consisting of three sub-tasks: sentiment prediction, humor identification, emotion quantification
- **Internet memes**: multimodal content (textual, visual, audio) on social media platforms like Facebook, Instagram, Twitter
- **Challenge**: understanding the meaning behind memes for identifying malicious information
- **Characteristics of Internet memes**: image-with-caption class commonly found on social media
- **Proposed system**: BERT-DenseNet deep learning model to classify memes
- **Prior work:** Multi-modal classification, data analysis approaches to studying memes
- **Contributions**: proposing BERT-DenseNet for meme classification

**Meme Emotion Analysis with BERT-DenseNet:**
- Section 3: Proposal of the deep learning model for classifying memes using BERT and DenseNet
- Section 4: Application of the models to tasks A, B, and C in SemEval2020
- Section 5: Results and comparative experiments

**Licensing Information:**
- Creative Commons Attribution 4.0 International License details: http://creativecommons.org/licenses/by/4.0/
- Source code for the model and training procedure: https://github.com/xxxxxxxxy/Memotion-Analysis


## 2 Background

**Background**
- Task A: Classify Internet meme as positive, negative, or neutral
- Task B: Identify if a meme is sarcastic, humorous, offensive, motivational
- Memes contain both visual and textual content (Sharma et al., 2020)
- Previous research focused on automatic generation of memes (Costa et al., 2015; Oliveira et al., 2016; Peirson et al., 2018; Veale et al., 2015), not analysis
- Multi-modal approach proposed for sentiment analysis
- Use Keras functional API and BERT (Devlin et al., 2019) and DenseNet (Huang et al., 2017) in the model.

**Contributions**:
1. Combine NLP, CV, and deep learning techniques for sentiment analysis of memes
2. Find that performance of DenseNet is better than ResNet
3. Proposed deep learning model outperforms competitive baselines except for task B.


## 3 System overview

**Model Overview: Memotion Analysis**

**Classification Sub-tasks:**
- Task A: binary or multiclass (not specified)
- Task B: four binary sub-tasks
- Task C: one classification task

**Model Architecture:**
1. **Input Layer**:
   - Input: (None, None)
   - Output: (None, None)
2. **BERT**:
   - Model input: [(None, None), (None, None)]
   - Output: [(768), (768)]
3. **segments**:
   - Input Layer
   - Output: (None, None)
4. **image\_input**:
   - Input Layer
   - Output: (None, 224, 224, 3)
5. **densenet121**:
   - Model input: (None, 224, 224, 3)
   - Output: (None, 7, 7, 1024)
6. **lambda\_1**:
   - Lambda function input: (None, None, 768)
   - Output: (None, 768)
7. **global_max_pooling2d_1**:
   - GlobalMaxPooling2D input: (None, 1024)
   - Output: (None, 1024)
8. **concatenate\_1**:
   - Concatenate function input: [(768), (1024)]
   - Output: (None, 1792)
9. **dense\_1**:
   - Dense layer input: (None, 1792)
   - Output: (None, 512)
10. **dropout\_1**:
    - Dropout layer input: (None, 512)
    - Output: (None, 512)
11. **softmax/sigmoid**:
    - Used for tasks A and C (softmatch)
    - Class scores text and encoder image

**Data Pre-processing:**
- Delete quotation marks in CSV files
- Copy OCR extracted text to corrected text when necessary
- Check images and add text if both OCR extracted text and corrected text are null
- Use WordPiece tokenization for text encoding

**Text Encoding:**
- Pretrained BERT encoder with L-12 H-768 A-12
- Transform input text into indices and segments
- Use [CLS] vector from the Lambda function as text embeddings (size 768)

**Image Encoding:**
- Convert images to arrays before encoding
- Use DenseNet for image feature extraction
- Global Max Pooling to reduce image embeddings to size 1024
- Combine text and image embeddings using concatenate function

**Combination and Final Layers:**
- Dense layer followed by dropout layer
- No need to add too many layers on top of the model due to complexity of BERT and DenseNet

**Activation Functions:**
- Softmax for tasks A and C
- Sigmoid for task B.


## 4 Experimental setup

**Experimental Setup**
- Three groups of classifiers: unimodal using text, machine vision, multimodal using both
- Data: publicly released dataset with 5,192 train, 1,800 dev, and 1,878 test mentions

**Data Splitting**
- Tables 1-3 show data splitting for three tasks: A (positive/neutral/negative), B (funny/sarcastic/offensive), C (scale of funny, sarcastic, offensive)
- Different proportions of labels in each task

**Parameter Settings**
- Model trained using Adam optimizer with learning rate 1.00E-05 and batch size 16 mentions
- Dropout rate of 0.2 on dropout layer and L2 regularization of 0.02 on dense layer
- Class weight parameter based on actual ratio in training data to balance labels and reduce overfitting
- Hyperparameters for comparative experiments: same optimizer, batch size, and class weight; different models (BERT, DenseNet, ResNet) and their variants with different dropout rates and L2 regularization

**External Library**
- Keras used to build model structure due to lack of official method to call BERT within it
- keras-bert library used for implementing BERT with Keras and loading pre-trained models.

**Evaluation**
- Performance evaluated using macro-F1 score
- For tasks B and C, final score produced by averaging macro-F1 scores of each subtask.


## 5 Results

**Results of SemEval Task:**
* Our model achieved 14th place for tasks A and C, below baseline for task B
* Highest score: 0.3547 (Task A), 0.5183 (Task B), 0.3225 (Task C)
* Baseline: 0.2176 (all tasks)

**Performance Analysis:**
* Task B: worst result, overfitting observed in all submissions
* Future improvement needed to address overfitting issue
* Re-trained BERT-DenseNet model performs better than final submitted model for Tasks B and C

**Comparison of Models:**
| Model  | Task A   | Task B    | Task C    |
|---------|----------|-----------|-----------|
| Highest | 0.3547   | 0.5183    | 0.3225    |
| Text BERT| 0.1574   | 0.4798    | 0.2749    |
| VisionDenseNet | 0.3344   | 0.5120    | 0.3209    |
| ResNet    | 0.3186   | 0.4965    | 0.3129    |
| Multi-modalBERT-DenseNet| 0.3137   | 0.4999    | 0.3127    |
| BERT-ResNet | 0.3305   | 0.4946    | 0.3149    |
* DenseNet outperforms ResNet due to feature reuse and access to previous layer feature-maps
* Limited data availability in the dataset makes it difficult for models to extract sufficient features
* Overfitting may occur easily due to deep model structure.


## 6 Conclusion

**Conclusion**
- Description of entry for SemEval 2020 Task 8: **Emotion Analysis**
- Presented method using deep learning to classify memes by emotion
- Found that image classification models help with meme classification, with **DenseNet** outperforming **ResNet**
- Adding text-based features is not always helpful for Memotion Analysis
- Proposed model outperforms base lines except for task B
- Classifier is still in early development
- Aims to:
  - Enrich meme datasets from social media and keep balance among classes
  - Consider additional features (e.g., adult slang)
  - Try other methods for combining features
- Present work is limited to image-and-text memes, aiming to consider other types (e.g., video and audio memes) in the future.

