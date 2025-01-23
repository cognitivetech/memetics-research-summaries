# MemeFier: Dual-stage Modality Fusion for Image Meme Classification

[MemeFier: Dual-stage Modality Fusion for Image Meme Classification](https://arxiv.org/abs/2304.02906)

## Table of Contents
- [MEMEFIER: DUAL-STAGE MODALITY FUSION FOR IMAGE MEME CLASSIFICATION](#memefier-dual-stage-modality-fusion-for-image-meme-classification)
- [1 Introduction](#1-introduction)
- [2 Related work](#2-related-work)
- [3 MemeFier](#3-memefier)
- [4 Experimental setup](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Conclusions](#6-conclusions)

## MEMEFIER: DUAL-STAGE MODALITY FUSION FOR IMAGE MEME CLASSIFICATION

**MemeFier: Dual-Stage Modality Fusion for Image Classification**

**Authors**:
- Christos Koutlis
- Manos Schinas
- Symeon Papadopoulos

**Affiliation**:
- CERTH-ITI, Thessaloniki, Greece
- {ckoutlis, manosetro, papadop}@iti.gr

**Abstract**:
- **Hate speech** is a societal problem that has significantly grown through the Internet.
- New forms of digital content like **image memes** have made it more difficult to analyze and detect compared to unimodal cases.
- Accurate automatic processing, analysis, and understanding of this content can help hinder hate speech proliferation in the digital world.
- The authors propose **MemeFier**, a deep learning-based architecture for fine-grained classification of Internet image memes, utilizing a **dual-stage modality fusion module**:
  - The first fusion stage produces feature vectors containing **modality alignment information** that captures non-trivial connections between the text and image of a meme.
  - The second fusion stage leverages the power of a Transformer encoder to learn **inter-modality correlations** at the token level and yield an informative representation.
  - The approach considers **external knowledge** as an additional input, and **background image caption supervision** as a regularizing component.
- Extensive experiments on three widely adopted benchmarks (Facebook Hateful Memes, Memotion7k, MultiOFF) indicate that the approach competes and in some cases surpasses state-of-the-art. The code is available on GitHub.

**Keywords**:
- Multimodal hate detection
- Meme classification
- Meme sentiment classification


## 1 Introduction

**MemeFier: Dual-Stage Modality Fusion for Image Meme Classification**

**Introduction**:
- Expressing emotions and opinions through image memes is common in digital world
- Memes can be used to spread hate, cyberbullying due to large scale of daily uploads
- Research community has developed mechanisms for automatic detection and classification of image memes

**Challenges**:
- Image meme classification is multimodal, requiring understanding of both textual overlay and background image
- Interpretation of textual part tied to visual part, making it hard to address fully automatically

**Proposed Approach: MemeFier**
- Deep learning-based architecture with dual-stage modality fusion module
- First stage: estimate level of alignment between modalities through element-wise multiplication of pre-trained representations
- Second stage: Transformer encoder processes alignment-aware features, estimating intra- and inter-modality associations using multihead softmax attention mechanism
- Consider external knowledge as input and caption supervision relevant to background image as regularizing factor

**Conclusion**:
- MemeFier is proposed to tackle the challenges of image meme classification by utilizing dual-stage modality fusion.


## 2 Related work

**MemeFier: A Method for Image Meme Classification**

**Background:**
- Several recent papers address meme classification, pushing forward state-of-the-art on benchmarks like Memotion7k, Facebook Hateful Memes, and MultiOFF.
- Techniques used include t-SNE for cluster detection, CCA and variants for modality interrelationship study.
- Multimodal fusion approaches: early (embedding concatenation or sum/average), late, hybrid, gated multimodal unit, multihead softmax attention, low-rank factorization bilinear pooling, outer product.
- Pretrained representations used: word embeddings (GloVe, FastText, Word2Vec) and large-scale neural networks for text, image, multimodal processing.
- Ensemble approaches with soft voting, majority voting, linear and non-linear prediction models combining ensemble members' predictions.
- External knowledge leveraged: textual and visual sentiment predictions, protected attribute extraction, entity linking (text and image), fine-grained object detection predictions.

**Introducing MemeFier:**
- Proposed method for image meme classification.
- Figure 2 illustrates the proposed architecture.


## 3 MemeFier

**MemeFier's Architecture**
- **Modality encoding**:
    - Use CLIP [34] for image and text embeddings
    - Get image embedding `og2Rd`, patch embeddings `fog_i=12Rng_i=12Rn`
    - Get text embedding `ox2Rd`, token embeddings `fox_i=12Rnx_i=12Rx`
- **External knowledge retrieval and encoding**:
    - Use FairFace [35] for predictions on gender, race, age of persons in image `e2N3_np`
    - Encode this information into embeddings `foe_i=12Rne_d`
- **Fusion**:
    - Dual-stage modality fusion
    - Stage 1: Produce token-level modality representations aware of alignment with other modality
    - Multiply image and text features element-wise to get fused embeddings `fg_i=og_i×ox_i` and `fx_i=ox_i×of_i`
    - Stage 2: Use a Transformer encoder `T()` to process the fused embeddings, along with a learnable classification token CLS
- **Classification**:
    - Use a fully-connected, sigmoid-activated layer for hatefulness output
- **Caption supervision**:
    - To mitigate overfitting of vision encoder, use an additional supervision signal by reconstructing a description of the background image
    - Crop visual part of meme with Visual Part Utilization (VPU) [1]
    - Use Once-For-All (OFA) [36] generated caption as target
    - Use a Transformer decoder to produce the caption based on fused image features `frg_i=1; frx_i=1; fre_i=1`


## 4 Experimental setup

**Datasets:**
* **Facebook Hateful Memes**: Contains 10K memes labeled as hateful or not, split into 8.5K training data, 0.5K validation data (dev), and 1K test data. Evaluated on the dev set due to no test labels.
* **Memotion7k**: Contains 9,871 memes with human annotations for sentiment prediction, overall emotion prediction, and emotion intensity estimation. Includes 1K trial data, 6,992 training data, and 1,879 test data. Sampled 10% from the training set for validation.
* **MultiOFF**: Contains 743 memes manually annotated as offensive or non-offensive. Includes 445 images in the training set, 149 each in the validation and test sets.

**Baselines:**
* Three baselines: Image-only (ResNet18 pretrained), text-only (LSTM), multimodal (combination of image and text).
* Reported results from competitive methods for comparison purposes on each dataset.

**Hyperparameter Tuning:**
* For baselines: Accounted for different initial learning rates, ResNet18 pretraining, hidden dimensions, number of LSTM layers.
* For MemeFier: Initial learning rates, number of epochs, contribution of caption supervision to loss function, model dimension, Transformer encoder and decoder settings.

**Implementation Details:**
* Baselines: Images resized to 256, cropped at 224, horizontally flipped, and standardized using ImageNet statistics. Text preprocessed by lowercasing, removing punctuation, numbers, and double spaces. Vocabulary size determined by occurrence frequency in corpus, maximum sequence length based on 90% quantile of lengths. Binary cross entropy for binary classification tasks, categorical cross entropy for multi-label and multi-class tasks. Adam optimizer with learning rate reduction after epoch 5.
* MemeFier: Same image preprocessing as baselines, vocabulary size determined by approach used for baselines, captions vocabulary includes all words and actual maximum sequence length. Model comprises almost 29M parameters, optimized using Adam optimizer, binary cross-entropy loss for hatefulness output, categorical cross-entropy for caption supervision. Batch size set to 32 with learning rate reduction after half epochs. Losses combined as described in the text.

**Evaluation Protocol:**
* Reported F1 score and accuracy for Memotion7k and MultiOFF datasets, AUC for Facebook Hateful Memes.


## 5 Results

**MemeFier Performance on Facebook Hateful Memes Dataset:**
* **Table 1**: Comparison of MemeFier with state-of-the-art methods on the dev seen split of the Facebook Hateful Memes dataset.
* **Accuracy**: Multimodal baseline outperforms both unimodal baselines.
* **AUC**: Text based approach performs better than image and multimodal approaches.
* State-of-the-art methods exhibit varying performance between 74.1-82.8 AUC, with MemeFier performing comparably at 80.1 AUC.

**MemeFier Performance on Mememotion7k Dataset:**
* **Table 2**: Performance comparison of MemeFier and competitive methods in terms of macro F1 score on Mememotion7k dataset.
* **Accuracy**: Not reported by other papers, but some marginal gains observed with MemeFier.
* The combination of input modalities does not lead to the best results, with one modality dominating over the other.
* MemeFier effectively exploits both modalities and outperforms all baselines and state-of-the-art methods in all tasks (a, b, and c).

**Ablation Analysis of MemeFier:**
* **Table 4**: Performance analysis after removing components one by one.
* All MemeFier components are necessary for the best performance as removing any of them results in reduced accuracy.

**Additional Information:**
* **Table 3**: Comparison of MemeFier and competitive methods on MultiOFF dataset, showing that image surpasses text, with the combination leading to the best outcome both in terms of accuracy and F1 score.
* Proposed method's performance is better than baselines in terms of accuracy while almost identical in terms of F1 score, comparable but lower than state-of-the-art.


## 6 Conclusions

**MemeFier: Deep Learning Method for Fine-grained Meme Classification**

1. **Proposed approach**: MemeFier - deep learning architecture
2. **Dual-stage modality fusion**: Estimate modality alignment at token level (element-wise multiplication) & search input dependencies (Transformer encoder)
3. **External knowledge incorporation**: Use for processing protected attributes of persons
4. **Caption supervision**: Regularization factor - imposes during training
5. **Performance**: Competitive and surpasses state-of-the-art on three meme classification benchmarks.


---

Thank you to arXiv for use of its open access interoperability.