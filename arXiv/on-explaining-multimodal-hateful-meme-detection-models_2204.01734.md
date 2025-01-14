# On Explaining Multimodal Hateful Meme Detection Models

[On Explaining Multimodal Hateful Meme Detection Models](https://arxiv.org/abs/2204.01734)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Research Questions](#2-research-questions)
- [3 Experiments](#3-experiments)
	- [3.1 Experiment Settings](#31-experiment-settings)
	- [3.2 Modality Attribution](#32-modality-attribution)
	- [3.3 Visual-Text Slurs Grounding](#33-visual-text-slurs-grounding)
	- [3.4 Bias and Error Analysis](#34-bias-and-error-analysis)
- [4 Conclusion](#4-conclusion)

## Abstract

**Multimodal Hateful Meme Detection Models: Understanding What These Models Learn**

**Background:**
- New research topic in academic and industry communities: Hateful meme detection
- Pretrained visual-linguistic models used for multimodal classification task
- Results promising but understanding of what these models learn is unclear

**Research Gap:**
- Image modality contributes more to hateful meme classification task
- Visual-linguistic models able to perform visual-text slurs grounding to a certain extent

**Three Research Questions:**
1. **What derogatory references do these visual-linguistic models capture in multimodality (image and text) of hateful memes?**
2. **Can these models effectively identify hate speech within both image and text modalities?**
3. **How do the visual-linguistic models perform on false positives due to biases acquired during training?**

**CCS Concepts:**
- Natural language processing
- Computer vision representations

**Keywords:**
- Hate speech, hateful memes, multimodal, explainable machine learning

**ACM Reference Format:**
Ming Shan Hee, Roy Ka-Wei Lee, and Wen-Haw Chong. 2022. On Explaining Multimodal Hateful Meme Detection Models. In Proceedings of the ACM Web Conference 2022 (WWW '22), April 25–29, 2022, Virtual Event, Lyon, France. ACM, New York, NY, USA, 5 pages. https://doi.org/10.1145/3485447.3512260

**Disclaimer:**
This paper contains violent and discriminatory content that may be disturbing to some readers.


## 1 Introduction

**Motivation**
- Internet memes often spread hatred under the guise of humor [8,13,24]
- Facebook released a dataset of hateful memes for research purposes [13]
- Research community has proposed solutions to address hateful meme propagation [16,20,31,35,36]

**Research Objectives**
- Understanding visual-linguistic models is an emerging area of interest [3,7,18,22]
- Previous work explored the internal behaviors of pre-trained language models [4]
- This paper aims to contribute to the understanding of visual-linguistic models by investigating how they understand hateful memes
- First paper to examine what visual-linguistic models learn during hateful meme classification task training.

**Contributions**
- Proposed three research questions:
  - **Visual-linguistic models**: Importance of visual modality in hateful meme classification [1]
  - **Learning visual-text slurs grounding** [2]
  - **Acquiring biases affecting hateful meme classification performance** [3]

**Findings**
- Visual-linguistic models accord higher importance to the visual modality during hateful meme classification [1]
- Models learn visual-text slurs grounding [2]
- Acquired biases negatively impact hateful meme classification performance [3]


## 2 Research Questions

**Research Questions (RQ) for Visual-Linguistic Models in Hateful Meme Classification:**
1. **Modality Attribution (RQ1):**
   - Understanding the contribution of text and visual information towards hateful meme classification
   - Applying attribution methods to examine input features' impact on deep models' predictions
2. **Visual-Text Slurs Grounding (RQ2):**
   - Investigating subtle allegations in derogatory terms communicated through both modalities
   - Extending studies on semantic grounding capabilities of visual-linguistic models to hateful memes
3. **Bias and Error Analysis (RQ3):**
   - Examining biases in text and visual modalities of wrongly classified memes
   - Conducting a preliminary analysis on group identifier biases in hateful meme classification models.


## 3 Experiments

### 3.1 Experiment Settings

**Facebook Hateful Meme Dataset**
- Dataset constructed by Facebook for multimodal hateful meme classification challenge
- Contains 10,000 memes with binary labels (hateful or non-hateful)
- Distributions outlined in Table 1
- Used in many research studies

**Models**
- **VilBERT** and **VisualBERT**: state-of-the-art visual-linguistic models for multimodal tasks
- Both models use pre-trained text from BERT and image features from Faster-RCNN with ResNeXt-152 backbone
- Can be trained on multimodal objectives as intermediate step before fine-tuning for hateful meme classification task
- **VilBERT CC** and **VisualBERT COCO**: multimodally pre-trained versions of these models, fine-tuned for hateful meme classification task
- Trained using Facebook MMF framework, hyperparameters adopted from [13]


### 3.2 Modality Attribution

**Contribution of Modalities in Hateful Meme Detection:**

**Gradients as Feature Importance**:
- Gradients represent contribution of each modality towards model's decision
- Equated to weightage each input feature has on making prediction

**Calculating Contribution**:
- Obtain gradients for inputs in each modality through backpropagation
- Normalize gradients by their magnitude to enable comparison
- Summation of normalized gradients as contribution of each modality
- Average and standard deviation across 500 samples in test data

**Analysis Considerations**:
- Ignore empty tokens in text inputs, as they don't contain meaning or contribute to gradient

**Observed Results**:
- Visual modality contributes more than text modality towards model’s prediction (higher average gradient)
- Low standard deviation for both modalities, indicating little variation in contribution across samples

**Concurrence with Previous Findings**:
- Concurs with Frank et al. [7]'s findings: Vision-and-language models tend to attend more to visual information than text information

**Possible Reason**:
- Internet memes generally have relatively short text (avg. 14 words, max. 54 words) compared to image features (top 100 image regions)
- Models may leverage the modality with more features (image features outnumber text features)


### 3.3 Visual-Text Slurs Grounding

**Visual-Linguistic Models for Understanding Multimodal Associations**

**Simplistic Solution to Learn Inter-Modality Alignments**:
- Uses a stack of Transformer layers that implicitly align text and visual input using self-attention
- Recent studies show that attention weights in VisualBERT establish intricate visual-text associations (e.g., entity grounding, syntactic grounding)

**Investigating Visual-Text Alignments for Hateful Memes**:
- Aim to understand how visual-linguistic models align visual features and text in hateful memes
- Visualize the top 9 features ranked by their contribution to the model's decisions

**Examining Specific Slurs**:
- "**dishwasher**": Sexist slur targeted at women, found in hate speech that undermines gender equality
- "**goat-f*cker**": Offensive slur targeted at the Muslim community, suggesting a relationship with goats (bestiality)

**Observed Visual-Text Alignments**:
- **dishwasher**: Model forms alignments between "##er" and images containing the woman in lower layers; residual alignment for "##wash" by end of computation
- **goat-f*cker**: Models assign significant attention weights to "f*ck" and "goat" bounding regions in early layers, with more weight on "f*ck"; no-op alignments to unrelated visual segments


### 3.4 Bias and Error Analysis

**Error Analysis of Hateful Meme Classification Models**

**Interest in False Positives**:
- Reveals features that models are overly sensitive to
- May indicate learned biases

**Visual Feature Bias Analysis**:
- Use bounding regions to visualize critical visual features
- Inspect subword tokens and individual word contributions using Integrated Gradients

**Example 1 (Figure 3a)**:
- "dishwasher" and "sandwich" subword tokens have high contribution towards hateful prediction
- Woman in image also receives significant attention weight
- Model likely learned bias where presence of these words/images leads to hateful classification

**Example 2 (Figure 3b)**:
- Bias towards the group identifier term "Islamic"
- Word "Islamic" does not assign much attention to any bounding regions
- Bias likely present in unimodal text space rather than multimodal


## 4 Conclusion

**Study on Hateful Meme Classification with Visual-Linguistic Models**

* Analyzed hateful meme classification using visual-linguistic models.
* Image modality had a greater impact on classification compared to text.
* Visual-linguistic models performed slurs grounding.
* Biases in models resulted in false positives.
* Future work: more datasets, benchmarking, and bias reduction techniques.
* Paper presentation: WWW '22, April 25-29, 2022, Virtual Event, Lyon, France.

