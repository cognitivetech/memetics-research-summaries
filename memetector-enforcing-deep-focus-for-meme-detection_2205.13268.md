# MemeTector: Enforcing deep focus for meme detection

[MemeTector: Enforcing deep focus for meme detection](https://arxiv.org/abs/2205.13268)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related work](#2-related-work)
- [3 Methodology](#3-methodology)
- [4 Experimental setup](#4-experimental-setup)
	- [4.2 Sample mixing and splitting](#42-sample-mixing-and-splitting)
	- [4.4 Training details](#44-training-details)
	- [5.2 Comparative study](#52-comparative-study)
- [6 Conclusions](#6-conclusions)

## Abstract

**Memetector: Enforcing Deep Focus for Meme Detection**

**Background:**
- Image memes as new media type combining text with images in social media
- Express humour, irony, sarcasm, hate speech or disinformation
- Accurate retrieval essential for understanding cultural and social aspects
- Challenge: machine recognition of image macros due to feature map similarity with complete image macro

**Proposed Methodology: Visual Part Utilization (VPU)**
- Regular images as instances of regular image class
- Initial image memes as instances of image meme class
- Forcing model to concentrate on critical parts characterizing an image meme
- Trainable attention mechanism on top of standard ViT architecture
- Interpretable predictions

**Findings:**
- Several training and test scenarios with web-scraped regular images
- Controlled text presence evaluation for robustness and accuracy
- Light VPU combined with sufficient text presence during training surpasses state of the art.

**Keywords:**
- Meme detection
- Visual Part Utilization (VPU)
- Trainable attention
- Vision Transformer.


## 1 Introduction

**Image Memes**
- Popular means of communication in social media
- Typical form: image macros
  - Images with overlay text at top and/or bottom
  - Used to express concepts, emotions (humor, irony, sarcasm)
- Differences from regular images:
  - Overlay text has specific font size, color, family, position
  - Background image usually has cultural reference or is memorable
- Other meme forms exist: plain text, tweet screenshots, social statement cards, logos
- Adoption of different forms is platform-dependent

**Research on Image Memes**
- Interest in analyzing digital social behavior and trends
- Focus on deep learning models for image meme classification
  - Detection of hateful image memes
- Understudied topic: detecting image memes from regular images

**MemeTector: A Model for Meme Detection**
- Proposed methodology for efficient image meme detection
- Utilizes Visual Part Utilization (VPU) and ViTa architecture
  - Trainable attention mechanism on top of Vision Transformer (ViT)

**VPU: Enhancing Learning with Visual Parts of Image Memes**
- Extract largest part of each image meme instance without text
- Denoted as "visual part" (Vi) of the image meme Mi
  - Background image is a regular image, easily discriminated by humans
  - VPU enhances learning of class distribution subtle peculiarities


## 2 Related work

**Meme Detection Research**:
- Previous studies focus on classifying memes into categories (hateful, offensive)
- Multi-modal nature of image memes treated as a multi-modal analysis problem
- Classification based on sentiment (positive, negative, neutral) and humor type
- Topic of image meme detection not yet extensively researched
- DankMemes dataset [17] released in 2020, but publicly unavailable at the time of writing
- Few recent meme detection methods presented [22,23,24]
- Similar problem of identifying satire images on social media addressed in [18]
- Other attempts exist, but not peer reviewed (GitHub repositories and blog posts)

**Proposed Approach**:
- Utilize visual part of image memes as instances of the regular images class
- Enable:
  - 100% accurate automatic annotation through existing meme classification datasets
  - Creation of a dataset of 40,000 images (twice the size of DankMemes)
- First to employ supplemental attention mechanism on top of ViT architecture for deep focus and interpretability.


## 3 Methodology

**MemeTector's Building Blocks: VPU and ViTa**

**3.1 Visual Part Utilization (VPU)**
- **Extraction:**
  - Locate text elements using TextFuseNet model
  - Keep bounding boxes corresponding to whole words
  - Apply Algorithm 1 to find largest rectangle containing no text
  - Determine width and height of visual part based on image size

**3.1.1 Extraction (VIO):**
- To extract the visual part Vi from an image Mi:
  1. Locate text elements using TextFuseNet model
  2. Keep bounding boxes corresponding to whole words
  3. Apply Algorithm 1 to find largest rectangle that contains no text
  4. Determine width ppW and height ppH of visual part based on image size
  5. Check upper and lower bounds for p, r, and center cR based on image dimensions

**3.2 MemeTector:**
- Enforcing deep focus for meme detection

**Algorithm 1: Visual Part Extraction**
- Input: Mi
- Output: Vi
- Size of Mi (W, H)
- TextFuseNet detection: Bi
- Loop through p and r values to determine width ppW and height ppH for visual part based on image size
- Create rectangle R with dimensions ppW x ppH that covers no text

**3.2.2 Attention Module:**
- ViT lacks attention module combining information from past layers
- Compute compatibility score between y (general representation) and patch embeddings of odd layers fz1 to fn in layer n (L)

**Table 1: Composition Scenarios for Regular Images Class R Construction based on PW and PT.**
| PW | 0%   | 33%    | 67%     | 100%    |
|---|---|---|---|---|
| PT | 0%   | 0%     | 33%     | 67%      |
|     | 100% | 67%    | 33%     | 0%       |
|     | 100% | 100%   | 0%      | 0%       |


## 4 Experimental setup

**Dataset Collection for Meme Detection**

**Merging Existing Datasets**:
- Combine instances from datasets containing image memes and regular images

**Image Meme Class (M)**:
- Hateful Memes Dataset [1]
  - Multimodal dataset for hateful meme detection
  - Contains 10,000 image memes
  - No consideration of hateful nature in analysis
  - Indicative examples: Figure 3 (a)-(c)

**Regular Images Class (R)**:
- **VPU methodology** on Hateful Memes dataset to obtain V
- Part of Google's Conceptual Captions dataset [2]
  - Randomly sampled images
  - Text presence property assessed using TextFuseNet [25]
  - Indicative examples: Figure 3 (d)-(f) and (g)-(i)


### 4.2 Sample mixing and splitting

**Meme Image Dataset Preparation:**
* Consider 10,000 instances from Hateful Memes dataset for M class
* Extract visual parts of image memes, resulting in V set with 9,984 images (discarding overlapping text)
* Mean area fraction of overlapping regions: 64.3%
* Discard same 16 memes from Google's Conceptual Captions dataset to create Rp and R respectively for the same number of instances as V (k=9,984)
* Determine PW and PT percentages for sample mixing in various scenarios Si (Table 1)
* Consider crossed scenarios Si;Sj for model evaluation
* Select 85% training, 5% validation, and 10% test samples for all sets M, V, Rp, Ra
* Construct Rper split with same index split to avoid overlapping visual parts Mi and Vi.

**Meme Detection Approach:**
* Meme detection is a visually driven task
* Critical information in memes lies in font size, color, family, position rather than text content
* Text recognition in image memes or regular images is challenging on its own
* Manual text recognition by humans is unrealistic for automatic meme detection
* Focus on analyzing visual signal only
* Consider state-of-the-art and baseline models from image classification domain as competitive methods: VGG16, ResNet50, EfficientNetB5, ViT7.


### 4.4 Training details

**Training Details for ViT and ViTa**
- Input size: (250x250x3) pixels
- Patch size: 25x25
- Number of patches: N=100
- Projection dimension D: 64
- Transformer encoder layers: L=8
- MSA heads: h=4
- ViTa has 3.4M parameters, trained from scratch like ViT
- Pretrained ImageNet weights used for EficientNetB5, ResNet50, and VGG16 models
- Dense sigmoid activated layer added to the last layer for all models
- Trained for 20 epochs with batch size 64
- AdamW optimizer with weight decay 1e-3 used
- Binary cross-entropy loss function
- First 10% of iterations are linear warm-up steps with learning rate 0 -> 1e-3
- Decaying learning rate as t = (1 + d*t)/(1+0.001*t) where t is the iteration and d=1e-3/20
- Models checkpointed based on validation accuracy

**Preprocessing**
- ViT and ViTa input images normalized to [0,1] then standardized by subtracting mean and dividing by standard deviation per channel (on training set)
- Other models use the standard preprocessing pipeline provided by Keras

**Evaluation**
- Models evaluated on various test settings using binary accuracy metric

**Results: Ablation Study**
- MemeTector performs well in all crossed scenarios between training and test settings, with high accuracy scores (89.0-97.8) and mean of 94.98
- S9=(PW=67%, PT=100%) training scenario provides best performance on average and highest accuracy values in most tests
- S2=(PW=33%, PT=0%) training scenario has high variability in performance, with good results for PT=0% but low results for test scenarios with text presence
- Best performance achieved in (S7,S1) scenario where MemeTector is trained on (PW=67%, PT=33%) and evaluated on (PW=0%, PT=0%)
- Worst performance obtained with (S1,S13) scenario where MemeTector is trained on (PW=0%, PT=0%) and evaluated on (PW=100%, PT=100%)
- Feeding the model with samples of different nature helps it generalize better to easy scenarios, while evaluating it on dissimilar settings leads to lower performance

**Comparison with VPU**
- Table 3 shows MemeTector's performance when trained without and with VPU
- When trained using VPU, MemeTector performs better than competition in 3 out of 4 test scenarios and on average

**ViT vs. ViTa Architecture**
- For ViT, the attention module is discarded and the output y is directly passed to Equation 11
- This changes the size of w1 to R2048xD for ViT compared to ViTa


### 5.2 Comparative study

**MemeTector: Enforcing Deep Focus for Meme Detection**

**Table 3: Impact of VPU Usage on Aggregated Accuracy**
- **VPU max\ni**: accuracy of the model when trained without Si and evaluated on Sj.
- All cases i,j in [10, 13]

**MemeTector's Attention Mechanism**
- Figure 4: Attention plots from MemeTector's trainable attention mechanism.
  - Upper 10: image memes
  - Lower 10: regular images
- Correct predictions for both image memes and regular images.

**MemeTector's Performance**
- **TP**: 877, **FP**: 396, **TN**: 1,454, **FN**: 465
- 73% accuracy
- Reduced performance in uncontrolled and noisy real-world data but still considered successful.

**Indicative Correct and Erroneous Predictions**
- Figure 5 illustrates indicative correct and erroneous predictions from the Twitter images experiment:
  1. **Correctly classiﬁed image meme**: similar format to training samples (Figure 5a)
  2. **Correctly classiﬁed regular image**: no confusion, even with text presence (not shown)
  3. **Misclassified regular image**: contains meme-like overlay text and top text (not shown)
  4. **Misclassified image meme**: two numbers as overlay text, not common in training set (Figure 5g)
  5. **Misclassified image meme**: similar structure to training samples but different font morphology (Figure 5h)
- The model focuses on the fonts for detection in some cases, even when their morphology is different from the training set.


## 6 Conclusions

**MemeTector: Enforcing deep focus for meme detection**

**Introduction:**
- Problem of image meme detection addressed
- Introduction of Visual Part Utilization (VPU) process for creating artificial datasets
- Proposed trainable attention mechanism on top of ViT architecture for improved performance and interpretability
- Findings surpass state-of-the-art performance in meme detection

**Dataset Creation with VPU:**
- Extract visual part of an image meme
- Utilize extracted visual part as instance of regular images class

**MemeTector:**
- Classifies Twitter images as memes or regular images
- Examples of correct and incorrect predictions provided in Figure 5

**Declarations:**
- No competing interests declared that are relevant to the content of this article
- Partially funded by Horizon 2020 European project MediaVerse under grant agreement no. 957252

**Data Availability:**
- All datasets used in this work are publicly available and properly referenced in the text

**References:**
1. Kiela et al., "The hateful memes challenge: Detecting hate speech in multimodal memes" (2020)
2. Sharma et al., "Conceptual captions: A cleaned, hypernymed, image alt-text dataset for automatic image captioning" (2018)
3. He et al., "Massive meme identification and popularity analysis in geopolitics" (2019)
4. Olivieri et al., "What is a meme, technically speaking?" (2022)
5. Segev et al., "Families and networks of internet memes: The relationship between cohesiveness, uniqueness, and quiddity concreteness" (2015)
6. Zannettou et al., "On the origins of memes by means of fringe web communities" (2018)
7. Xie et al., "Visual memes in social media: Tracking real-world news in YouTube videos" (2011)
8. Dancygier and Vandelanotte, "Internet memes as multimodal constructions" (2017)
9. Afridi et al., "A multimodal memes classiﬁcation: A survey and open research issues" (2021)
10. Amalia et al., "Meme opinion categorization by using optical character recognition (OCR) and naïve Bayes algorithm" (2018)
11. Smitha et al., "Meme classiﬁcation using textual and visual features" (2018)
12. Gaurav et al., "A machine learning method for recognizing invasive content in memes" (2020)
13. Aggarwal et al., "Two-way feature extraction using sequential and multimodal approach for hateful meme classiﬁcation" (2021)
14. Kiela et al., "The hateful memes challenge: Competition report" (2021)
15. Zhou et al., "Multimodal learning for hateful memes detection" (2021)
16. Khedkar et al., "Hateful memes, offensive or non-offensive!" (2022)
17. Miliani et al., "DANKMEMES @ evalita 2020: The memeing of life: Memes, multimodality and politics" (2020)
18. Sinha et al., "Unsupervised approach for monitoring satire on social media" (2019)
19. Dosovitskiy et al., "An image is worth 16x16 words: Transformers for image recognition at scale" (2021)
20. Shrestha and Rusert, "NLP_UIOWA at SemEval-2020 Task 8: You’re not the only one cursed with knowledge - multi branch model memotion analysis" (2020)
21. Fiorucci, "SNK @ DANKMEMES: Leveraging pretrained embeddings for multimodal meme detection" (2020)
22. Chakravarthi et al., "Multimodal meme dataset (MultiOFF) for identifying offensive content in image and text" (2020)
23. Setpal and Sarti, "ArchiMeDe @ DANKMEMES: A new model architecture for meme detection" (2020)
24. Vlad et al., "UPB @ DANKMEMES: Italian memes analysis - employing visual models and graph convolutional networks for meme identiﬁcation and hate speech detection" (2020)
25. Ye et al., "TextFuseNet: Scene text detection with richer fused features" (2020)
26. Jetley et al., "Learn to pay attention" (2018)
27. Vaswani et al., "Attention is all you need" (2018)
28. Ba et al., "Layer normalization" (2016)
29. Simonyan and Zisserman, "Very deep convolutional networks for large-scale image recognition" (2015)
30. He et al., "Deep residual learning for image recognition" (2016)
31. Tan and Le, "Efﬁcientnet: Rethinking model scaling for convolutional neural networks" (2019)
32. Loshchilov and Hutter, "Decoupled weight decay regularization" (2019)

