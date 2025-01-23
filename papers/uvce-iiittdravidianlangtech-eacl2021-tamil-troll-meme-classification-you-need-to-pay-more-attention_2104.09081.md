# UVCE-IIITT@DravidianLangTech-EACL2021: Tamil Troll Meme Classification: You need to Pay more Attention

[UVCE-IIITT@DravidianLangTech-EACL2021: Tamil Troll Meme Classification: You need to Pay more Attention](https://arxiv.org/abs/2104.09081)

## Table of Contents

- [UVCE-IIITT@DravidianLangTech-EACL2021: Tamil Troll Meme Classification: You need to Pay more Attention](#uvce-iiittdravidianlangtech-eacl2021-tamil-troll-meme-classification-you-need-to-pay-more-attention)
- [Tamil Troll Meme
Classiﬁcation](#tamil-troll-memenclassiﬁcation)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Data](#3-data)
- [4 System Description](#4-system-description)
- [5 Experiments](#5-experiments)
- [6 Results](#6-results)
- [7 Conclusions](#7-conclusions)- [Tamil Troll Meme\nClassiﬁcation](#tamil-troll-meme-nclassi-cation)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Data](#3-data)
- [4 System Description](#4-system-description)
- [5 Experiments](#5-experiments)
- [6 Results](#6-results)
- [7 Conclusions](#7-conclusions)

## Tamil Troll Meme\nClassiﬁcation

**Tamil Troll Meme Analysis**

**Background:**
- Dravidian language commonly used in southern Asia: Tamil
- Era of social media: memes as part of daily life
- Research focus: understanding meaning of Tamil memes through classification as troll or non-troll

**Approach:**
1. Use a transformer-transformer architecture model for analysis
2. Attention as main component to achieve state-of-the-art results
3. Binary classification task with dataset consisting of:
   - Troll images and their captions (text)
   - Non-troll images and their captions (text)
4. Objective: pay more attention to extracted features, ignore noise in both images and text.

**Authors:**
- Siddhanth U Hegde (University Visvesvaraya College of Engineering, Bangalore University)
- Adeep Hande (Indian Institute of Information Technology Tiruchirappalli, Tamil Nadu)
- Ruba Priyadharshini (ULTRA Arts and Science College, India)
- Sajeetha Thavareesan (Eastern University, Sri Lanka)
- Bharathi Raja Chakravarthi (National University of Ireland Galway)


## 1 Introduction

**Memes:**
- Became ubiquitous over the internet in past decade
- Come in various formats: images, video, text and images
- Popularity leads to usage as communication tool on social media platforms
- Text in memes makes sentiment analysis difficult (Avvaru & Vobilisetty, 2020)
- Used sarcastically in sensitive contexts like politics, casteism (French, 2017; Nave et al., 2018)
- Multimodality allows insight into societal factors and cultural implications (Milner, 2013)
- Analyzing emotions can help identify fake news, offensive content (Chakravarthi et al., 2020b,a)
- May become integral part of understanding racial and gender discourse on social media platforms (Milner, 2013; Ghanghor et al., 2021b,a)

**Memes in Society:**
- Manual monitoring and moderation of user-generated content is insufficient due to high volume of data
- Development of automated systems for moderation (Kumar et al., 2018; Yasaswini et al., 2021; Puranik et al., 2021; Chakravarthi et al., 2020c; Mandl et al., 2020)
- In countries with large populations like India, memes target specific communities
- Dataset for meme classification based on troll classifications in Tamil language (Suryawanshi et al., 2020)
- Tamil language: spoken in South Asia; earliest known inscriptions from 580 BCE and 260 BCE respectively (Chakravarthi, 2020)
- Officially recognized as the language of Tamil Nadu, India, Singapore, and Sri Lanka (Chakravarthi et al., 2018, 2019)

**Meme Classification:**
- Task consists of identifying troll or non-troll memes using provided images and captions (Suryawanshi & Chakravarthi, 2021)
- Use a combination of Vision Transform (ViT) and mBERT for most efficient model (Dosovitskiy et al., 2021; Devlin et al., 2019)


## 2 Related Work

**Related Work on Memes**
- **Internet memes**: subject of interest for Computer Vision and Natural Language Processing researchers
- **Usage of memes on social media platforms**: expressing opinions, illustrating social issues, showcasing personal stance
- **Reasons for the spread of memes**: novelty, simplicity, coherence, emotional attachment, ability to have different meanings based on perception
- **Multimodal sentiment analysis**: developed by Hu and Flaxman using a deep neural network that combines visual analysis and text analysis to predict user's emotional state from Tumblr posts.


## 3 Data

**Dataset:** Troll Classification

* **Description**: Troll Classification dataset of Tamil Memes by Suryawanshi et al. (2020) with 2,699 memes.
* **Distribution**:
    * Troll: 1,154 (42.8%)
    * Non-Troll: 917 (34.3%)
    * Total: 2,071 images
    * Class Train: 1,280 (61.4%)
    * Validation: 129 (5.7%)
    * Test: 662 (32.9%)


## 4 System Description

**Multimodal Deep Learning for AI**
- **Multimodal deep learning**: robust and efficient way to integrate multiple communicative modalities for improved results
- Objective: output a single value (Troll or Non-Troll) based on image and text analysis
- Model design: Vision Transformer (ViT) for images, Bidirectional Encoder Representations from Transformers (BERT) for captions
- **ViT**: transformer architecture with global attention, receiving 2D patches as input, projected and multiplied with an embedding matrix
- **BERT**: language representation model trained on Wikipedia corpus, jointly conditioned on left and right contexts for extracting meaning

**Classification Results**
- Precision: 0.87 to 0.99, Recall: 0.60 to 0.98, F1-Score: 0.40 to 0.93, Support: 229 to 1052
- Accuracy: 0.60 (ViT on images) and 0.60 (BERT on captions)

**Importance of Attention Gain**
- Model focuses on salient portions of text and images for better performance


## 5 Experiments

**PyTorch Implementation:**
- Used PyTorch version 1.5.0 in Google Colaboratory environment
- Preprocessing of images:
  * Resized to 256 X 256 pixels
  * Removed texts and borders, resulting in 224 X 224 pixel images
  - Normalized RGB channels with mean and standard deviation for input to transformer

**Transformer Model:**
- Original trained on ImageNet dataset
- Fine-tuned with default hyperparameters:
  * 16 patches, embed dimension of 768, 12 layers, 12 attention heads, dropout rate of 0.1
- Replaced head outputting 1000 classes with a linear layer of 128 neurons
- Preprocessed texts:
  * Removed stopwords, special characters, and punctuation
  - Tokenized before feeding into BERT configuration
  * Obtained pooled output from multilingual BERT model, passed through a linear layer of 128 neurons
- Merged transformer outputs into a single layer with 256 neurons and ReLU activation function
- Dropout applied for final neuron determining class (Troll or Non-Troll)

**Training:**
- Learning rate: 2e-05
- Batch size: 16
- Maximum length of captions truncated to 128 characters
- Training for 4 epochs with linear schedule and warmup

**Results:**
- Model learned quickly, achieving good progress on validation set
- Merging outputs from different domain models helped in getting better results.


## 6 Results

**Results:**
- Achieved overall F1-score of 0.96 using ViT for image classification
- Using mBERT based on captions achieves 0.93 as F1-score
- Baseline scores were 0.59 mentioned in dataset paper
- Concatenating and feeding both representations into a linear layer could lead to better learning
- Model achieves perfect 1.00 weighted F1-score on validation set
- Preprocessing of images was a major factor for achieving great F1-score on validation set
- System performed poorly on test set due to inconsistency with training data in text positioning on images.

**Confusion Matrix:**
- Validation set: Figure 2(a)
- Test set: Figure 2(b)


## 7 Conclusions

**Conclusions**
- Proposed solution outperforms on validation set
- Validation set mirrors train set in distribution of classes
- Dataset is small, augmenting it won't help optimally
- Algorithm overfits the train set
- Poor performance due to change in distribution
  - Test set memes had multiple images difficult for ViT to capture features
- Model scored:
  - F1 score of 0.46 on test set
  - 1.0 on validation set
- Vast difference between scores due to high bias

**Innovation**:
- Transformer-transformer architecture achieves extreme results
- Future work:
  - Perform task of having more transformers in parallel computation
  - Syncing them makes a significant difference in deep learning era.


---

Thank you to arXiv for use of its open access interoperability.
