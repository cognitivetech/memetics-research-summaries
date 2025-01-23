# Feels Bad Man: Dissecting Automated Hateful Meme Detection Through the Lens of Facebook's Challenge

[Feels Bad Man: Dissecting Automated Hateful Meme Detection Through the Lens of Facebook's Challenge](https://arxiv.org/abs/2202.08492)

## Table of Contents
- [Feels Bad Man: Dissecting Automated Hateful Meme Detection](#feels-bad-man-dissecting-automated-hateful-meme-detection)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 Datasets](#3-datasets)
- [4 Experimental Setup](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Related Work](#6-related-work)
- [7 Conclusion](#7-conclusion)
- [A Feature Importance & Virality](#a-feature-importance-virality)

## Feels Bad Man: Dissecting Automated Hateful Meme Detection

**Feels Bad Man: Dissecting Automated Hateful Meme Detection**

**Background**:
- Internet memes are a dominant method of communication
- Increasingly used to advocate extremism and foster derogatory beliefs
- Lack of understanding on perceptual aspects causing this phenomenon

**Research Goals**:
- Assess effectiveness of current state-of-the-art multimodal machine learning models for hateful meme detection
- Determine importance of multimodality, influence of fringe Web communities, and learning transferability on social platforms

**Methodology**:
- Use two benchmark datasets: 12,140 images from 4chan's "Politically Incorrect" board (/pol/) and Facebook’s Hateful Memes Challenge dataset
- Train with competition's top-ranking machine learning models to discover most prominent features distinguishing viral hateful memes from benign ones

**Findings**:
- **Memes' image characteristics provide greater wealth of information than textual content**
- Current systems developed for online detection of hate speech in memes necessitate further concentration on visual elements to improve interpretation of underlying cultural connotations
- Multimodal models fail to adequately grasp the intricacies of hate speech in memes and generalize across social media platforms.


## 1 Introduction

**Social Networking Sites and Hateful Memes**

**Impact of Social Networking Sites:**
- Facilitated communication among users worldwide
- Formation of online communities based on shared values
- Continuous change in discourse methods, including use of memes to spread hateful beliefs

**Hateful Memes and Internet:**
- Increasing interest in managing problem of hate speech in multimodal memes
  - Hateful Memes Challenge launched by Facebook AI in 2020
- Quick comprehension and virality of image memes due to human brain's ability to interpret them quickly (13 ms)
- Circulation influenced by various social platforms

**Research Questions:**
1. Significance of multimodality in image memes?
2. Portability of models trained on Facebook’s challenge dataset to other social platforms?
3. Characteristics of hateful viral memes?

**Methodology:**
- Four experiments using Vision and Language (V&L) machine learning models
  - Evaluating potency of multi-modal classifiers for viral hateful memes
- Three datasets used: Kiela et al.’s challenge dataset, Zannettou et al.’s dataset from /pol/, Facebook's Hateful Memes Challenge
- Analysis of visual attributes with most influential impact on classification accuracy.

**Findings:**
1. Visual characteristics offer a wealth of information for communicating intended meaning without text
2. Hateful Memes Challenge dataset not adequately representative for detection algorithms, as demonstrated by second experiment's results
3. Four principal characteristics associated with virality in hateful memes: subject matter, facial expressions, gestures, and proportion.

**Note**: Definition of hate speech: "speech or expression that denigrates a person or persons on the basis of (alleged) membership in a social group identified by attributes such as race, ethnicity, gender, sexual orientation, religion, age, physical or mental disability, and others." [18]

**Caution**: This paper contains uncensored hateful images which may be disturbing to some readers.


## 2 Background

**The Hateful Memes Challenge**
- Launched by Facebook AI to support development of autonomous systems for recognizing harmful multimodal content [7]
- Proposed challenge set comprised of **multimodal memes** conveying hateful or non-hateful messages
- Difficult for unimodal classifiers due to "benign confounders" - samples containing contradictory meanings through their modalities

**4chan**
- Anonymous image-sharing board
- Recognized for users' radical opinions and influence on other social media sites
- **/pol/** board: Harbors content promoting far-right, misogynistic, and transphobic views [11, 25]
- Sparked widespread controversy, e.g., 2016 US presidential elections - /pol/ created antisemitic memes to advance white supremacy agenda
- Many hateful viral memes trace back to 4chan as their source of origin [24]


## 3 Datasets

**Datasets Used in Experimentation:**
* **10,567 images collected by Ling et al.**: 
  * Hateful or non-hateful
  * Multimodal and unimodal samples from 4chan
* **Hateful Memes Challenge dataset by Kiela et al.**:
  * Multimodal hate speech on Facebook
  * Socio-cultural information through visual modes

**Division of Datasets:**
* Experiments use two sets:
  1. Set 1: Multimodal non-hateful images from Facebook + Hateful images from 4chan (5,481 multimodal non-hateful + 3,442 multimodal hateful) and (5,481 multimodal non-hateful + 2,778 unimodal hateful)
  2. Set 2: Text-based sets for classification (1,001 non-hateful + 750 hateful 4chan images) and another set (1,299 non-hateful + 1,297 hateful 4chan images)

**Preprocessing:**
* Facebook's competition provided .jsonl files for training, validation, and testing
* Extracted text from 4chan image memes using EasyOCR
* Manually corrected errors or slang words that were not entirely captured by EasyOCR.


## 4 Experimental Setup

**Experiment on Multimodal Hateful Memes:**
- **Two cases**: Multimodal Memes and Unimodal Memes
- **Goal**: Test influence of multimodality on model predictability
- **Multimodal Memes**:
  - Dataset: 8,923 image memes with text (balanced distribution)
  - Model: VisualBERT CC ensemble
  - Feature extraction using Detectron and Mask RCNN
  - Hyperparameter Search for optimal parameters
  - Majority vote approach to combine estimations
- **Unimodal Memes**:
  - Dataset: 2,778 hateful image memes without text, 5,481 non-hateful Facebook images with text
  - Model: VisualBERT CC
  - Feature extraction using Detectron and Mask RCNN
  - Hyperparameter Search for optimal parameters
  - Majority vote approach to combine estimations

**Experiment on Facebook Memes:**
- **Goal**: Study influential potential of hateful memes from mainstream social media platforms on smaller Web communities
- **Methodology**: UNITER model trained on Kiela et al.'s dataset and tested on 4chan test set (multimodal, imbalanced class distribution)

**Experiment on Multimodal 4chan Memes:**
- **Goal**: Evaluate classifiability of three models: UNITER, OSCAR, average prediction ensemble
- **Methodology**: Dataset split into training, validation, and testing subsets (70:10:20)
- **Models**: UNITER and OSCAR trained using Detectron for feature extraction
- **Evaluation metrics**: Precision, Recall, F1-Score, AUC-ROC.


## 5 Results

**Effects of Multimodality in Hateful Memes: Results and Analysis**

**Performance Results:**
- **VisualBERT CC classifier**: Higher recall than precision due to training on multimodal samples, specific for V&L tasks
- **UniModal Memes**: Precision greater since all samples contain text leading to higher identification of benign memes
- **ROC Curves:**
  - VisualBERT CC ensemble: AUC score of approximately 0.80, correct discrimination between hateful and non-hateful memes
  - UniModal Memes: Demonstrates images are as meaningful as text in conveying ideology, ROC curve near identical to sub-experiments

**Generalizability of Facebook's Meme Samples:**
- **UNITER**: Poor classiﬁcation performance with near-chance AUC score (0.56), low discriminatory ability between classes
- **ROC Curve**: Indicates inadequate true positive rate for addressing hate speech recognition in multimodal memes

**Evaluating Vision-Language Models on Toxic Viral 4chan Memes:**
- **UNITER, OSCAR, and average-prediction**: AUCs of 0.989, 0.988, and 0.989 respectively
- **Average-prediction ensemble**: Best overall performance with highest recall rate (compared to UNITER and OSCAR)
- **UNITER**: Greater precision (0.979) but inferior recall, impeded by its weak AUC score

**Figure 5:** ROC curves for average-prediction ensemble, UNITER, and OSCAR classifiers.


## 6 Related Work

**Meme Propagation Research:**
* Previous work focused on measuring and tracing meme dissemination on the Web (Zannettou et al., 20XX)
	+ Introduced a custom metric to measure visual similarity between image memes
	+ Studied impact of memes on meme propagation in polarized communities like 4chan’s /pol/, Gab, and The donald
* Indicators of Viral Image Memes (Deza & Parikh, 20XX)
	+ Conducted semantic evaluation of perceptual cues in viral memes
	+ Identified five key attributes that link to virality: 'Animal', 'Synthgen', 'Beautiful', 'Explicit', and 'Sexual'
	+ Each attribute elicits different emotional reactions from viewers, potentially affecting sharing decisions
* Detection of Hateful and Offensive Memes (Kiela et al., 20XX)
	+ Introduced a challenge dataset of 10,000 artificial multimodal memes representative of real ones on social platforms
	+ Annotated as hateful or non-hateful
	+ Used early fusion strategy with transformer models to combine visual elements and textual content for classification
* Novelty: Detection of Hateful Speech in Multimodal Memes (Kiela et al., 20XX)
	+ First work to consider anticipation of hateful content prior to publication - viral hateful memes
	+ Identified limitations in Kiela et al.’s dataset and approaches used by winning contestants of Hateful Memes Challenge.


## 7 Conclusion

**Limitations**
- Study of memes composed of more than a single panel worthy of consideration to understand virality potential (Kiela et al. [12])
- Limited availability of meme datasets for such studies, hoping future work will contribute to development
- Careful creation and scrutiny of train, validation, and test datasets time consuming, reducing sampling diversity
- GPU compatibility issues with learning algorithms from Hateful Memes Challenge necessitate appropriate CUDA versions
- Influence of sociocultural identity on understanding online content challenges interpretation of true intentions of creators

**Main Takeaways**
- Multimodal deep learning approach to determine if advancements made toward hateful meme detection generalize to 4chan and other fringe communities
- Inclusion of text in image memes does not significantly impede spread of extremist views, close classiﬁcation scores obtained on unimodal memes
- Kiela et al.’s challenge dataset [12] does not realistically depict actual memes shared on social media, resulting in incapable learning algorithms for hateful meme detection
- Effectiveness of ensemble V&L classifiers for enhancing detection performance
- First step toward assessing viability of state-of-the-art multimodal machine learning methods to improve creation and deployment of autonomous systems for hate speech detection in memes posted on the Web.


## A Feature Importance & Virality

**Characteristics of Hateful Memes: Formal Analysis**

**Subject Matter**:
- 67% of viral memes in training set and 55% of true positives (TP) depict a character, stereotype representation, caricature, or famous individual
- Images with a primary focus have greater likelihood of becoming viral
- Subjects indicate target audience of hateful meme
- VisualBERT CC classifier predicts 599 and 520 hateful memes from sub-experiment test sets
- Kiela et al.'s dataset shows model performance influenced by racial stereotype portrayals and impactful historical figures

**Facial Expressions**:
- Strongly impacted classiﬁcation decisions made by VisualBERT CC classifier (93.7% of viral hateful memes in training set, 84% of TPs)
- Meme virality influenced by the expression of sentiment to advocate beliefs
- Majority of viral hateful memes depict subjects conveying emotions through facial expressions
- VisualBERT CC model correctly classifies 87% of hateful test samples with this attribute (Figure 9)
- Figure 10: Misclassified samples from Multimodal Memes, from the HM dataset

**Gestures**:
- On par with facial expressions in feature importance for meme virality
- Indicates underlying connotations of an image to change its meaning (Figure 11a)
- Both features used by average-prediction model to produce final prediction based on textual meaning (93.7% and 84% of viral hateful memes possess these traits together)
- VisualBERT CC classifier uses this characteristic to assess each test sample (Figure 11b)

**Proportion**:
- Majority of hateful viral memes with two or more features use close-up shots (70% and 84% of viral hateful memes in training sets, same for TPs made by VisualBERT CC and average-predictions models)
- Memes authors depict full form of image's figure to convey message more clearly through facial emotional expressions and gestures
- The Effects of Multimodality in Hateful Memes show VisualBERT CC model picks up on this feature to distinguish between classes (Figure 13)


---

Thank you to arXiv for use of its open access interoperability.