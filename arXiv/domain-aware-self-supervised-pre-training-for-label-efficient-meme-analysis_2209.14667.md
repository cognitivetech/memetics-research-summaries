# Domain-aware Self-supervised Pre-training for Label-Efficient Meme Analysis

[Domain-aware Self-supervised Pre-training for Label-Efficient Meme Analysis](https://arxiv.org/abs/2209.14667)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Dataset](#3-dataset)
- [4 Proposed Solution](#4-proposed-solution)
- [5 Experiments and Results](#5-experiments-and-results)
	- [5.1 Self-supervised Learning and Linear Evaluation](#51-self-supervised-learning-and-linear-evaluation)
	- [5.2 Label-Efficient Training on Downstream Tasks](#52-label-efficient-training-on-downstream-tasks)
- [6 Impact of Label-Efficient Supervision During Fine-tuning](#6-impact-of-label-efficient-supervision-during-fine-tuning)
- [7 Discussion](#7-discussion)
- [8 Conclusion](#8-conclusion)
- [A Hyperparameters](#a-hyperparameters)
- [B Statistical Analysis of Datasets](#b-statistical-analysis-of-datasets)
- [C Training Characteristics](#c-training-characteristics)
- [D Ethics and Broader Impact](#d-ethics-and-broader-impact)

## Abstract

**Self-Supervised Pre-training for Label-Efficient Meme Analysis**

**Background:**
- Existing self-supervised learning strategies limited to:
  - Limited set of objectives
  - Generic downstream tasks for uni-modal applications
- Isolates progress in imperative multi-modal applications, like meme analysis

**Approach:**
- Introduce two self-supervised pre-training methods: Ext-PIE-Net and MM-SimCLR
  * Use off-the-shelf multi-modal hate-speech data during pre-training
  * Incorporate multiple specialized pretext tasks for effective representation learning

**Contributions:**
- Experiment with different self-supervision strategies, including:
  * Potential variants to learn rich cross-modality representations
- Evaluate using popular linear probing on the Hateful Memes task
  * Strongly compete with fully supervised baseline via label-efficient training
  * Outperform the fully supervised baseline on all three tasks of the Memotion challenge:
    * Performance gain: 18%, 23.64%, and 93% respectively
- Demonstrate generalizability to HarMeme task
- Analyze task-specific learning, using fewer labeled training samples
- Establish relationship between self-supervision strategy complexity and downstream task performance

**Conclusion:**
- Highlights the requirement for better multi-modal self-supervision methods involving specialized pretext tasks for efficient fine-tuning and generalizable performance.


## 1 Introduction

**The Scale of Digital Mutation on the Web**
- **Creates an illusion of reality**, addressing the viewer, and representing a convoluted space (Manovich, 2001)
- Social activities are affected or influenced by online entities, sometimes disrupting social harmony due to:
  - Prominent surge of multi-modal harmful, abusive, and hateful content
  - Need for automatic mediation of online activities involving multi-modality

**Self-Supervision Strategies for Visual-Linguistic Applications**
- Different pretext tasks:
  - **Masked Language Modeling (MLM)**
  - **Masked Region Modeling (MRM)**
  - **Word-Region Alignment (WRA)**
  - **Image-Text Matching (ITM)**
- Large-scale datasets curated towards the required pre-training:
  - MS COCO, Conceptual Captions (CC), Wikipedia-based Image Text (WIT), LAION-400M
- Challenges in creating multi-dimensional and fine-grained manual annotations for large volumes of multi-modal data

**Pre-Training Schemes for Downstream Multi-Modal Tasks**
- Visual BERT, ViLBERT, LXMERT: Pre-trained on pretext tasks like sentence-image prediction, masked multi-modal learning, multi-modal alignment prediction, and detected-label classification
- Requirements:
  - Availability of multiple semantically grounded sentences corresponding to an image
  - Visual-semantic object and pixel-level annotations for the images
- Limitations:
  - Fall short on performance for complex multi-modal tasks like meme analysis
  - Do not represent strong visual-linguistic grounding and require sophisticated multi-modal fusion and contextual knowledge integration

**Proposed Contributions**
1. Propose two self-supervision-based multi-modal pre-training frameworks that learn semantically rich cross-modal features for meme analysis.
2. Establish the effectiveness of the proposed self-supervision frameworks towards adapting to downstream tasks using only a few labeled training samples.
3. Demonstrate the generalizability of the representations learned across tasks and datasets.


## 2 Related Work

**Self-supervised and Semi-supervised Learning:**
* **Self-supervised learning**: optimizes training objectives without explicit labels
* Pretext tasks introduce pseudo-labels: next word prediction (Peters et al., 2018), sentence order prediction (SOP) (Lan et al., 2020)
* Contrastive learning: optimize similarity between positive pairs and reduce it for negative ones (Oord et al., 2018; Chen et al., 2020a)
* Non-contrastive learning: increase similarity with previous augmented views (Grill et al., 2020)
* Multi-modal embedding space learning: capture complex semantics, address non-trivial downstream tasks

**Multi-modal Pre-training:**
* Recent works: Wang et al. (2021), DALL-E (Ramesh et al., 2021), CLIP (Radford et al., 2021)
* Primary objective: learn multi-modal embedding space jointly
* Datasets used for pre-training: too generic to capture complex semantics

**Studies on Memes:**
* Research focus: online hate, harm, offense, abuse (Kiela et al., 2020; Sharma et al., 2020)
* Classification task: Kolawole (2015), linear SVM, low-level descriptors, only visual information
* Meme generation: represent meme image and catchphrase in the same vector space using deep neural networks (Kido Shimomoto et al., 2019; Peirson et al., 2018)
* Human assessment: outperformed random choices but below-par compared to human-produced memes.
* Solicited efforts: achieve richer and more meaningful content modeling for tasks that conventional multi-modal approaches cannot solve.


## 3 Dataset

**Pretraining Dataset:**
- **MMHS150K dataset** (Gomez et al., 2020) used for pretraining:
  * Consists of 150K multi-modal tweets
  * Spans four hate-inclined topics: racism, sexism, homophobia, religious extremism
  * Represents diversity with memes, morphed images, satirical art
* Additional pretraining data from Facebook's Hateful Memes dataset (Kiela et al., 2020):
  * Exclusively for pretraining
  * Contains harmful and not-harmful memes

**Training and Evaluation Datasets:**
- **Hateful Memes**: 3552 memes annotated as harmful or not harmful (Pramanick et al., 2021)
- **Harm-P**: Belongs to HarMeme task, consists of 3552 memes with two labels: harmful and not harmful
- **Memotion**: Approx. 8K memes defining three subtasks: sentiment analysis (positive/negative), emotion classification (happiness/sarcasm/offense/motivational), and emotion class quantification (slightly/mildly/very)

**Dataset Characteristics:**
- **MMHS150K**: Large-scale corpus of multi-modal information, varying complexities
- **Pretraining**: Self-supervised using proposed loss functions based on neural representations only
- **Downstream Tasks**: Adapt to related tasks efficiently with minimal annotations required.


## 4 Proposed Solution

**Multi-Modal Self-Supervision: MM-SimCLR and Ext-PIE-Net**

**Review of SimCLR and Hinge Loss Formulations:**
* **SimCLR (Chen et al., 2020a)**: A popular self-supervision technique that learns representations for images by maximizing agreement between augmented views in a latent space. The objective function is defined as: `LNT-Xent(i;j) = cosine_similarity(p(i), p(j))` where `p(i)` and `p(j)` are the projections for augmented views i and j, respectively; and  temps is temperature.
* **Hinge Loss**: A loss function conventionally used in uni-modal vector space (Rosasco et al., 2003). In a two-modality system with `u` and `v` as modality-specific representations in common space, the multi-modal weighted hinge loss (LwHinge) is formulated using a cosine similarity function `s(.)`: `LwHinge(u;v) = max(0:2) * cosine_similarity(u, v)` where the result is clamped with a ReLU function. The individual terms are weighted by `u2v` and `v2u` before aggregation. This is expressed as:

**Proposed Solutions: MM-SimCLR and Ext-PIE-Net**
* **MM-SimCLR**: A multi-modal variant of SimCLR that utilizes an adaptation of the contrastive loss formulation for learning multi-modal embedding space. It also includes specialized multi-modal pretext tasks for joint representation learning.
* **Ext-PIE-Net**: An extended version of PIE-Net that uses a multi-headed co-attention mechanism and hinge loss calculation.

**Architectures:**
* MM-SimCLR: Multi-modal SimCLR (left)
* Ext-PIE-Net: Extended Pie-Net (right)

**Objective Functions:**
* MM-SimCLR: `L = NX⃝ihf1LNT-Xent(fi;1;fi;2) + f2i⃝ihLwHinge(ii;fi) + f2t⃝ihLwHinge(ti;fi)`
* Ext-PIE-Net: Implemented as shown in the figure.


## 5 Experiments and Results

**Self-Supervision: Evaluation Strategy**
* Presentation of self-supervision strategies evaluation results
* Linear evaluation strategy (Oord et al., 2018) used for assessing quality of representations learned
* Primary focus on multi-modal applications and comparison with state-of-the-art setups
* Emphasis on investigations in the Introduction section
* Comparison restricted to accessible datasets like MMHS150K, pre-trained ViLBERT, and Visual BERT
* Average accuracy values for Hateful Memes task (SL, SSL) and Macro-F1 scores for Memotion and HarMeme tasks reported.

**Self-Supervision: Evaluation Details**
* Self-supervised learning (SL) vs self-supervised learning with fine-tuning (SSL+FT) comparison
* Focus on multi-modal datasets that are conveniently accessible via web
* Linear classifier employed for fair assessment of resulting inductive bias
* Primary evaluation metrics: accuracy values for Hateful Memes task and Macro-F1 scores for Memotion and HarMeme tasks.

**Comparison with State-of-the-Art Setups**
* Comparison with multi-modal state-of-the-art setups
* Evaluation of representations learned through pre-training using linear evaluation strategy.

**Accessible Datasets Used for Comparison**
* MMHS150K: conveniently accessible via web, used for comparison in self-supervision experiments.
* ViLBERT and Visual BERT: fine-tuned versions of these models used for comparison in self-supervision experiments.

**Evaluation Metrics**
* Accuracy values for Hateful Memes task (SL, SSL)
* Macro-F1 scores for Memotion and HarMeme tasks.


### 5.1 Self-supervised Learning and Linear Evaluation

**Self-supervised Learning and Linear Evaluation**

**Experiment Overview**:
- Experiment with related existing approaches
- Compare self-supervised and supervised learning frameworks
- Do not consider pre-trained models like Visual BERT and ViLBERT due to pre-training strategies

**SSL Systems**:
- **SimCLR (Chen et al., 2020a)**: Focuses on agreement between similar image views
- **VSE++ (Faghri et al., 2018)**: Mining hard negatives for heavy penalization
- **Modified SimCLR**: Extending the loss to text modality using WordNet synonyms and back-translation

**Multi-modal Systems**:
- **Late fusion**: Average prediction scores of ResNet-152 and BERT
- **Concat BERT**: Concatenate representations from ResNet-152 and BERT, use perceptron as classifier
- **MMBT**: Multi-modal Bitransformer capturing intra/inter-modal dynamics
- **ViL-BERT CC**: Vision and Language BERT trained on conceptual captions
- **Visual BERT COCO**: Pre-trained using MS-COCO dataset

**Results**:
- SimCLR results in 0.50 accuracy (meager difference from image-only baseline)
- VSE++ yields improved accuracy of 0.53 due to factoring of hard negatives
- Modified SimCLR for textual modality has low accuracies (0.48, 0.45)
- MM-SimCLR enhances performance to 0.5508
- Ext-PIE-Net further enhances it to 0.5998 (+9.98%) over image-only SimCLR
- Proposed solutions incorporate consideration of multiple views and single text representation for specialized multi-modal contrastive learning

**Comparison with Baseline and Previous Best**:
- Performances fall behind fully-supervised counterparts but reasonably better than strong self-supervised methods
- Task-wise Macro-F1 scores: SENT, EMOT, EMOT-Q (Table 2)


### 5.2 Label-Efficient Training on Downstream Tasks

**Label-Efficient Training on Downstream Tasks**

**Self-Supervised Pre-Training Evaluation**:
- Use a subset of labeled samples to assess label efficiency during adaptation
- Linear classification head brings modalities into the same dimension (512)
- Shallow, fully connected network classifies obtained multi-modal representation into target labels
- Evaluate on Memotion and HarMeme tasks

**Memotion Analysis**:
- Baselines and leaderboard reflect non-triviality with SOTA results of 0.354, 0.518, 0.32 (Macro-F1)
- Baseline systems have Macro-F1 scores of 0.217, 0.500, 0.300 (SENT, EMOT, EMOT-Q)
- Previous best systems: word2vec-based feed-forward NN for SENT, multi-modal multi-tasking setup for EMOT, feature-based ensembling for EMOT-Q
- Improvement solicited in multi-modal systems

**Comparison of Proposed Approaches and Baselines on Memotion Tasks**:
- Ext-PIE-Net outperforms Late Fusion, Visual BERT, ViLBERT, previous SL, and uni/multi-modal SSL systems (SENT and EMOT)
    - 1.37% improvement in SENT, 7.93% increment over VSE++ in EMOT
- MM-SimCLR performs better on relatively more straightforward HarMeme task
    - Outperforms other competitive multi-modal baselines (Supervised), SimCLR, and SSL multi-modal baselines (VSE, VSE++)
    - Lags behind strong SL base lines ViLBERT CC, Visual BERT COCO, and MOMENTA

**Harmful Memes**:
- Transferability of pre-trained representations examined by fine-tuning on HarmMeme dataset
- Fully supervised models obtain Macro-F1 scores of 0.8603, 0.8607, 0.8826 (VilBERT CC, Visual BERT COCO, MOMENTA)
- MM-SimCLR performs well in label-efficient setup with 0.8140 Macro-F1
- Ext-PIE-Net performs poorly compared to MM-SimCLR's impressive F1 score of 0.8140
- MM-SimCLR outperforms other competitive multi-modal baselines (Supervised), SimCLR, and SSL multi-modal baselines (VSE, VSE++, Ext-PIE-Net)
- Scope for enhancement in pre-training objectives and frameworks within existing multi-modal systems.


## 6 Impact of Label-Efficient Supervision During Fine-tuning

**Impact of Label-Efficient Supervision During Fine-tuning**

**Comparison of Performances**:
- Ext-PIE-Net converges efficiently to 0.3565 F1 score with 10% (600) labeled samples, compared to MM-SimCLR's 0.3511 F1 score with 50% (3000) labeled samples
- Ext-PIE-Net achieves an overall better F1 score of 0.7547 for EMOT task, compared to MM-SimCLR and other results
- Optimal performance of SimCLR is reasonably at-par or even better for SENT and EMOT tasks, but shows little active convergence

**Label Efficiency Scenarios**:
- VSE yields 3.02% and 7.98% improvement over SL baseline for SENT and EMOT tasks, respectively
- VSE++ fails to register impressive performance compared to the increment of 12.52% and 17.52% for the two tasks, respectively
- Performance curves are depicted for 100 epochs across four different label-efficiency scenarios

**Performance Trends**:
- Ext-PIE-Net shows progressive learning for SENT and EMOT tasks (c.f. Fig. 3)
- MM-SimCLR shows saturated learning for SENT and EMOT tasks (c.f. Fig. 3)
- For HarMeme task, incremental supervision exhibits incremental performance with the increase in the amount of supervision during fine-tuning
- The final F1 score of 0.814 obtained by MM-SimCLR is on just 50% (1510) of the actual training set, demonstrating the efficacy and generalizability of pre-training strategies


## 7 Discussion

**Memotion Dataset Results:**

* Downstream evaluation shows:
  * Ensembling-based methods perform better or
  * Large variations in performance trends
* Complexity correlates with modelling solutions
* Highlighted performances and comparisons for two models (Sharma et al., 2020)


## 8 Conclusion

**Self-Supervised Multi-Modal Learning: Two Strategies**
* **MM-SimCLR**:
  + Multi-modal contrastive loss formulation
  + Factors in loss terms for image modality and multi-modality jointly
* **Ext-PIE-Net**:
  + Joint formulation of weighted modality-specific hinge loss terms
  + Combined with contrastive loss computed between representations obtained using symmetric multi-modal fusion

**Domain-Aware Self-Supervised Pre-Training**
* Can be leveraged for label-efficient multi-modal adaptation
* Achieves competitive, even superior performance gains in some scenarios
* Performances vary task-dependently:
  + MM-SimCLR: Better on EMOT-Q and HarMeme tasks (lower level of granularity)
  + Ext-PIE-Net: Better on SENT and EMOT tasks (requires modeling higher abstraction level for target categories)

**Methodology Analysis**
* Further analysis and evaluation needed to understand generalizability


## A Hyperparameters
* Training on NVIDIA Tesla P4 with 8GB dedicated memory using Pytorch
* Initialization with pre-trained weights for image encoder (ResNet-18) and text encoder (distilbert-base-uncased)
* Freeze encoder weights during supervised learning, add new classification layers
* Use Adam optimizer and cross-entropy loss
* Batch size: 32, learning rate: 0.0001 for multi-modal experiments; 0.0005 for Ext-PIE-Net
* Train MM-SimCLR for 150 epochs with a ResNet-50 backbone and batch size of 32
* Freeze encoder weights during label-efficient training, use classification heads for supervision
* Use Xavier initialization for new layers and set bias to zero.


## B Statistical Analysis of Datasets

**Datasets Used in Hate Speech Analysis:**
- Created synthetically using specific hate topics or downloaded from social media platforms using generic and domain-specific hate keywords (Kiela et al., 2020; Gomez et al., 2020; Pramanick et al., 2021)

**Top-5 Hate and Non-hate Keywords:**
- Ranked based on tf-idf scores within the accompanying texts (Table 5)
- Represent extreme urban parlance in MMHS150K (realistic social media communication)
- Canonical and topic-oriented in Hateful Memes dataset

**Balancing Potential Keyword Bias:**
- Categorical representation balanced by introducing confounders or considering contrastive examples for exact hate keywords

**Length Distribution:**
- Mean length of all datasets: 8 (Fig. 5)
- MMHS150K: uniform distribution with most posts less than 30 words due to tweet character limit (Fig. 5a)
- Hateful Memes: reasonable variation, some examples greater than 30 words (Fig. 5b)
- Confounding effect visible in Fig. 5b where longer hateful content could be present
- Harm-P reflects distribution of accompanying textual contents over social media (Fig. 5c).


## C Training Characteristics

**Observed Trends in Training Curves**
- **Significant fluctuations within training curves**: especially for SENT and EMOT-Q tasks
- **Gradual enhancement in performances** observed in early epochs (<60) for both SENT and EMOT tasks
  - Ext-PIE-Net has the best macro-f1 score, with significant variation
  - Both models perform reasonably similarly overall

**Performance Trends for SENT Task by Label Configuration**
- **Ext-PIE-Net**: Consistent growth in macro-f1 score for all label configurations
- **Word Frequency Analysis**: Top-5 most frequent words and their tf-idf scores in each class (Table 5)
- **Distributions of Text Length**: Comparison between Hateful/Harmful and Not-hateful/harmful scenarios (Figure 5)

**Comparison of Training Performance for Different Label Fractions**
- Ext-PIE-Net: Showcases better convergence across all label configurations (Figure 6, top row)
- MM-SimCLR: Exhibits better training behavior after 30th epoch, especially for scenarios involving 1% and 50% labeled samples (Figure 6, bottom row)


## D Ethics and Broader Impact

**User Privacy**:
- Meme content and associated information do not include personal information
- Issues related to copyright addressed as part of dataset source

**Biases**:
- Any unintentional biases found in the datasets are acknowledged
- Detecting emotions and harmfulness can be subjective, leading to potential biases in gold-labeled data or label distribution

**Misuse Potential**:
- Datasets used can be potentially used for ill-intended purposes, such as biased targeting of individuals/communities/organizations
- Research activity requires human moderation to prevent misuse

**Intended Use**:
- Datasets used solely for research purposes in line with the intended usage prescribed by their creators
- Dataset will be distributed for research only, without a license for commercial use

**Environmental Impact**:
- Large-scale Transformers require many computations, contributing to global warming
- However, in this case, models are fine-tuned on relatively small datasets and can be run on CPUs for inference without significant environmental impact.

