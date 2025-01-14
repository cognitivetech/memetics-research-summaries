# DisinfoMeme: A Multimodal Dataset for Detecting Meme Intentionally Spreading Out Disinformation

[DisinfoMeme: A Multimodal Dataset for Detecting Meme Intentionally Spreading Out Disinformation](https://arxiv.org/abs/2205.12617)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Dataset](#2-dataset)
	- [2.2 Dataset Construction](#22-dataset-construction)
	- [2.3 Dataset Statistics](#23-dataset-statistics)
- [3 Challenges in DisinfoMeme](#3-challenges-in-disinfomeme)
- [4 Experiments](#4-experiments)
- [5 Related Work](#5-related-work)
- [6 Conclusion](#6-conclusion)
- [A Hyperparameters](#a-hyperparameters)
- [B Details of Dataset Construction](#b-details-of-dataset-construction)

## Abstract

**DisinfoMeme: A Multimodal Dataset for Detecting Meme Intentionally Spreading Disinformation**

**Background:**
- Disinformation is a serious problem on social media
- Memes have significant advantage in dissemination due to short format, visual appeal, and humor
- DisinfoMeme dataset presented to detect disinformation memes

**Dataset Description:**
- Mined from Reddit
- Covers three current topics: COVID-19 pandemic, Black Lives Matter movement, veganism/vegetarianism
- Challenges: limited data and label imbalance, reliance on external knowledge, multimodal reasoning, layout dependency, noise from OCR (Optical Character Recognition)

**Goals:**
- Help detect disinformation memes
- Test various unimodal and multimodal models on this dataset

**Conclusion:**
- Experiments show that current models have room for improvement in handling disinformation memes.


## 1 Introduction

**Disinformation Memes: An Emerging Challenge in Information Dissemination**

**Introduction:**
- Social media facilitates spread of information (Shearer & Gottfried, 2017)
- Rapid spread of inaccurate information is a problem (Broniatowski et al., 2018; Swire-Thompson & Lazer, 2019; Siddiqui et al., 2020; Ferrara et al., 2020)
- Prevalence of memes as vehicles for spreading disinformation

**Defining Disinformation Memes:**
- Image overlayed with text created by Internet users
- Intentionally spreads inaccurate information
- Example: meme about pharmaceutical companies creating diseases (Figure 1)

**Importance of Studying Disinformation Memes:**
- More effective tools for spreading disinformation than pure text (Zannettou et al., 2018; Hameleers et al., 2020; Li & Xie, 2020; Ferrara et al., 2020)
- Limited focus on image-based misinformation detection (Thorne et al., 2018; Zellers et al., 2019b; Bozarth & Budak, 2020; Alam et al., 2021)

**Introduction to DisinfoMeme Dataset:**
- Multimodal dataset for detecting disinformation memes
- Contains 1,170 annotated memes related to COVID-19 pandemic (Pandemic), Black Lives Matter movement (BLM), and Veganism/Vegetarianism (Veganism)
- Includes 30,302 unannotated images for developing unsupervised or weakly supervised learning methods

**Challenges in Studying Disinformation Memes:**
1. Limited data and label imbalance:
   - Disinformation memes are a minority of Internet images
   - Addressed by conducting image retrieval only in meme-prone communities based on disinformation-prone keywords
2. Reliance on external knowledge:
   - Memes refer to popular culture, slang, and current events
   - Understanding requires model to be well-versed in domain-specific knowledge
3. Multimodal reasoning:
   - Combination of text and image requires consideration of both modalities
4. Layout dependency:
   - Memes can be viewed as structured documents
   - Changing the layout breaks semantic meaning
5. OCR noise:
   - Wide range of image styles and varieties in layouts creates difficulty for OCR systems

**Conclusion:**
- Disinformation memes pose a significant challenge in information dissemination
- The DisinfoMeme dataset provides a meaningful and challenging task for vision-and-language models
- Future research encouraged to facilitate advancements in detecting disinformation memes.


## 2 Dataset

**Dataset Overview:**
* Utilizes user content from Reddit
* Retrieves images potentially related to memes from selected subreddits
* Assigns annotation tasks on Amazon Mechanical Turk (MTurk)
* Annotators decide if an image is a topic-related meme and whether it promotes disinformation
* Complies with Reddit's API terms

**Definitions:**
* **Meme**: Image containing superimposed text pieces that require multimodal understanding for full meaning.
* **Disinformation**: Intention to spread inaccurate information, versus misinformation which is false or inaccurate without intent.
* Annotation process: Distinguish disinformation from non-disinformation memes based on user agreement and score calculation (1, 2, or 3)
* Focus on disinformation due to its potential harm
* Utilitarian view towards annotator disagreement: Consider the gradient nature of the problem for effective detection.
* Recall is more important than precision in this task as it concerns false negatives.


### 2.2 Dataset Construction

**Dataset Overview:**
- Contains supervised set and unsupervised set
- Spans three topics: Pandemic, BLM, Veganism
- First two topics are sources of heated debate and disinformation
- Third topic serves as contrast
- Images retrieved from Reddit using PRAW3 for real-time content

**Image Retrieval:**
- Keywords used to find related words
- Queries restricted to subreddits where users post memes
- Human inspection of subreddits for relevance and completeness
- OCR used to extract text from images using Google Cloud Vision API

**Annotation Process:**
1. Workers determine if an image is a meme
2. Memes are classified based on their topic (Pandemic, BLM, Veganism)
3. Workers determine if the meme actively spreads inaccurate information

**Image Processing:**
- Images that pass first two questions enter final step
- Discard images that do not meet criteria

**Dataset Breakdown:**
- Total of 890 non-disinformation memes and 280 disinformation memes in the supervised set (Table 1)
- Significant imbalance between labels, reflecting real-world scenario.


### 2.3 Dataset Statistics

**Dataset Statistics: DisinfoMeme**

* Total: 31,472 images (unsupervised: 30,302, supervised: 1,170)
* Supervised set: 1,170 memes (Pandemic: 980, BLM: 74, Veganism: 116)
* Eliminated: 926 not memes and 171 not topic-related.


## 3 Challenges in DisinfoMeme

**Disinformation Memes Characteristics**

**Limited Data and Label Imbalance**:
- Disinformation memes are hard to find on the internet
- Majority of memes are benign, causing a data scarcity issue
- To obtain disinformation memes, large amounts of annotation are required, leading to a small and imbalanced dataset

**External Knowledge**:
- Internet memes rely extensively on references to popular culture, slang, current events, and domain-specific knowledge
- 70% of the examples in the dataset require external knowledge

**Multimodal Reasoning**:
- Understanding most memes requires multimodal reasoning (vision and language)
- Memes may have a complex referential relationship between text and specific portions of the image

**Layout Dependency**:
- The semantic meaning is dependent on the layout of some memes
- Memes can be viewed as structured documents that require structured modeling

**OCR Noise**:
- Meme images pose a great challenge for OCR systems due to text overlapping with images and watermarks

**Comparison to Hateful Memes**:
- DisinfoMeme poses unique challenges compared to the Hateful Memes dataset in terms of external knowledge, multimodal reasoning, layout dependency, and OCR noise.


## 4 Experiments

**Experiments on DisinfoMeme Detection**
* **Dataset**: Supervised dataset, Pandemic category used for training
* **Evaluation Metrics**: Mean F1 scores, precision scores, ROC AUC
* **Models Tested**: 3 unimodal (Text BERT, Image Grid, Image Region) and 2 multimodal (VisualBERT COCO, VisualBERT HatefulMemes, ViLBERT CC, ViLBERT HatefulMemes)
* **Baselines**: Random Guess, Minority Vote

**Results**
* Models achieve higher recall than precision
* Multimodal models show similar performance as unimodal Text BERT and slightly better in some cases (Table 3)
	+ VisualBERT COCO: F1 = 53.3, ROC AUC = 37.4
	+ ViLBERT CC: F1 = 30.5, ROC AUC = 39.4
* Multimodal information benefits the task but room for improvement is large
* Dataset scalability: Figure 4 shows clear upward trend in both VisualBERT COCO and ViLBERT CC, indicating more gains from more annotated data
* Prior knowledge from Hateful Memes does not significantly benefit the task (Table 3)
	+ VisualBERT HatefulMemes: F1 = 46.2, ROC AUC = 38.1
	+ ViLBERT HatefulMemes: F1 = 51.4, ROC AUC = 40.6
* Limited transferability across topics (Table 4)
	+ None of the models have seen examples under BLM and Veganism topics during training
	+ Models only outperform random guess baseline marginally on these topics.


## 5 Related Work

**Detecting Disinformation: Memes**

**Focus**: Detecting disinformation in memes on the Internet

**Related Research**:
- Text domain research: Pérez-Rosas et al., 2017; Thorne et al., 2018; Zellers et al., 2019b
- Other modalities: Chen et al., 2019a (tables); Wang et al., 2018; Tan et al., 2020; Fung et al., 2021 (images)

**Challenges**:
- Interplay between vision and language: DisinfoMeme is a vision-and-language task
- Grounding to external knowledge: Marino et al., 2019
- Understanding text in visual scenes: Mishra et al., 2019

**Related Work**:
- Hateful Memes (Kiela et al., 2020): unconstrained hate speech detection on the Internet

**Vision-and-Language Models**:
- Long line of work to build models for understanding visual world in natural language
- Tested several widely-used V&L models but they struggle with DisinfoMeme task
- Hope DisinfoMeme can encourage development of new V&L methods: knowledge-enriched, unsupervised/weakly-supervised learning, and models that understand text in images.


## 6 Conclusion

**Multimodal Disinformation Detection in Internet Memes:** An Overview

**Introduction**:
- Dataset for multimodal disinformation detection in internet memes
- Demonstrates potential use as basis for identifying misinformation on social media

**Dataset Description**:
- Aims to inspire future research on new methods for multimodal disinformation detection

**Ethical Considerations**:
- Dataset and models could contain biases
- DisinfoMeme dataset should not be deployed without comprehensive ethical review or human moderation

**References**:

**Survey on Multimodal Disinformation Detection**:
- A survey on multimodal disinformation detection (2021)

**Visual Language Model for Few-Shot Learning**:
- Flamingo: A visual language model for few-shot learning (2022)

**Image Captioning and Visual Question Answering**:
- Bottom-up and top-down attention for image captioning and visual question answering (2018)

**Table-Based Fact Verification**:
- Tabfact: A large-scale dataset for table-based fact verification (2019)

**Universal Encoder for Vision and Language**:
- Unicoder-VL: A universal encoder for vision and language by cross-modal pre-training (2019)

**Pretraining Transferable Visual Models from Natural Language Supervision**:
- Learning transferable visual models from natural language supervision (2021)

**Object-Semantics Aligned Pre-Training for Vision-Language Tasks**:
- Oscar: Object-semantics aligned pre-training for vision-language tasks (2020b)

**Is a Picture Worth a Thousand Words? An Empirical Study of Image Content and Social Media Engagement**:
- Yiyi Li and Ying Xie (2020)

**Common Objects in Context**:
- Microsoft COCO Capions: Data collection and evaluation server (2018)

**Visual Genome: Connecting Language and Vision using Crowdsourced Dense Image Annotations**:
- Visual genome: Connecting language and vision using crowdsourced dense image annotations (2017)

**Internet Meme and Political Discourse**:
- Anushka Kulkarni (2017)

**Babytalk: Understanding and Generating Simple Image Descriptions**:
- Girish Kulkarni et al. (2013)

**Unsupervised Vision-and-Language Pre-Training without Parallel Images and Captions**:
- Liunian Harold Li et al. (2020a)

**Grounded Language-Image Pre-Training**:
- Liunian Harold Li et al. (2021)

**Automatic Detection of Fake News**:
- Auto-nmantic captions: A cleaned, hypernymed, image alt-text dataset for automatic image captioning (2017)

**Learning Transferable Visual Models with External Knowledge**:
- K-lite: Learning transferable visual models with external knowledge (2022)

**“Social Media Misinformation”—an Epidemic within the COVID-19 Pandemic**:
- Mohammed Yaseen Ahmed Siddiqui et al. (2020)

**Multimodal Framework for Vision and Language Research**:
- MMF: A multimodal framework for vision and language research (2020)

**Pythia: A Platform for Vision & Language Research**:
- Pythia: A platform for vision and language research (2018)

**Towards VQA Models that Can Read**:
- Towards vqa models that can read (2019)

**Pretraining of Generic Visual-Linguistic Representations**:
- VL-BERT: Pretraining of generic visual-linguistic representations (2019)

**Defending Against Neural Fake News**:
- Detecting cross-modal inconsistency to defend against neural fake news (2020)

**Fact Extraction and Verification**:
- Fever: A large-scale dataset for fact extraction and verification (2018)

**Gender Bias in Contextualized Word Embeddings**:
- Jieyu Zhao et al. (2019)

**Reducing Gender Bias Amplification using Corpus-Level Constraints**:
- Men also like shopping: Reducing gender bias amplification using corpus-level constraints (2017)

**Unified Vision-Language Pre-Training for Image Captioning and VQA**:
- Uniﬁed vision-language pre-training for image captioning and VQA (2022)

**Multi-Layer Cross-Modal Knowledge Reasoning for Fact-Based Visual Question Answering**:
- Mucko: Multi-layer cross-modal knowledge reasoning for fact-based visual question answering (2020)


## A Hyperparameters

**Experiment Setup:**

- All experiments conducted on a GeForce GTX 1080Ti
- Peak learning rate: 1e-5
- Warmup steps: 20
- Batch size for ViLBERT COCO and ViLERT HM: 16
- Batch size for all other models: 32
- Negative label weight loss: 0.3
- Positive label weight loss: 1
- Based on Velioglu and Rose (2020) with environment adaptations


## B Details of Dataset Construction

**Reddit Data Collection Process**

**First Collection (August 2021)**:
- Conducted in 8 subreddits: meme, memes, dankmemes, Memes_Of_The_Dank, MemeEconomy, okbuddyretard, MemesIRL, TheRightCantMeme
- Additional topic: Afghanistan (subsequently dropped due to potential bias)
- Supervised data only sampled from the first collection

**Annotation Process**:
- Pilot study on 1,000 examples across all topics in October 2021
- Modified annotation process (illustrated in Figure 2) and second annotation of 2,000 Pandemic examples in March 2022
- **Time Keywords**: vaccine, vaccination, Pfizer, Moderna, Johnson & Johnson, AstraZeneca, covid, cdc, Fauci, social distancing, Wuhan, FDA, NIH, Tedros, quarantine, pandemic, bat, SARS, World Health Organization, vegan, vegetarian, PETA, animal rights, animal products, BLM, Black Lives Matter, Antifa, WFH (Work From Home), Afghanistan, Taliban, Kabul

**Second Collection (January 2022)**:
- Conducted in the same 8 subreddits as the first collection
- **Time Keywords**: vaccine, vaccination, Pfizer, Moderna, Johnson & Johnson, AstraZeneca, covid, cdc, Fauci, social distancing, Wuhan, FDA, NIH, Tedros, quarantine, pandemic, bat, SARS, World Health Organization, vegan, vegetarian, PETA, animal rights, animal products, BLM, Black Lives Matter, Antifa, WFH (Work From Home), delta, omicron, variant, booster, shot, dose, mask, anti-vaxxer

**Merging Datasets**:
- Merged the two datasets by selecting images from the first stage using an approach that imitates the final annotation process
- Ensured fairness of payment by determining the reward based on a standard of 12 dollars per hour, without any authors testing the average time used for each assignment.