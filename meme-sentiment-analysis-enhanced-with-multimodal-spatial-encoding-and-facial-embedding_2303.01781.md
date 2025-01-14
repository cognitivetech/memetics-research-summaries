# Meme Sentiment Analysis Enhanced with Multimodal Spatial Encoding and Facial Embedding

[Meme Sentiment Analysis Enhanced with Multimodal Spatial Encoding and Facial Embedding](https://arxiv.org/abs/2303.01781)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Works](#2-related-works)
- [3 Methodology](#3-methodology)
	- [3.2 Models](#32-models)
- [4 Results](#4-results)

## Abstract

**Meme Sentiment Analysis:**
* Characterized by interspersing of text amongst visual elements
* State-of-the-art multimodal meme classifiers lack consideration for spatial positioning of elements
* Two datasets used for sentiment classification: Muzhaffar Hazman et al. [0000−0001−8262−2476] and Susan McKeever et al. [0000−0003−1766−2441]
* Performance gains from incorporating spatial position of visual objects, faces, and text clusters:
	+ Improved understanding of latent meaning in memes
	+ Enhanced representation for image processing algorithms
* Facial embedding as an effective enhancement to image representation in multimodal meme classifiers
* Spatial information allows fully automated approaches to outperform human validation baselines.

**Internet Memes:**
- Characterized by text interspersed with visual elements
- Importance of understanding spatial positioning for meaningful interpretation
- State-of-the-art multimodal meme classifiers neglect this aspect
- Two datasets used for sentiment analysis: [0000−0001−8262−2476] and [0000−0003−1766−2441]

**Performance Gains:**
- Incorporating spatial position of visual objects, faces, and text clusters
	+ Improved understanding of meme meaning
	+ Enhanced representation for image processing algorithms
- Facial embedding as an effective enhancement to image representation in multimodal meme classifiers.

**Advantages:**
- Fully automated approaches outperform human validation baselines with the incorporation of spatial information.

**Keywords:**
- Multimodal Deep Learning
- Sentiment Analysis
- Internet Memes.


## 1 Introduction

**Introduction:**
* Sentiment polarity classification: analyze text for sentiment (negative, positive, neutral)
* Extended to multimodal inputs (text, images, etc.)
* Challenging due to brief texts, cultural references, and context dependence
* Importance of meme analysis in opinion mining, hate speech detection, disinformation investigation

**Problem Statement:**
* Given a meme with an image I and text T, classify the meme as Negative, Positive or Neutral.

**Challenges:**
* Text within memes is interspersed into images
* Positioning of words and visual objects crucial for meaning
* Current approaches omit intermodal positional relations

**Proposed Approach:**
* Inject spatial information from both modalities into deep learning classifier
* Account for interspersing of text clusters and visual objects
* Representational overlap on a shared coordinate system (spatial encoding)
* Append spatial encoding to local representations before multimodal fusion and classification.

**Contribution:**
* First work to use shared coordinate spatial encoding and deep representation of faces for meme sentiment classification.


## 2 Related Works

**Meme Classification:**

**Memes vs Other User-Generated Content**:
- Memes have distinct characteristics from other user-generated content:
  - Text and image share a common visual medium
  - Text intentionally located amongst visual content to create meaning
  - Use short text pieces and few foreground visual objects, relying on intermodal relations for meaning
- Meme classifiers must learn subtle intermodal relationships with limited input

**Affective Classification of Memes**:
- Various affective classification tasks can be applied to memes without requiring distinct approaches
- Bucur et al.'s submission to the Memotion Challenge:
  - Trained for sentiment polarity, offensiveness, sarcasm, humor, and motivational intent
  - Suggests meme classifiers exhibit adaptability across different affective computing tasks
- Pramanick et al.:
  - Reported best-performing sentiment classification solution to the Memotion dataset
  - Same architecture outperforms all or all but one competing solutions when trained on eight affect dimensions

**Multimodal Meme Classifier Architecture**:
- Typical approach: Generate unimodal representations of each modality, then fuse these into a multimodal representation of the meme
- Variety of deep learning representations used for visual and textual modalities, with no clear best option

**Positional Encoding in Meme Classification**:
- Positional encoding plays a central role in Transformers architecture and natural language tasks
- However, most multimodal meme classifiers use unimodal encoders, so positions of text and visual elements are encoded separately
- No reported approach uses a shared positional encoding between the text and image modalities on a common spatial coordinate system
- Shang et al. proposed a more general representation of spatial position by appending the spatial encoding of extracted visual objects and text clusters prior to input into an intermodal co-attentive pooling module

**Visual Feature Representations in Meme Classification**:
- Image modality commonly represented by passing entire meme image through an image encoder
- Enhancing this representation with that of extracted visual objects has proven beneficial in classifying hateful memes
  - Inputting the meme image into Google Cloud Vision API's Web Entity Detection to create a description or set of attributes
  - Including Race and Gender tags for each face using a pre-trained FairFace classifier
  - Representing cropped images of visual objects and faces with VGG-19
- Use of faces in sentiment analysis is not new, as facial expressions are valuable mid-level features in classifying the sentiment conveyed by images
- Zhu argues that expecting a global image encoding to sufficiently recognize facial features predictive of hatefulness is unreasonable given the size of current meme datasets


## 3 Methodology

**Methodology**

**Datasets and Feature Extraction**:
- Two competition datasets used: Memotion 1.0 (Memo1) and Memotion 2.0 (Memo2)
- Datasets contain user-generated memes labeled with one of three exclusive sentiment classes
- Text from each meme extracted using automated OCR tool, then manually corrected
- For experiments, samples kept separate without filtering or preprocessing (Original datasets)
- Text clusters, faces, and visual objects localized and represented using tools:
  - Google Cloud Vision
  - EasyOCR
  - CLIP image/text encoders
- Maximum counts of text clusters, visual objects, and faces set to 18, 10, and 5 respectively, with padding used for memes with fewer
- Meme samples filtered to contain identifiable visual objects and text clusters, resulting in Filtered datasets
- Filtered-OCR datasets replace text of each meme with that returned from the feature extraction OCR step

**Multimodal Spatial Encoding in Sentiment Classification**:
- Spatial encoding applied to text features, face features, and object features
- Padding used for memes with fewer features
- Models trained, validated, and tested on the Filtered-OCR datasets


### 3.2 Models

**Models Description:**
- Four models described: Obj-NoSpatial, Obj-Spatial, Face-NoSpatial, Face-Spatial
- Architecture illustrated in Fig. 4
- Built using PyTorch with triangular cyclical learning rate schedule ranging between 1e8 M

**Characteristics:**
- Intermodal Co-Attention module not included in Baseline model
- Attention-based Modality Fusion mechanism used for Baseline and Obj-Spatial, Face-Spatial models
- Dense layers defined as 256, 64, 8, and 1 producing attention scores for each modality
- GeLU-activated dense layer followed by log-softmax activation to output predicted logits of sentiment classes

**Baseline Model:**
- CLIP representations of meme image and text fused using Gu’s attentive modality fusion mechanism
- Trained on Original dataset for performance comparisons with previously published works
- Evaluated on Filtered and Filtered-OCR datasets to measure impact of OCR-based text extraction output on performance

**Obj-NoSpatial and Face-NoSpatial Models:**
- Remove meme image or text, respectively
- Inputs: CLIP-encoded visual objects/faces and text clusters (in case of Obj-NoSpatial) or FaceNet representations of faces (in case of Face-NoSpatial)
- Co-attentive weighted pooling allowing learning attention maps between each modality and text cluster producing one-dimensional vector for each modality

**Obj-Spatial and Face-Spatial Models:**
- Introduce spatial encodings of each text cluster, visual object, and face
- Append spatial encoding to object/cluster/face representation before co-attentive pooling
- Co-attentive analogy alignment module proposed in [12] used for Obj-Spatial and Face-Spatial models instead of simple co-attentive pooling in Obj-NoSpatial and Face-NoSpatial models.

**Img-Obj-Spatial and Img-Face-Spatial Models:**
- Combine CLIP representation of meme image with objects/text clusters (in case of Img-Obj-Spatial) or faces (in case of Img-Face-Spatial)
- GeLU-activated dense layer followed by log-softmax activation to output predicted logits of sentiment classes.

**Table 2:** Goals of each experimental model.
| Model | Dataset | Goal |
|---|---|---|
| Baseline | Original | Benchmarks our chosen modality encodings and fusion mechanism against leading solutions. |
| Filtered | Filtered-OCR | Establishes baseline performance on samples with detectable text clusters and visual objects. |
| Filtered-OCR | N/A | Measures the impact of replacing human-curated text with text clusters returned by automated OCR. Also, establishes a baseline for fully automated approaches. |
| Obj-NoSpatial | Filtered-OCR | Measures the performance of representing the image modality using only CLIP-encoded localised visual objects without spatial encodings. |
| Obj-Spatial | Filtered-OCR | Measures the performance impact of including spatial encodings of objects and text clusters. |
| Img-Obj-Spatial | Filtered-OCR | Maximizes available visual information by augmenting image input with objects, text clusters, and respective spatial encodings. |
| Face-NoSpatial | Filtered-OCR | Measures the performance of representing the image modality using only embeddings of localised faces without spatial encodings. |
| Face-Spatial | Filtered-OCR | Measures the performance impact of including spatial encodings of faces and text clusters. |
| Img-Face-Spatial | Filtered-OCR | Augments image input with faces, text clusters, and respective spatial encodings. |


## 4 Results

**Performance Evaluation of Baseline Model**
* **Baseline model**: Places within top six highest performing solutions on Original datasets (Tables 3 & 4)
* Performance on Original, Filtered, and Filtered-OCR datasets:
  + Lower performance on Filtered dataset due to removal of text on object-less backgrounds
  + Decreased performance on Filtered-OCR compared to Filtered due to lower quality of automated OCR text
* **Spatially aware models**: Able to overcome performance penalty despite lower quality text

**Comparison with Fully Automated Approaches**
* Fully automated models outperform Baseline on each dataset (Table 6)
* Improve feasibility and reduce effort for creating future meme datasets

**Importance of Spatial Encoding in Sentiment Classification of Memes**
* **Spatial encoding**: Improves performance for Obj-Spatial and Face-Spatial compared to respective no-spatial models
* Intermodal spatial information not sufficiently represented by CLIP encodings of whole meme image
* Relevance to other vision-language tasks with shared visual medium

**Performance Differences between Image Modalities and Representations**
* **CLIP-encoded object representation**: Reduction in available visual information leads to worse performance than Baseline
* **Face-NoSpatial**: Outperforms Obj-NoSpatial and Baseline while suffering from similar reduction in visual information
* Mixed results between Obj-Spatial, Face-Spatial, and Baseline depending on dataset

**Augmenting Memes with Local Representations and Spatial Encodings**
* Outperforms models relying only on image or text modality
* Inconsistent performance between CLIP-encoded objects versus FaceNet-encoded faces as augmentations
* Top performing solutions: Img-Obj-Spatial (Memo1) and Img-Face-Spatial (Memo2)

**Conclusions**
* Proposed baseline multimodal classifier ranks within top six of leading state-of-the-art solutions for both datasets
* Representing image modality with visual objects alone does not consistently provide performance benefits, but a face-based representation does
* Incorporation of spatial information grants performance improvements over image-only and faces/objects-only approaches
* Fully automated competitive alternatives proposed for current state-of-the-art solutions that rely on manual validation.

