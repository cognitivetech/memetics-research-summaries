# Multimodal and Explainable Internet Meme Classification

[Multimodal and Explainable Internet Meme Classification](https://arxiv.org/abs/2212.05612)

## Table of Contents
- [Abstract](#abstract)
- [Introduction](#introduction)
- [Method](#method)
- [Experimental Setup](#experimental-setup)
- [Analysis](#analysis)
- [Discussion](#discussion)
- [Related Work](#related-work)

## Abstract

**Internet Meme Classification: Multimodal and Explainable Approach**

**Background:**
- Difficulty of content moderation on online platforms due to Internet memes
- Existing work focuses on black-box methods, neglecting semantics and context

**Objective:**
- Develop a modular and explainable architecture for Internet meme understanding
- Design multimodal classification methods using example-based reasoning and SOTA models in text and vision representation

**Contributions:**
1. **Modular and Explainable Architecture:**
   - Addresses the need for transparency in Internet meme classification
2. **Multimodal Classification Methods:**
   - Example-based reasoning: individual cases considered
   - Prototype-based method: training cases used as templates
3. **Textual and Visual SOTA Models:**
   - Textual representation of memes
   - Visual representation of memes
4. **Tasks Studied:**
   - Hate Speech Detection
   - Misogyny Classification
5. **Comparison:**
   - Example-based vs prototype-based methods
   - Text, vision, and multimodal models across various harmfulness categories (stereotype, objectification)
6. **User Interface:**
   - Facilitates comparative analysis of examples retrieved by all models for a given meme
7. **Implications:**
   - Informs the community about strengths and limitations of explainable methods in detecting harmful memes.

## Introduction

**Introduction**
- Social media content moderation is a societal challenge due to:
  - Lowered barriers to information sharing leading to harmful narratives and misinformation spread
  - Difficulty detecting toxicity or inappropriateness, even for humans
  - Content can be multimodal (text, images, video) and spread quickly
  - Coordinated influence operations (bots, trolls) amplifying the impact
  - Lack of consistent content moderation policies across platforms

**Implications of Content Moderation Policies**
- Late, inconsistent, or unfair moderation can:
  - Anger users and contribute to reinforcing conspiracy theories
  - Permit coordinated influence operations or enable toxic communities
  - Disproportionately affect marginalized groups (e.g., women, ethnic minorities)

**Challenges in Meme Analysis**
- Internet memes are multimodal (image and text), creative, relatable, and community-dependent
- Correct interpretation requires understanding the virtual context
- Memes spread complex messages with minimal information units
- Fluid nature: subject to variations and alterations
- Inaccurate classification can lead to inadequate moderation interventions

**Prior Work on Meme Analysis**
- Temporal spread (virality) analysis
- High-level categorization tasks like hate speech detection
- Limited work on semantics and pragmatics of memes
- Combining text, vision, and extra contextual knowledge is an AI-complete problem

**Proposed Approach**
- Employ explainable reasoning methods for meme understanding: example-based and prototype-based reasoning
- Leverage state-of-the-art (SOTA) models to extract features from textual and visual data
- Compare the performance of example-based, prototype-based, text-only, vision-only, and multimodal models on tasks like hate speech detection and misogyny classification.
- Develop a user-friendly interface to facilitate comparative analysis of examples retrieved by different models for a given meme
- Make code available to facilitate future research on explainable IM classification for social good.


## Method

**Internet Meme Classification Model: Example-based vs. Prototype-based Approaches**

**Example-based Meme Classification:**
- Uses an example-based method for predictions and explanations
- Shows similar memes to end-users to understand the model's behavior
- Helps users understand how the classifier represents a meme compared to training dataset
- Works well despite text, image, and cultural specificity in memes
- Limited effectiveness due to context dependence

**Prototype-based Meme Classification:**
- Uses prototype theory for label-wise prototypes and rule-based decision algorithm
- Inherently interpretable as it is not a post-hoc approach
- Based on the theory that there is a graded degree of belonging to a conceptual category, with some members being more central than others
- Uses training data features extracted using pre-trained model to create class-wise prototypes (local peaks for class distribution)
- New unlabelled sample can be evaluated against these prototypes and classified using rule-based local and global decision-making stages.

**Pretrained Models for Feature Extraction:**
- Textual Models: BERT base model, trained on BooksCorpus and English Wikipedia; BERTweet model with the same architecture as BERT but trained over 80 GB corpus of 850M English tweets using RoBERTa pretraining procedure.
- Vision Models: CLIP (Contrastive Language-Image Pre-training) model, trained with Natural Language Supervision over 400 million (image, text) pairs collected from the Internet with contrastive objective.
- Mixed Models: Concatenate features from BERTweet and CLIP together for downstream predictions.


## Experimental Setup

**Experimental Setup**
- Discussing setup for evaluating approaches over MAMI and Hateful Memes datasets
- Two sub-tasks of misogyny detection and classification: Sub-task A (MAMI) and Sub-task B (MAMI)

**Tasks and Datasets**
- SemEval-2022 Task 5: Multimedia Automatic Misogyny Identification (MAMI) dataset
  * Sub-task A: Misogyny Detection
    **Focuses on detecting whether a meme is misogynous**
    **Inter-annotator Fleiss-k Agreement**: 0.5767
  * Sub-task B: Misogyny Type Classification
    **Categorizes a meme into one or more misogyny types (shaming, stereotype, objectification, violence)**
    **Inter-annotator Fleiss-k Agreement**: 0.3373
  * Data statistics for both subtasks presented in Table 2
- Hateful Memes dataset
  * Consists of a single task of meme hate detection
  * Contains 10,000 memes equally divided into hateful and not-hateful classes
  * Human accuracy: 84.70%, ranging from 83% to 87%

**Evaluation**
- Consistent with the original MAMI dataset paper
- Sub-task A evaluated using macro-average F1 measure for each class label
- Sub-task B evaluated using weighted-average F1 measure, weighted by true label count for each category
- Performance statistics for all participants in SemEval-2022 competition presented in Table 3
- Manually evaluate example-based explanation approach and prototype-based (xDNN) method using a visualization tool and the training dataset

**Model Training Details**
- Classification model uses a trainable neural head over frozen pre-trained models
- Trained with Binary Cross Entropy Loss, Adam optimizer, and learnning rate of 10^-4
- Table 1 describes each layer of the classification head
- Hidden state of L3 is used for feature extraction for similar example searches

**Pretrained Models**
- xDNN: generative model that learns prototypes and distributions from training data
- Reusing publicly available xDNN implementation for experiments with different pre-trained models.


## Analysis

**Performance Comparison of Meme Classification Models**

**Analysis**:
- Compares different methods and feature extraction models for meme classification
- Focuses on both accuracy and explainability

**Results**:
- **Table 4**: Performance comparison of individual models on MAMI and Hateful Meme datasets
- Observations:
    - All models perform better at misogyny detection in MAMI than hate detection in Hateful Meme
    - BERTweet (Twitter model) outperforms BERT-based models for MAMI, but the difference is minimal
    - For Hateful Meme, BERT performs better than BERTweet, suggesting a shift in distribution between datasets
    - Example-based deep learning method outperforms prototype-based xDNN for both datasets and pre-trained models
    - CLIP image model performs better than text models for both datasets
    - Combined CLIP and BERTweet model performs best, with minimal improvement over CLIP alone

**Explainability Analysis**:
- **Example-Based Classification**: Displays most similar images from training dataset for explainability
- Observations:
    - Models correctly detect misogyny and stereotype in test image
    - Combined model retrieves most reliable images related to both misogyny and stereotyping
    - CLIP and BERTTweet models partially useful, with CLIP retrieving more relevant images
    - Text-only setting does not accurately reflect the subject of discussion in the test image

**Prototype-Based Classification (xDNN)**:
- Inherently explainable as it predicts label based on closest prototype
- Surprisingly, xDNN creates prototypes equal to training supports for each class. Investigation ongoing to find exact reason.


## Discussion

**Meme Classification: Lessons and Discussion Points**

**Findings on Meme Classification:**
- Balancing explainability and accuracy through meme classification methods
- Example-based method achieved higher performance, simpler and more intuitive explanations
- Vision models outperformed language models; combination of both yielded best results

**Challenges in Meme Classification:**
- Lack of context: Pretrained models lack access to real-world context which can lead to wrong classifications
- Need for cultural and folkloric understanding: Memes often rely on common sense and shared references for interpretation

**Improving Meme Classification:**
- Account for cultural and folkloric nature of memes: Consider both image and text, implicit references
- Integration of background knowledge and figures of speech: Capture explicit and implicit meanings to achieve robust results

**Subjectivity in Ground Truth Labels:**
- Inherent subjectivity in misogyny detection and type classification
- Labelers' background and familiarity with social norms affect ground truth labels
- Consistency issues in labeling aspects like sexism: Address biases through careful evaluation and consideration.


## Related Work

**Related Work on Internet Memes in AI:**
- Most prior work focused on understanding virality and spread of memes on social media (Marino 2015; Taecharungroj and Nueangjamnong 2014; Ling et al. 2021)
- Detection of hate speech in memes: Hateful Memes Challenge and Dataset (Kiela et al. 2021), ViLBERT (Lu et al. 2019), UNITER (Chen et al. 2020), CLIP (Radford et al. 2021b)
- Organizing memes into a genealogy for knowledge base building: Sheratt (Sheratt 2022)
- No prior work focused on multi-faceted and explainable methods for understanding IMs

**Related Work on Explainability:**
- Example-based explanations enhance users' comprehension of deep learning models (Cai, Jongejan, and Holbrook 2019; Ford, Kenny, and Keane 2020)
- Prototype-based classification methods for visual tasks: xDNN (Angelov and Soares 2019)

**Findings:**
- Example-based methods achieve higher performance and more intuitive explanatory power compared to prototype-based methods in IM classiﬁcation tasks
- Vision models are more effective than language models for feature extraction, and their combination achieves the best performance.

**Challenges:**
- Including background knowledge and real-world context in complex multimodal tasks
- Concerns about subjectivity in related tasks.

---

Thank you to arXiv for use of its open access interoperability.
