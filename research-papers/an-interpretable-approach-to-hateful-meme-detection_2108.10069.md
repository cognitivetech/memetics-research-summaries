# An Interpretable Approach to Hateful Meme Detection

[An Interpretable Approach to Hateful Meme Detection](https://arxiv.org/abs/2108.10069)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Dataset/Challenge Description](#2-datasetchallenge-description)
- [3 Related Work](#3-related-work)
- [4 Methods/Approach](#4-methodsapproach)
- [5 Results and Discussion](#5-results-and-discussion)

## Abstract

**Hateful Meme Detection Approach**
- **Tanvi Deshpande** and **Nitya Mani**: Interpretable approach to hateful meme detection
- Uses machine learning and simple heuristics to identify features most important for classifying a meme as hateful
- Builds gradient-boosted decision tree and LSTM-based model, achieving comparable performance (73.8 validation and 72.7 test AUROC) to humans and state-of-the-art transformer models on this challenging task

**Key Concepts**
- Computing methodologies: Artificial intelligence; Machine learning
- Multimodal fusion; Multimodal representations

**ACM Reference Format**:
- Tanvi Deshpande and Nitya Mani. 2021. An Interpretable Approach to Hateful Meme Detection. In Proceedings of the 2021 International Conference on Multimodal Interaction (ICMI '21), October 18–22, 2021, Montréal, Canada. ACM, New York, NY, USA, 5 pages. <https://doi.org/10.1145/3462244.3479949>


## 1 Introduction

**Memes and Hate Speech**

**Impact of Memes on Spreading Hate Online**:
- Memes have become a powerful medium for spreading hate online
- Social media platforms facilitate the spread of prejudiced messages through memes
- Memes are frequently used to spread hate, alt-right, and neo-Nazi rhetoric
- Reddit's r/The_Donald and 4chan are responsible for a large fraction of hateful memes
- Over 600,000 racist memes were shared on /pol/ in just 13 months

**Challenges in Detecting Hateful Memes**:
- Flagging hateful memes before they spread is challenging for humans and AI models
- Ineffectiveness of current hate speech moderation methods highlights the need to improve automatic hate speech detection
- The May 2020 Facebook AI dataset of over 10,000 multi-modal memes was released as part of the Hateful Memes Challenge

**Motivation**:
- Human annotations achieved poor performance on the Hateful Memes dataset, suggesting a need for machine learning augmentation
- This work explores using human-interpretable machine learning algorithms to outperform non-transformer baselines and achieve comparable performance to complex transformer models
- The goal is to create a reasonably-performant model that can flag memes and provide insights into important features for human classification


## 2 Dataset/Challenge Description

**Hateful Memes Dataset:**

* Contains 12,140 samples, ~63% non-hateful and ~37% hateful
* Hateful memes often have text/image confounders
* Exploratory data analysis: hate attacks minority groups using stereotypes & threats/violence
* May-October 2020 competition for researchers to fine-tune transformer models
* Metric: area under the Receiver Operating Characteristic (auROC) curve


## 3 Related Work

**Related Datasets:**
- **Hateful Memes dataset**: First of its kind, but similar datasets exist
- **SemEval-2020 Task 8 (Memotion analysis) [21]**:
  - Involves classifying sentiment, humor, offensiveness, and motivation on a dataset of 10,000 human-annotated memes
  - Macro F1-score for baseline model: 0.21 (sentiment), 0.50 (humor type classification)
  - Emphasizes the challenge of interpreting memes
- **Additionally [15]**: Similar dataset with 2,631 Italian memes

**Text-only Hate Speech Detection:**
- Extensive work on text-based hate speech detection
- Current state-of-the-art approaches use:
  - BERT and other embedding schemes

**Multimodal/Meme Hate Detection:**
- State-of-the-art multimodal hate speech detection includes:
  - Unimodally pretrained models for early and late fusion
  - Multimodal pretraining (e.g., BERT, VisualBERT)
- **Hateful Memes challenge winners**: Achieved auROC's between 0.78 and 0.84
  - Relyed heavily on large multimodal transformer models (OSCAR, UNITER, VisualBERT, LXMERT) for fine-tuning and ensembling
- Despite outperforming baselines, these models are still far from an ideal resolution to identifying hateful memes.


## 4 Methods/Approach

**Methodology for Hateful Meme Detection**

**Approach**:
- Use thoughtfully engineered features
- Pass to two models: Gradient Boosted Decision Tree (GBDT) and Simple LSTM
- Allows easy isolation of crucial features and extraction of underlying logic

**Text and Image Embedding**:
- **Gradient-boosted decision tree**:
  - Use captioning model to capture image content as text
  - Embed both text and images using tf-idf
- **LSTM model**:
  - Concatenate meme image captions and text
  - Embed using DistilBERT

**Additional Textual Features**:
- **Named-entity detection**: Use SpaCy to extract culturally relevant components
- **Profanity/slurs**: Counts of profanity and slurs banned by Google
- **Hateful words**: Flag words commonly used in derogatory manner, like "dishwasher"
- **Text sentiment**: Use TextBlob to identify polarity and subjectivity
- **Emotion detection**: Use text2emotion library to score meme text
- **Semantic similarity**: Use RoBERTa model to detect semantic similarity between meme text and generated captions/entities

**Image-based Features**:
- Preprocess images by removing text using OCR, captioning them, and detecting objects/web entities

**Total Preprocessing**:
- Concatenate emotion, sentiment, semantic similarity, profanity, and hateful words features (13x1)
- Combine meme text, captions, detected objects, and named/web entities (19651x1)

**Models**:
- Use 90-10 train/validation-test split
- Build two classes of models:
  - **GBDT**: Input joint tf-idf embeddings and engineered features
  - **LSTM**: Use pretrained DistilBERT model to process text and captions jointly


## 5 Results and Discussion

**Summary of Results**
- Significant improvement from non-transformer base models and comparable results to transformer baselines using more lightweight and interpretable models
- Able to augment memes with most important features determined by the model for easier human classification

**Loss Function and auROC Curve (Figure 4)**
- LSTM Model: Plots from the LSTM Model

**Discussion**
- **Gradient-boosted decision trees (GBDT) feature importances**:
  - Yields 494 predictive features, ranked by `feature_importances_` property
  - Precision of 0.53 and recall of 0.58
  - Top features: Certain tf-idf embedded words, text emotion, named entities (e.g., Hitler, ethnic groups), Table 2

- **GBDT vs. recurrent network**:
  - GBDT provides faster computation time and ranking of most important features to meme detection
  - Effective at including engineered features like text sentiment, which are meaningless to LSTMs
  - Figure 5: Feature importances of top engineered features

**Table 1: Results**
- AUROC Accuracy
- Source Model Validation Test Validation Test
  - Human: 82.65 - 84.70
  - Hateful Memes Image-grid: 58.79, 52.63, 52.73, 52.00
  - Non-transformer Baselines Image-region: 57.98, 55.92, 52.66, 52.13
  - Text-only BERT: 64.65, 65.08, 58.26, 59.20
  - Late Fusion: 65.97, 64.75, 61.53, 59.66
  - Hateful Memes ViLBERT: 71.13, 70.45, 62.20, 62.30
  - Transformer Baselines VisualBERT: 70.60, 71.33, 62.10, 63.20
  - ViLBERT CC: 70.07, 70.03, 61.40, 61.10
  - VisualBERT COCO: 73.97, 71.41, 65.06, 64.73
  - GBDT w/ image tagging: 70.86, 71.11, 70.27, 71.19
  - Our Models GBDT w/ tagging/captions: 71.67, 70.90, 69.58, 68.45
  - GBDT w/ BERT only: 70.38, 71.52, 68.97, 69.36
  - LSTM w/ BERT features: 73.78, 72.72, 67.83, 66.39

**Table 2: Top Features (GBDT)**
- Named Entities: `ent_jews_norp`, `ent_muslim_norp`, `ent_hitler_person`, `ent_mexicans_norp`, `ent_islamic_norp`
- Total Features: 3.4×10−2 (`ent_jews_norp`), 2.3×10−1 (text hate words), 3.0×10−2 (`ent_muslim_norp`), 1.1×10−1 (club), 6.4×10−2 (`isis`), 5.3×10−2 (`jews`), 5.1×10−2 (`muslims`), 2.5×10−2 (`ent_asians_norp`), 4.3×10−2 (teacher)

**Confounders**
- Model correctly identifies not only simple hateful memes but also distinguishes between hateful memes and nontrivial confounders, leveraging both modalities for classification

**Table 3: Confounder/hateful meme comparison**
- Label: Hateful meme Image confounder
  - Meme: "a group of people playing on a beach" vs. "a black and white photo of a monkey"
  - Predicted Label: 1 (hateful) vs. 0 (not hateful)

**Figure 6: Classified Hateful Memes from Test Set**
- Correctly classified hateful meme
- Misclassified hateful meme

**Extensions and Conclusion**
- Further extensions: Measuring human performance on augmented memes, developing features based on metadata (shares, user post history)


---

Thank you to arXiv for use of its open access interoperability.