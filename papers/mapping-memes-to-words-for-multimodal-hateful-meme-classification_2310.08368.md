# Mapping Memes to Words for Multimodal Hateful Meme Classification

[Mapping Memes to Words for Multimodal Hateful Meme Classification](https://arxiv.org/abs/2310.08368)

## Table of Contents
- [Mapping Memes to Words for Multimodal Hateful Meme Classification](#mapping-memes-to-words-for-multimodal-hateful-meme-classification)
- [2. Related Work](#2-related-work)
- [3. Proposed Approach](#3-proposed-approach)
- [4. Experimental Results](#4-experimental-results)
- [5. Conclusion](#5-conclusion)

## Mapping Memes to Words for Multimodal Hateful Meme Classification

**I. Introduction**
- Multimodal image-text memes combine visual and textual elements
- Prevalent on internet, used for humor, ideas, or emotions
- Some memes promote hateful content and discrimination
- Detecting hateful memes is challenging due to intertwined meaning of text and images

**II. Approach: ISSUES (Interactive Semantic Synthesis for Hateful Memes)**
- Proposed approach for multimodal hateful meme classification
- Leverages pre-trained CLIP vision-language model and textual inversion technique
- Effectively captures multimodal semantic content of the memes

**III. Experiments and Results**
- Achieves state-of-the-art results on Hateful Memes Challenge and HarMeme datasets
- Code and pre-trained models available at https://github.com/miccunifi/ISSUES

**IV. Disclaimer**
- This paper contains hateful content that may be disturbing to some readers.


## 2. Related Work

**Related Work**

**Hateful Meme Classification**:
- Hateful meme classification has gained prominence as an emerging multimodal task
- Facebook's organization of the **Hateful Memes Challenge (HMC)** established a benchmark dataset
- Provided baselines for competitors like **VilBERT** and **VisualBERT**
- Top 5 submissions outperformed baselines due to:
  - Use of external data, additional input features, and/or ensemble models

**After the Competition**:
- Other methods have been proposed:
  - **PromptHate**: A prompt-based model that prompts pre-trained language models
  - **Hate-CLIPper**: Explicitly models the cross-modal interactions between CLIP image and text features

**Textual Inversion**:
- Textual inversion has emerged as a powerful approach in:
  - Personalized image generation (text-to-image synthesis)
  - Virtual try-on
  - Personalized and composed image retrieval
- Methods that employ textual inversion:
  - **SEARLE**: Trains a textual inversion network with a distillation-based loss


## 3. Proposed Approach

**CLIP (Contrastive Learning of Image and Text Representations) Model**:
- Designed to align visual and textual data within a common embedding space
- Comprises a **visual encoder (VE)** and a **text encoder (TE)**
- VE and TE extract feature representations from an input image and its corresponding text caption, respectively

**SEARLE Model**:
- Approach that involves training a **textual inversion network (ϕ)** by distilling knowledge from an optimization-based method
- ϕ network maps the CLIP visual features of an image into a **pseudo-word token** within the CLIP token embedding space
- Pre-training of ϕ ensures the pseudo-word token captures both the visual information of the image and enables effective interactions with actual words.

**ISSUES Approach**:
- Focuses on three main areas:
  1. Enhancing the textual representation of a meme through textual inversion
  2. Adapting the embedding spaces of the pre-trained model using linear projections
  3. Employing an expressive multimodal fusion function

**Textual Inversion**:
- Maps the image of a meme IM to a **pseudo-word token v∗** in the CLIP token embedding space W
- Combines textual features from a prompt "a photo of S∗, {meme text}" which encompass both textual and visual information

**Embedding Space Adaptation**:
- Pre-trained text and image encoder projections aim to align text and image representations in a shared multimodal latent space
- However, this alignment is not suitable for the task as memes contain text and images with different meanings
- Linear projections are trained after freezing the ϕ and CLIP encoders to adapt the embedding spaces and disentangle image and text modalities

**Multimodal Fusion Function**:
- Adopts the **Combiner network** as the multimodal feature fusion function
- Takes two multimodal representations as input:
  1. Pre-trained projection of the CLIP visual encoder
  2. Projection of the output of the CLIP text encoder augmented with textual inversion
- The Combiner enhances its capability to capture the nuanced semantics of memes by utilizing two multimodal representations.


## 4. Experimental Results

**Experimental Results**

**Datasets**:
- HMC [9] and HarMeme [18] used for experiments
- HMC: 8500, 500, 2000 synthetic memes in training, development, test sets respectively
- Hatred targeted at religion, race, disability, sex
- HarMeme: COVID-19 related real-world memes labeled as very harmful, partially harmful, and harmless
- Combined first two classes into a single hateful class
- HMC train/test split not reported for DisMultiHate [12] and PromptHate [5]

**Quantitative Results**:
- Comparison of ISSUES with baselines and competing methods in Tabs 1 and 2 (HMC test unseen, HarMeme test sets)
- CLIP Text/Image Only and Sum performed better than Vanilla BERT models
- Hate-CLIPper [10] outperformed by ISSUES on both datasets

**Ablation Study**:
- Tab. 3 shows results of an ablation study on the HMC dataset, evaluating different components of the model (Combiner, 2-stage training, textual inversion)


## 5. Conclusion

**ISSUES: Classifying Hateful Memes**

* Introduce ISSUES: a method for hateful meme classification using CLIP and textual inversion.
* Adapt pre-trained models through trainable linear projections and two-stage training.
* Enhance semantic interactions with Combiner network.
* Evaluated on HMC and HarMeme datasets, achieving SotA results.
* Partially funded by European Commission Horizon 2020 program (grant number 101004545).


---

Thank you to arXiv for use of its open access interoperability.