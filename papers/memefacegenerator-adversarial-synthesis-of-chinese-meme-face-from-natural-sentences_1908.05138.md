# MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences

[MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences](https://arxiv.org/abs/1908.05138)

## Table of Contents
- [MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences](#memefacegenerator-adversarial-synthesis-of-chinese-meme-face-from-natural-sentences)
- [1 Introduction](#1-introduction)
- [2 Approach](#2-approach)
- [3 System Demonstration](#3-system-demonstration)
- [4 Analysis](#4-analysis)
- [5 Conclusions](#5-conclusions)

## MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences

**MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences**

**Abstract**:
- Chinese meme-face is a popular internet subculture in Chinese Social Community Networks
- Consists of a template image modified by amusing details and a text caption
- **MemeFaceGenerator**: Generative Adversarial Network with attention module and template information as supplementary signals to automatically generate meme-faces from text inputs
- Developed web service for system demonstration of meme-face synthesis
- MemeFaceGenerator capable of generating high-quality meme-faces from random text inputs.

**Key Components**:
- **MemeFaceGenerator**:
  - Generative Adversarial Network
  - Attention module and template information as supplementary signals
- Web service for system demonstration

**Performance**:
- Capable of generating high-quality meme-faces from random text inputs.


## 1 Introduction

**Chinese Social Community Networks (SNS)**
- **Meme-faces**: new fashion and pop-culture in Chinese SNS
- Different from classic emojis: express more abstract emotions
- Manually created through image editing process

**Creation of a Meme-face**
1. **Picking a meaningful image**: changing details to make it amusing
2. **Adding or modifying details**: align semantics of image to text
3. **Computer role**: used only as an image editing tool
4. **Active research area**: bridging semantics between image and natural language
5. **Generative Adversarial Networks (GANs)**: directly generate text-aligned meme-faces
6. **Generator G**: downsamples pattern Pi and xˆ, concatenates, performs MLP
7. **Editing component G′i**: generates new meme-faces based on text and pattern
8. **Discriminators D0 to Dm**: inherited from AttnGAN
9. **Text-image matching network Deep Attentional Multimodal Similarity (DAMSM)**: inherited from AttnGAN
10. **Objective function L**: includes loss functions LG and LDAMSM

**Meme-face Generation using GAN with Attention Module**
- Applies GAN architecture with attention module to exploit relationships of texts and image regions
- Adopts basic patterns in meme-face templates as supplementary signal: enforces generator focus on modifying essential local regions to semantically match given text caption.


## 2 Approach

**MemeFace Generator Architecture**
- **Overview**: GAN architecture with attention module named MemeFace-Generator to generate meme-face from text semantics representation
- **Components**:
  - Stacked Attentional Generative Network (Xu et al., 2018) models text into visual-semantic representations xˆ
    - Conditioning Augmentation (Fca)
    - Attention model i (Fattn) for obtaining new sentence embedding at each stage
    - Generator Gi represents the ith generator of AttnGAN
  - Editing component G′i generates text-aligned and pattern closed meme-faces
    - Downsamples Pi and xˆ into representations with same dimension
    - Concatenates and performs Multi-layer Perceptron (MLP) to integrate information
    - Uses up-sampling blocks to generate images in small-to-large scales
- **Inherited Architectures**: Generator G, discriminators D0 to Dm, and text-image matching network Deep Attentional Multimodal Similarity (DAMSM) from AttnGAN

**Data Preparation**
- Collect 56,710 meme-faces online, extract text captions via OCR engine
- Implement data cleaning based on:
  - Categories of meme-face
  - Words in text caption
- Use clustering to find meme-faces from the same templates and refine quality of text captions

**Training Details**
- Optimize MemeFaceGenerator using Adam with learning rate 0.0002, batch size 14
- Train for 200 epochs, update generator every 5 epochs, discriminator every epoch
- Construct neural networks via Pytorch 0.3.0


## 3 System Demonstration

**System Demonstration:**
* Web server constructed using vue and tornado (Figure 3)
* Input text transferred from front-end to back-end as json format
* Model generates meme-faces based on loaded epochs and input text
* Generated meme-faces posted sequentially on web front-end for demonstration
* System log contains training progress information
* Meme-faces are 256x256 pixels and encoded using base64 schemes
* Left side of the web page shows a sequence of generated meme-faces throughout training process.

**Learning Process:**
* Introducing template information for panda face
* Model rapidly learns profile and general features of meme-face
* Focuses on generating more detailed facial expressions
* Adjusts facial expression to match input text gradually
* Final result is a smiling face semantically relevant to the input text "Wow, not bad."


## 4 Analysis

**Meme-Face Generator Analysis**

**Semantic Relevance**:
- Ideally, generator should produce images semantically relevant to text captions
- Several generated meme-faces analyzed for acuity and rationality in semantic-relevance capturing

**Example 1: Blushing Cheeks (Figure 4a)**:
- Given text input "lil cutie I’m here"
- Generator captures semantics, reflected by blushing cheeks in the image

**Example 2: Telephone Receiver (Figure 4d)**:
- Given text input "hang up (the phone)"
- Generator extracts phrase and generates telephone receiver accordingly

**Example 3: Sadness and Provocation (Figures 4b, 4e)**:
- Given text inputs "just go, dare you hit the road don’t come back", "listen to me, stop arguing and put up a fight"
- Generator extracts sentiments of sadness and provocation, generates meme-faces with tears and shouting poses

**Example 4: Famous Meme-Faces (Figures 4c, 4f)**:
- Consistent with text inputs "Best drama queen of the year", "Wow, not bad"
- Generator learns relevance between faces in different templates and text sentiments

**Synthesizing Results**:
- Visual-semantic representations capture various semantics from text input
- Stack Attentional Generative Network enables detailed and emotional images agreeing with text inputs
- Synthesized results can be used directly in social community networks without further editing

**Numerical Evaluation**:
- Cross-evaluation by 3 annotators using labeling criterion:
  0: Poor quality or inconsistent with text caption
  1: Acceptable but not closely relevant to the text caption
  2: Interesting content and matches with text caption
- Over 80% of generated images labeled as 1 or higher, verifying generator's capability in modeling latent semantic relevance between input text and output image.


## 5 Conclusions

**MemeFaceGenerator using GAN with Attention Module:**

1. Utilized Chinese meme-face generation with a GAN architecture and attention module.
2. Incorporated template information during training for improved results.
3. Implemented precise data cleaning process.
4. Generates meme-faces consistent with text inputs.
5. Captures various semantics in generated images and text captions through facial expressions and details.


---

Thank you to arXiv for use of its open access interoperability.