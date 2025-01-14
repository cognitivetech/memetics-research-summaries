# Codec at SemEval-2022 Task 5: Multi-Modal Multi-Transformer Misogynous Meme Classification Framework

[Codec at SemEval-2022 Task 5: Multi-Modal Multi-Transformer Misogynous Meme Classification Framework](https://arxiv.org/abs/2206.07190)

## Table of Contents
- [Multi-Modal Multi-Transformer Misogynous Meme Classiﬁcation Framework](#multi-modal-multi-transformer-misogynous-meme-classiﬁcation-framework)
- [1 Introduction](#1-introduction)
- [2 Background](#2-background)
- [3 System overview](#3-system-overview)
- [4 Experimental setup"](#4-experimental-setup)
- [5 Results](#5-results)
- [6 Conclusion](#6-conclusion)

## Multi-Modal Multi-Transformer Misogynous Meme Classiﬁcation Framework

**Multi-Modal Multi-Transformer Framework for Misogynous Meme Classification (SemEval-2022 Task 5)**

**Approach**:
- Based on three main strategies:
  1. Combine different state-of-the-art architectures to capture a wide spectrum of semantic signals from multi-modal input.
  2. Employ multi-task learning scheme to use multiple datasets from the same knowledge domain to increase performance.
  3. Use multiple objectives to regularize and fine-tune system components.

**Participation in SemEval 2022 Competition (Task 5)**:
- Building a generic framework for both multi-modal embedding and multi-label binary classification tasks.

**Challenges**:
- Pretraining deep models from scratch is resource and data hungry, so the approach is focused on combining various strategies to improve performance.

**Strategies Detailed**:
1. **Combining different state-of-the-art architectures**:
   - Capture a wide spectrum of semantic signals from multi-modal input.

2. **Employing multi-task learning scheme**:
   - Use multiple datasets from the same knowledge domain to help increase the model's performance.

3. **Using multiple objectives**:
   - Regularize and fine-tune different system components.


## 1 Introduction

**Introduction:**
* Participating in SemEval 2022 task 5: Multimedia Automatic Misogyny Identification (MAMI) challenge
* Binary and multi-label binary classification tasks for identifying misogynous memes using image and text content
* Memes are multi-modal, rely on implicit knowledge, and subject to human interpretation
* Using transformer-based architectures for combining text and vision inputs

**Approach:**
* Pretraining deep neural networks and transformer-based architectures is data-hungry and computationally demanding
* Combining different pretrained architectures as backbones using a limited computational budget
* Capturing wide spectrum of semantic signals from input modalities for effective learning
* Employing auxiliary objectives to guide model during training towards main objective
* Building a generic classification framework for both sub-tasks A and B

**Components:**
* Multi-modal shared transformer encoder
* Uni-modal multi transformer encoders
* Sequence embedding (Figure 1)

**Performance:**
* Sub-task A: macro-average F1-Measure = 0.715 during evaluation phase, higher score post-evaluation = 0.761
* Sub-task B: weighted-average F1-Measure = 0.698 during evaluation phase
* Code available at https://github.com/nahmed-mahran/MAMI2022.


## 2 Background

**Datasets:**
- **MAMI dataset** is one of many available datasets for training machine learning models
- Input can be:
  - Uni-modal (text or image only)
  - Bi-modal (pairs of image and text)
- **63 publicly available datasets** cataloged on a dedicated website, reviewed in (Vidgen and Derczynski, 2020)
- Used: **1hatespeechdata.com**, hateful meme dataset by Facebook AI (**Kiela et al., 2020**) with 10K labeled images

**Multi-modal Frameworks:**
- **MMBT (Kiela et al., 2019):**
  - Concatenates linear projection of ResNet output for image and BERT tokens embeddings for text
  - Sequence fed into a transformer encoder, called bi-transformer
  - Adds positional and segment embeddings to distinguish image and text parts
  - Architecture can use different image encoders
- **MMCA (Wei et al., 2020):**
  - Combines Faster R-CNN with BERT for two embedding types:
    - Self-attention embedding to capture intra-modality interactions
    - Cross-attention embedding to capture both intra and inter-modality interactions


## 3 System overview

**System Overview**

**3.1 Token Embedding:**
- Each input modality encoded into a sequence of vectors in unified dimension space
- Binary mask vector generated for length of sequence to indicate which parts are considered
- Output: "Token Embedding" and "Tokens Binary Mask" layers (Figure 1)
- Different encoders per modality, various sequence types for capturing semantic signals

**CLIP Image Embedding:**
- Split image into equal size patches
- Use CLIP to encode image and its slices into a sequence of vectors
- Project each vector into model hidden dimension space
- Use "RN50x4" CLIP model for backbone (ResNet-50 scaled up 4x)

**DETR Image Objects Embedding:**
- Use DETR to encode image into a sequence of 100 image objects representations
- DETR's classifier produces logits corresponding to object boxes and labels
- Mask out no-object predictions using DETR's classifier
- Ignore logit of no-object label, take softmax of remaining labels for selection
- Project each vector into model hidden dimension space

**BERT Text Embedding:**
- Use BERT pre-trained on hate speech to tokenize input text and generate embeddings
- Maximum of 120 tokens, don't project embeddings, use output space as model's hidden dimension space (768 dimensions)

**3.2 Sequence Embedding:**
- Combine token embeddings into a single sequence using normalization and addition
- Add token type embedding and positional embeddings
- Use multi-layer transformer encoder stage to produce final sequence embedding at "Sequence Embedding" layer (Figure 1)
- Two variants: Shared or multiple transformer encoders

**Shared Transformer Encoder:**
- Illustrated in Figure 1a
- Uses a single shared multi-layer transformer encoder for inter/intra-modality interactions
- Add token type embedding and [CLS], [SEP] tokens for each sequence type
- Use pre-trained BERT transformer encoder

**Multiple Transformer Encoders:**
- Illustrated in Figure 1b
- Uses a multi-layer transformer encoder per token type
- Adds token type embedding but no extra [SEP] or [CLS] tokens
- Use PyTorch's implementation of transformer encoder for each modality
- Concatenate all sequences from each transformer encoder as output sequence

**3.3 Classification:**
- Two modes: whole sequence embedding or pooled sequence embedding (Figure 2)

**Multi-head MLP Classifier:**
- Uses pooled sequence embedding as input
- Two feedforward linear layers with GELU activation and hidden size of 768
- Outputs number of logits equal to the number of classes, applies sigmoid activation for binary label probabilities

**Transformer Decoder Single-head MLP Classifier:**
- Takes whole sequence embedding along with binary mask as input
- Multi-head transformer decoder learns interactions between source and target sequences
- Single-head MLP classifier shares parameters for all classes
- Architecture same as multi-head MLP classifier but without separate layers per class

**3.4 Multi-task Learning:**
- Use more training data from other similar datasets using power set of labels (excluding empty set)
- Each dataset has its own set of tasks with separate MLP classifiers, shared parameters except learnable class queries
- Mini-batch contains data from only one dataset, compute targets per task for all tasks in that dataset during training

**3.5 Multi-objective:**
- Linearly project modal encoding into hidden model space to preserve similarity between instances
- Cosine similarity constraint: similarity between encodings should be the same as similarity between their projections
- Embedding loss: regularize embedding space of MLP classifier to make dissimilar labels more separable
- Encourages transformer encoder, decoder, and hidden layers of MLP classifier to produce embeddings that capture labels' similarity.


## 4 Experimental setup"

**MAMI and Facebook Hateful Meme (FBHM) Datasets:**
- **MAMI**: Misogynistic content labels: misogynous, shaming, stereotype, objectification, violence
- Task configurations:
  * Task_A: Misogynous
  * Task_B: Shaming, stereotype, objectification, violence
- **FBHM**: Hateful memes dataset
- Redundant task MAMI added for dependency learning

**Data Split and Evaluation:**
- 80% train and 20% development sets using stratified sampling
- Post-evaluation period of the competition as test set
- Batch size: 16
- Number of epochs: 15
- Optimizer: MADGRAD (Defazio and Jelassi, 2021)
- Learning rate: 2^-10^4 with a learning rate linear scheduler
- Gradient accumulation steps: Total number of batches * number of epochs = 20 * 15 = 300
- Warmup period: Total gradient accumulation steps = 10
- Weight decay for all parameters except biases and layer normalization weights: 5^-10^4
- Gradient clipping to overall norm of 0.5
- Implementation based on PyTorch and HuggingFace Transformers
- Google Colab Pro plus with one Tesla P100 GPU
- No special data preprocessing or fine tuning for backbones
- Official accuracy measures used for scoring:
  * Single class tasks: Macro-average F1-Measure (scoreA)
  * Multi class tasks: Weighted-average F1-Measure (scoreB)


## 5 Results

**Transformer Encoder Configurations**
- **Ablations**: System configurations for different architecture variations:
    - Transformer encoder (Xformer Enc) with shared transformer (Shared), multi transformers (Multi), or no pooling (No) of whole sequence using [CLS] embedding
    - Encoder output pooling (Pooling): Whether to pool the whole sequence using [CLS] or only text tokens using the decoder with single head MLP classifier
    - Token encoding projection alignment (Proj Align): Whether to enable it or not
    - Contrastive embedding loss (Contrastive): Whether to enable it or not
    - Multi-task learning (Multi-task) whether to use Facebook's hateful meme dataset or not
    - Image encoders (Backbones): Whether to use CLIP only, DETR only, or both together
- **Experiments**: Planned as a tournament of rounds, testing subset of configurations and reporting max scores for Task_A and Task_B on all splits. Winner variants are used for subsequent rounds.

**Round 1: Transformer Encoder vs. Encoder Output Pooling**
- Compared transformer encoder and encoder output pooling methods
- Performed four experiments, summarized in **Table 2**
- Multi-transformers encoders without output pooling architecture variant is the winner

**Round 2: Significance of Multi-Objective Approach**
- Tested encoding projection alignment (Proj Align) and contrastive embedding loss (Contrastive)
- Performed four experiments, summarized in **Table 3**
- Experiment 10 with multi-transformers, multi-pooling, no Proj Align, and no Contrastive is the winner

**Round 3: Significance of Image Encoders Backbones (CLIP vs. DETR)**
- Compared CLIP and DETR as image encoders backbones
- Performed one experiment, summarized in **Table 4**
- CLIP is more significant than DETR as an image encoder backbone

**Round 4: Significance of Additional Training Data from Facebook's Hateful Meme Dataset**
- Trained for more epochs to test the impact of external dataset
- Performed one experiment, summarized in **Table 5**
- The use of more training data from the external dataset results in significant improvement.

**Visualizations**
- t-SNE projections of transformer decoder output per class and corresponding class learnt input query embedding
- Class learnt queries can be thought of as centers of positive labels
- Average attention weights per transformer decoder layer, showing dependencies between classes (Figure 3) and source-target sequence attention weights (Figure 4):
    - Each class depends uniformly on other classes
    - Model pays more attention to CLIP features, less attention to BERT text features, and least attention to DETR object features.


## 6 Conclusion

**Framework for Multi-Modal Embedding and Multi-Label Binary Classification**

**Proposed Framework**:
- Combines different architectures achieving state-of-the-art in various tasks and modalities
- Captures a wide spectrum of semantic signals from the multi-modal input
- Employs a **multi-task learning scheme** to use multiple datasets from the same knowledge domain
- Uses **multiple objectives** to regularize and fine-tune the system components

**Visualization of Attention Weights**:
- Figure 3: t-SNE projections of transformer decoder output per class (small dots) and corresponding class query (biggest dot)
- Figure 4: Attention weights visualization per transformer decoder layer, with first input layer on the left and last output layer on the right

**Experiments**:
- Results show the significance of some ideas
- Future work:
  - Experiment with different backbone architectures
  - Try more objectives and regularizations (e.g., make decoder output for positive instance closer to corresponding class query embedding)

