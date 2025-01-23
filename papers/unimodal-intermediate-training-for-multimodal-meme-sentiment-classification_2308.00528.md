# Unimodal Intermediate Training for Multimodal Meme Sentiment Classification

[Unimodal Intermediate Training for Multimodal Meme Sentiment Classification](https://arxiv.org/abs/2308.00528)

## Table of Contents
- [Unimodal Intermediate Training for Multimodal Meme Sentiment Classification](#unimodal-intermediate-training-for-multimodal-meme-sentiment-classification)
- [1 Introduction](#1-introduction)
- [2 Related Works](#2-related-works)
- [3 Methodology](#3-methodology)
- [4 Results](#4-results)
- [5 Limitations and Future Works](#5-limitations-and-future-works)
- [6 Conclusion](#6-conclusion)
- [Appendix](#appendix)

## Unimodal Intermediate Training for Multimodal Meme Sentiment Classification

**Internet Memes Sentiment Classification: Unimodal Intermediate Training for Multimodal Memes**

**Background:**
- Internet Memes pose a challenge for automated sentiment classification due to the lack of labeled data.
- This study aims to address this issue by supplementing training of multimodal meme classifier with unimodal (image-only and text-only) data.

**Methods:**
- Proposed method uses a novel variant of supervised intermediate training with relatively abundant sentiment-labeled unmodal data.

**Findings:**
- Incorporation of unimodal text data results in statistically significant performance improvement.
- The set of labelled memes can be reduced by 40% without reducing the performance of the downstream model.

**Conclusion:**
- Unimodal intermediate training provides a viable solution to overcome the scarcity of labeled multimodal meme data for sentiment classification.


## 1 Introduction

**Meme Sentiment Classification: A Comparative Analysis**

**Introduction:**
- Increasing popularity of memes in digital communities leads to research interest in multimodal expression analysis
- State-of-the-art classifiers underperform on sentiment classification of memes compared to text and image sentiment classifiers
- Importance of accurately inferring meaning from memes for social media sentiment analysis

**Challenges:**
- Complexity and cultural dependence of memes cause Subjective Perception Problem (Sharma et al., 2020)
- Copyright-protected visual elements complicate data availability
- Trending visual symbols introduce new challenges in labeling

**Data Efficient Methods:**
- Leveraging unimodal sentiment-labelled data for meme sentiment classification using Phang et al.’s (2019) Supplementary Training on Intermediate Labeled Tasks (STILT) approach

**STILT Approach:**
- Load pretrained weights into a classifier model
- Fine-tune the model on an intermediate task with sufficient data
- Fine-tune the model on target, data-scarce meme sentiment classification task

**Previous Findings:**
- STILT improves performance in text-only NLU tasks (Poth et al., 2021; Wang et al., 2019) but inconsistently for different intermediate tasks (Pruksachatkun et al., 2020)

**Proposed Approach:**
- Use unimodal sentiment data as an intermediate task in Text Encoder Pretraining, Image Encoder Pretraining for meme sentiment classification
- Test effectiveness of proposed approach with image-only and text-only 3-class sentiment data (Image-STILT and Text-STILT)

**Research Questions:**
1. Does supplementing multimodal meme classifier training with unimodal sentiment data significantly improve its performance?
2. To what extent can we reduce the amount of labelled memes while preserving the performance of a meme sentiment classifier using unimodal STILT?


## 2 Related Works

**Meme Affective Classifiers:**
* Multimodal deep learning models trained for classifying memes based on affect dimensions like sentiment polarity, offensiveness, motivationality, sarcasm, hate speech, and trolling behavior. (Sharma et al., 2020; Patwa et al., 2022; Mishra et al., 2023; Kiela et al., 2020; Suryawanshi et al., 2020)
* Two general architectural approaches:
  + **Multi-encoder models**: Use multiple pretrained unimodal encoders that are then fused prior to classification. (Sharma et al., 2020; Patwa et al., 2022)
    * Text and image encoders trained in self-supervised and unsupervised tasks like BERT or SentenceTransformer for text, and VGG-19 or RESNET50 for images.
  + **Single-encoder models**: Based on a pretrained multimodal vision-and-language transformer model that accepts both modalities as input. (Muenninghoff, 2020; Zhu, 2020)
    * Uses pretrained models such as VLBERT, UNITER, ERNIE-ViL, DeVLBERT, and VisualBERT.
* No clear evidence to show one architectural approach consistently outperforms the other in various meme classification tasks.
* Both multi- and single-encoder architectures use transfer learning by finetuning pretrained models on labeled memes.
* Pretraining is assumed to yield performance benefits for meme classification tasks, but this has not been exhaustively proven relative to image- and text-only tasks. (Jiang et al., 2022)
* Several recent works have attempted to incorporate external knowledge into meme classifiers:
  + Additional encoders for human faces, entity recognition via a large knowledge base, cross-modal positional information, social media interactions, and image captioning. (Zhu, 2020; Hazman et al., 2023; Pramanick et al., 2021b; Shang et al., 2021; Blaier et al., 2021)
* Lack of studies on whether pretrained representations are suitable for the downstream task or if an encoder's performance in classifying unimodal input transfers to classifying multimodal memes.

**Supplementary Training of Meme Classifiers:**
* Several works addressed the lack of labelled multimodal memes by incorporating additional non-meme data:
  + Self-supervised representation learning approaches to learn semantically rich cross-modal features for various meme affective classification tasks. (Sharma et al., 2022)
    * Finetuned image and text encoders on image-with-caption tweets before fitting the representations on several multimodal meme classification tasks.
    * Performance improvement in some but not all tasks, underperforming in comparison to typical supervised finetuning approaches.
  + Multitask learning approach that simultaneously trained a classifier for multiple meme classification tasks (sentiment, sarcasm, humor, offensiveness, motivationality). (Bucur et al., 2022)
    * Underperformed in binary detection of humour, sarcasm, and offensiveness; only effective in predicting the intensity of sarcasm and offensiveness.
    * Multitask multimodal classifier offers the best reported results on the Memotion 2.0 sentiment classification task to date.
* Inclusion of unimodal inputs to supplement training of multimodal meme classifiers:
  + Unimodal image augmentation improved performance in detecting trolling behavior in Tamil memes (Suryawanshi et al., 2020).
    * Assigned non-meme images as not containing trolling language; found that this augmentation with 1,000 non-meme images decreased the classifier's performance.
    * Both pretrained weight models and multimodal classifiers performed identically to a model that did not use either pretraining or data augmentations.

**Modality Fusion:**
* Dropout & Normalize:
  + Visual Features
  + Textual Features
  + Fused Multimodal Features
  + Dropout & Normalize for each modality separately
* Our model architecture (Figure 2): Adapted from Hazman et al. (2023).


## 3 Methodology

**Methodology**

**Target Task**:
- Chosen task: 3-class sentiment polarity of multimodal memes as defined by Ramamoorthy et al. (2022)
- Dataset: Memotion 2.0 (Ramamoorthy et al., 2022)

**Approach**:
- Experimental approach: Comparing performance of:
  - Baseline model (trained only on memes)
  - Image-STILT model (trained first on unimodal image data, then on memes)
  - Text-STILT model (trained first on unimodal text data, then on memes)
- All models architecturally identical, trained in Memotion 2.0 training set and tested against Memotion 2.0 testing set
- Performance measured using weighted F1-score as defined by Sharma et al. (2022)

**Model Architecture**:
- Based on Baseline model proposed by Hazman et al. (2023)
- Image and text encoders from OpenAI CLIP (Radford et al., 2021) to represent each modality
- Same modality fusion weighting mechanism used in the Baseline model
- Added dropout and batch normalization after encoding and fusion of encodings to prevent overfitting

**Datasets**:
- **Multimodal Memes**: Sentiment-labeled multimodal memes from Memotion 2.0 benchmark dataset as target task
- **Unimodal Images and Texts**: Crowdflower (CrowdFlower, 2016) for unimodal images, DynaSent (Potts et al., 2021) for unimodal text
  - Both datasets contain crowdsourced samples collected from social networking sites with 3-class sentiment labels

**Training**:
- **Baseline**: Model trained on Memotion 2.0 training set, early stopping based on minimum loss on validation set
- **Unimodal STILTs (Image-STILT and Text-STILT)**: Initialization same as Baseline, followed by training model on selected unimodal dataset while freezing encoder of other modality, then evaluated against Memotion 2.0 testing set

**Experimental Approach**:
- **RQ1**: Use Wilcoxon Signed-Rank test to establish if Image-STILT or Text-STILT offer statistically significant performance improvement over Baseline
  - Null hypothesis: No significant difference in performance between Baseline and each STILT variant
  - 10 random restart for each approach, all models trained on Memotion 2.0 training set
- **RQ2**: Train Baseline, Image-STILT, and Text-STILT on varying amounts of training memes to characterize performance benefits with limited availability of labeled memes
  - 5 random restarts for each approach at each training set size, resulting in 45 observations per pair (Baseline vs. Image-STILT, Baseline vs. Text-STILT)
  - Wilcoxon Signed-Rank test across entire range of labelled meme availability, separately for each pair


## 4 Results

**Performance Improvement (RQ1)**
- **Text-STILT outperforms Baseline**: statistically significant improvement as shown in Figure 3 and Table 4
- Text-STILT incorporates supplementary data into multimodal meme classifiers
- Effectiveness not yet understood; posit that longer texts or textual structures hinting at sentiment are more accurately classified

**Limited Labelled Memes (RQ2)**
- **Text-STILT significantly improves performance over Baseline**: across varying amounts of labelled meme availability between 50% and 80%
- Text-STILT outperforms Baseline even with only 60% of available labelled memes (Figure 5)
- No significant improvement in performance for Image-STILT over Baseline across the entire range of meme availability (p-values: 0.667 and 0.985)
- Small difference in performance between Text-STILT and contemporary approaches
- 41% of memes not correctly classified by either Text-STILT or Baseline.


## 5 Limitations and Future Works

**Limitations and Future Work**

**Hyperparameters**:
- Kept constant to generate comparable results between Baseline and Text-STILT
- Additional work required to determine maximum achievable performance of Text-STILT on the chosen task

**Modality Ablation Studies**:
- Previous works performed modality ablation studies with multimodal architectures remaining the state of the practice
- All models in this study are similarly multimodal

**Image-STILT Reformulation**:
- Plan to reformulate Image-STILT with respect to the approach and data used to isolate the cause of its non-performance on the downstream task

**Text-STILT vs. Classifiers**:
- Text-STILT may not benefit all multimodal meme classifiers
- Phang et al. showed STILT offers varying degrees of benefit depending on the encoders chosen
- Future work needed to verify if these observations hold across a wide range of pretrained encoders commonly used in meme classifiers

**Unimodal STILT Modifications**:
- Some modifications to unimodal STILTs are needed to be applied to single-stream multimodal encoders, as those used in other works

**Intermediate Training Benefits**:
- Pruksachatkun et al. showed intermediate training benefits various text-only tasks differently
- Plan to conduct more extensive experimentation to validate the effectiveness of Text-STILT on other meme classification tasks, e.g. pairing hate-speech detection in text with hateful meme detection.


## 6 Conclusion

**Conclusion:**

- Multimodal meme sentiment classification using STILT
  - Incorporated unimodal sentiment analysis data
  - Image-only and text-only sentiment classification as intermediate tasks
  - Improved performance with fewer labeled memes (60%)
- Observations:
  - Similarities and differences between image and text modalities in multimodal vs. unimodal sentiment analysis
- Discussion on the benefits of this novel approach for training meme classifiers.


## Appendix

**Hyperparameters and Settings**
- **Input**: Memes (unimodal)
- **Learning Rate**:
  - Initial: 1.5e−5 to 5e−5, then 5e−6 to 1e−5
- **Max Epochs**: 40 (for unimodal), 60 (for multimodal)
- **Optimizer**: AdamW
- **Betas**: [0.5, 0.9]
- **Weight Decay**: 0.9
- **AMSGrad**: False
- **Dropout Rate**: 0.2
- **Early Stopping**: Per Meme Validation set
  - Min Loss: Max Weighted F1 Score

**Performance Metrics**
- **Metric**: Weighted F1-Score
  - Harmonic mean of precision and recall, equally representing both
  - "Weighted" denotes F1 score computed per class and averaged with class weights

**Architectural Details**
- **Models**: Based on Baseline model proposed by Hazman et al. (2023)
- **Image Encoder (FI)**: Embedding representation of image modality from CLIP
- **Text Encoder (FT)**: Embedding representation of text modality from CLIP
- **Modality Fusion**: Attentive fusion mechanism proposed by Gu et al. (2018)
  - Each modality embedding passed through dense layers with reducing sizes
  - Softmax applied to generate weighted score for each modality

**Model Training**
- **Embedding Representation**: Dropout and normalization added
- **Fusion Mechanism**: Dropout and normalization added
- **Loss Function**: Mean Multiclass Cross Entropy Loss
  - Weighted by (1 - Nyn) / PN, where Nx is the logits for each class and yn is the target label

**Performance Benchmarking**
- Current competing approaches show small spread in Weigthed F1-Scores
- Text-STILT offers similar performance improvement as other SOTA solutions
- Contingency table shows notable differences in correctly classified memes between Baseline and Text-STILT


---

Thank you to arXiv for use of its open access interoperability.
