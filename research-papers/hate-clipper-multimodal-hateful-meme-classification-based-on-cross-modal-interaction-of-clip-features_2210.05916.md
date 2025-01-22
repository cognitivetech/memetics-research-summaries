# Hate-CLIPper: Multimodal Hateful Meme Classification based on Cross-modal Interaction of CLIP Features

[Hate-CLIPper: Multimodal Hateful Meme Classification based on Cross-modal Interaction of CLIP Features](https://arxiv.org/abs/2210.05916)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Methodology](#3-methodology)
- [4 Experimental Results](#4-experimental-results)
- [5 Interpretability](#5-interpretability)
- [6 Conclusion](#6-conclusion)
- [7 Limitations](#7-limitations)

## Abstract

**Hateful Meme Classification using Hate-CLIPper**

**Background:**
- Hateful memes on social media: growing concern
- Individual image or text may not convey same meaning as meme
- Multimodal pre-training beneficial for detecting hateful memes
  - Captures relationship between image and text
  - Represents them in similar feature space

**Proposed Approach:** Hate-CLIPper architecture
- Explicitly models cross-modal interactions between image and text representations
- Uses Contrastive Language-Image Pre-training (CLIP) encoders
- Feature Interaction Matrix (FIM) for modeling interactions
  - Simple classifier based on FIM representation achieves state-of-the-art performance:
    - Hateful Memes Challenge (HMC) dataset: AUROC of 85.8
      * Human performance: 82.65%
- Applicable to other datasets: Propaganda Memes, TamilMemes
- Interpretability analysis of FIM representation

**Key Components:**
1. **Multimodal Pre-training**: Beneficial for detecting hateful memes due to its ability to capture the relationship between image and text.
2. **Intermediate Fusion**: Essential for modeling interactions between image and text features.
3. **Hate-CLIPper Architecture**: Explicitly models cross-modal interactions using CLIP encoders and a feature interaction matrix (FIM).
4. **Feature Interaction Matrix (FIM)**: Represents the interactions between image and text features, which is used for hateful meme classification.
5. **Contrastive Language-Image Pre-training (CLIP) Encoders**: Used in Hate-CLIPper architecture to obtain the image and text representations.
6. **Classifier**: Based on FIM representation achieves state-of-the-art performance for hateful meme classification.
7. **Datasets**: Hateful Memes Challenge (HMC), Propaganda Memes, TamilMemes.
8. **Interpretability Analysis**: Performed to understand the meaning of cross-modal interactions in FIM representation.


## 1 Introduction

**Introduction:**
- Multimodal memes: images overlaid with text spreading on social media (Kiela et al., 2020)
- Some can represent hate speech, impossible to manually detect (Kiela et al., 2020)
- Automated detection challenging due to multimodal nature (Kiela et al., 2020)

**Hateful Memes Challenge (NeurIPS 2020):**
- Focus on identifying multi-modal hateful memes
- Memes curated with non-hateful "confounders" in image or text

**Multimodal Machine Learning Models:**
- Required for robust and accurate detection of hateful memes
- Fusion of different modalities can occur at various levels: early fusion, late fusion

**Early Fusion:**
- Raw inputs combined and joint representation learned (Kiela et al., 2019; Lu et al., 2019; Li et al., 2019)
- Not optimal for hateful meme classification due to text's role as image caption violation

**Late Fusion:**
- End-to-end models for each modality, outputs combined (Kiela et al., 2020)
- Text in a meme doesn't play the role of an image caption

**Intermediate Fusion and Multimodal Pretraining:**
- Image and text features related via common attributes
- Existing intermediate fusion methods: ConcatBERT (Kiela et al., 2020)
- Need to align image and text features through multimodal pretraining

**Contributions:**
1. Propose an architecture called Hate-CLIPper for multimodal hateful meme classification using intermediate fusion of aligned image and text representations obtained using the multimodally pretrained Contrastive Language-Image Pretraining (CLIP) encoders (Radford et al., 2021).
2. Utilize bilinear pooling (outer product) for intermediate fusion of image and text features in Hate-CLIPper, which explicitly models correlations between dimensions of the image and text feature spaces. This representation is called Feature Interaction Matrix (FIM).
3. Demonstrate that a simple classifier with few training epochs is sufficient to achieve state-of-the-art performance for hateful meme classification on three benchmark datasets without any additional input features like object bounding boxes, face detection, and text attributes.
4. Showcase the interpretability of FIM by identifying salient locations in the FIM that trigger the classification decision and clustering the resulting trigger vectors to facilitate learning of meaningful concepts.


## 2 Related Work

**Hateful Memes Challenge (HMC)**
- Established benchmark dataset for hateful meme detection
- Evaluated human performance vs unimodal and multimodal ML models

**Unimodal Models**:
- **Image-Grid**: Based on ResNet-152 features
- **Image-Region**: Based on Faster RCNN features
- **Text-BERT**: Based on original BERT features

**Multimodal Models**:
- **Concat BERT**: Uses multilayer perceptron classifier with concatenated ResNet-152 (image) and BERT (text) features
- **MMBT**: Models with Image-Grid and Image-Region features
- **ViLBERT**:
- **VisualBERT**:

**Performance Gap**:
- Large performance gap between humans (AUROC of 82.651) and best baseline using Visual BERT (AUROC of 75.44)

**Top Submissions**:
- All top 5 submissions achieved better AUROC than baseline methods
- Use of ensemble models and external data/additional input features contributed to improvement

**Extended HMC Dataset**:
- Added ﬁne-grained labels for protected category and attack type
    - Protected categories: race, disability, religion, nationality, sex, empty protected category
    - Attack types: contest, mocking, inferiority, slur, exclusion, dehumanizing, inciting violence

**Multimodal Models**:
- **CLIP Encoders**: Obtain image and text features, concatenated and passed to logistic regression classifier
    - Separate classifiers for protected categories and attack types
- **MOMENTA**: Augments CLIP encoder representations with object/face VGG-19 and text DistilBERT features, uses cross-modality attention fusion (CMAF)

**Bilinear Pooling**:
- Shown to improve performance for multimodal tasks, but not well experimented with multimodally pretrained encoders like CLIP


## 3 Methodology

**Methodology**
- Develop a simple end-to-end model for hateful meme classification
- Avoid sophisticated ensemble approaches and external data/labels
- Hypothesis: Rich information available in CLIP visual and text representations, failure to model interactions adequately
- Propose **Hate-CLIPper architecture** (Figure 2)

**Architecture Components:**
- Pretrained CLIP image and text encoders
- Trainable projection layers at output of CLIP encoders
- Feature interaction matrix (FIM) to model interactions between projected image and text feature spaces
- Customized trainable projection layers after CLIP encoders

**Training:**
- Use pretrained CLIP models trained on 400 million <image, text> pairs from the Internet
- Add trainable projection layers based on given datasets
- Projection layers map unimodal image and text features to corresponding image projection `pi` and text projection `pt`, both with the same dimensionality `n`
- Key difference: Customized trainable projection layers after CLIP encoders

**Modeling Full Cross-modal Interactions:**
- Explicit modeling of interactions between projected image and text feature spaces using FIM
- Obtain FIM representation by computing outer product of `pi` and `pt`
- Flatten FIM to vector of length `nn2`, passed through learnable neural network classifier
- Different from traditional concatenation (Concat) technique, which simply concatenates representations

**Modeling Reduced Cross-modal Interactions:**
- Limitations of cross-fusion approach: high dimensionality, requires larger classifier with more parameters
- Diagonal elements of FIM represent element-wise product between `pi` and `pt`, indicate alignment between dimensions
- Vector representing diagonal elements can still be useful for classification as encoders are pretrained with alignment task
- Refer to fusion using only diagonal elements of FIM as "align-fusion"

**Classification Module:**
- Output of intermediate fusion module is a vector `r` of dimension `d` (baseline: `2n`, cross-fusion: `nn2`, align-fusion: `n`)
- Shallow neural network with pre-output layers and softmax output layer to obtain final output `o`
- First layer maps input `r` with dimensions `ddimensions` to common pre-output dimension `m`
- Each fully-connected layer follows ReLU activation and trained with dropout
- Optimize trainable (projection and pre-output) layers by minimizing binary cross-entropy loss for binary classification (hateful vs. non-hateful memes)
- For fine-grained classification, add auxiliary output layers and train using total loss for all classiﬁcation tasks.


## 4 Experimental Results

**Datasets Used:**
- HMC dataset: contains 8500 memes in training set, 500 in development seen split, 540 in development unseen split, 1000 in test seen split, and 2000 in test unseen split.
- Propaganda Memes dataset: multi-label multimodal dataset with 22 propagandist classes.
- TamilMemes dataset: dataset for troll/non-troll classiﬁcation of memes in the Tamil language, has meme images and corresponding transliterated meme texts.

**Evaluation:**
- **Setup**: Trained Hate-CLIPper and baselines (concat fusion and attention-based CMAF) on the train split and evaluated them on dev-seen and test-seen splits of the HMC dataset using AUROC as the evaluation metric.
- For Propaganda Memes and TamilMemes datasets, used micro F1 score as the evaluation metric for fair comparison with results reported in literature.
- Used PyTorch on NVIDIA Tesla A100 GPU and TorchMetrics library to compute all evaluation metrics.

**Findings:**
- Performance of intermediate fusion with CLIP encoders is better than several early and late fusion approaches such as MMBT, ViLBERT, Visual BERT, and concat fusion on the HMC dataset.
- Cross-fusion and align-fusion variants of Hate-CLIPper achieve the best AUROC for both evaluation sets of the HMC dataset, which is also better than human performance.
- Align-fusion performs significantly better than concat-fusion with 2multimodal features, indicating the importance of pre-aligned image and text representations of CLIP.
- A single projection layer for each modality and a shallow neural network (1 or 3 layers) for classifier is sufficient to achieve good performance.
- The proposed approach outperforms CMAF scheme used in MOMENTA, especially when additional information is available.

**Multilinguality:**
- For TamilMemes dataset, results are not directly comparable due to differences in test sets and encoders used (CLIP vs multimodal pretraining with CLIP loss).
- Replacing CLIP text encoder with multilingual BERT did not lead to performance improvement due to feature space misalignment caused by lack of multimodal pretraining using image and Tamil text pairs.


## 5 Interpretability

**Interpretability of Feature Interaction Matrix (FIM)**

**Computing Trigger Vectors**:
- Compute n2-dimensional binary trigger vector for each hateful meme
- Cluster these trigger vectors using K-means clustering algorithm
- Manually examine clusters to determine common underlying pattern

**Computing Trigger Vector (D, R, T)**:
- Reset feature interaction matrix R to zero values
- Evaluate gradient of loss function for non-hateful class with respect to R
- Denote the model-specific gradient matrix as D
- Binarize D by setting top-20 and bottom 20 percentiles to 1, others to 0
- Perform forward pass through Hate-CLIPper for each hateful meme to obtain FIM R
- Binarize R by setting top-10 and bottom-10 percentiles to 1, others to 0
- Compute trigger matrix T as element-wise product of binarized D and R matrices
- Flatten T to obtain the trigger vector for a meme

**K-means Clustering**:
- Apply K-means clustering algorithm on trigger vectors to group hateful memes
- Examine clusters to identify common underlying patterns

**Observations from Clusters**:
- Some clusters contain memes related to the same concept (e.g., death) in different modalities
- Clusters may also include unrelated memes, or have less than 3 or more than 10 memes, which are not useful for explanation.


## 6 Conclusion

**Hate-CLIPper: A Simple End-to-End Architecture for Hateful Meme Classification**

1. Intermediate fusion and multimodal pretraining importance
2. Proposed model: Hate-CLIPper
3. Uses explicit cross-modal CLIP representations
4. State-of-the-art performance in 14 epochs, 4 trainable layers (1 image projection, 1 text projection, 1 pre-output, and 1 output)
5. No additional input features like bounding boxes or face detection required
6. Successful classification on Hateful Memes Challenge dataset
7. Similar performance in multi-label classification for Propaganda Memes dataset
8. Preliminary interpretability studies of cross-modal interactions


## 7 Limitations

**Limitations of Hateful Meme Classification**

**Ethical Perspective**:
- Subjectivity of defining "hate speech"
- Difficulty drawing clear line between hateful and non-hateful content

**Technical Challenges**:
- Accuracy of hateful meme classifiers is still subpar on benchmark datasets
- Impedes real-world deployment

**Limitations of Hate-CLIPper Framework**:
- Handling high dimensionality of feature interaction matrix is computational challenge
  - Requires model with billion parameters (O(n2m))
  - Align-fusion approach performs close to cross-fusion, requiring only O(nm)parameters
- CLIP encoders used are well-trained on massive English dataset
  - Rarely available for low-resource languages, limiting direct applicability
- Misaligned text and image feature spaces in multilingual experiment
  - More thorough ablation studies needed to understand ability of projection layers to overcome misalignment
- Proposed approach for interpretability is simple and ad-hoc
  - Need more systematic evaluation of explainability
- Fine-grained labels not utilized for FIM interpretation (Mathias et al., 2021)


---

Thank you to arXiv for use of its open access interoperability.