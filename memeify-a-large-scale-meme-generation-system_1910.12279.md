# Memeify: A Large-Scale Meme Generation System

[Memeify: A Large-Scale Meme Generation System](https://arxiv.org/abs/1910.12279)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Dataset Description](#2-dataset-description)
- [3 MEMEIFY: Our Proposed Architecture](#3-memeify-our-proposed-architecture)
- [4 Evaluation and Analysis](#4-evaluation-and-analysis)
- [5 Conclusion](#5-conclusion)

## Abstract

**Memeify: A Large-Scale Meme Generation System**

**Background:**
- Interest in meme research increasing rapidly
- Limited dataset availability, lacking class information or specific context

**Contribution:**
- Preparation of large-scale meme dataset with captions and class labels (1.1 million meme captions from 128 classes)
- Explanation for the existence of broad categories called 'themes' across the meme dataset
- Each theme consists of multiple meme classes

**Methodology:**
- Use a trained state-of-the-art transformer model for caption generation
- Employ an encoder-decoder architecture

**System Development:**
- Web interface named Memeify for users to generate memes of their choice
- Detailed explanation of individual components of the system

**Evaluation:**
- Qualitative evaluation through user study

**Publication:**
- Published in 7th ACM IKDD CoDS and 25th COMAD (CoDS COMAD 2020), January 5–7, 2020, Hyderabad, India
- Appeared in ACM, New York, NY, USA with a DOI link: https://doi.org/10.1145/3371158.3371403


## 1 Introduction

**Meme Generation: Current Trends and Advances**

**Memes**:
- Hottest trending ways of expressing ideas and opinions on social media since late 2000s
- Conquered Internet landscape with hundreds accessed daily on various platforms
- Creation requires context and creativity

**Advances in Mememe Generation**:
- Deep learning and natural language processing (NLP) advances enable generative tasks
- Peirson et al. proposed meme generation network as image captioning problem
  * Used standard Glove embeddings for word vectors, simple encoder-decoder architecture
- BERT model generates vectors for each word through transformer network training
- MT-DNN generalizes BERT, applies effective regularization mechanism to create word vectors

**Proposed Meme Generation System: Memeify**
- Generates captions given a context
- Builds large-scale reliable and robust dataset
- Draws inferences on meme characteristics based on image backgrounds and captions
- Proposes end-to-end meme generation system for real-time meme creation

**Contributions**:
- Generation of large-scale meme dataset (first of its kind)
- Design of novel web application to generate memes in real time

**Accessibility**:
- Code and dataset made public at https://github.com/suryatejreddy/Memeify


## 2 Dataset Description

**Data Curation**
- Created own dataset of meme images, captions, and class information
- Each meme belongs to a specific class based on base image
- Current datasets have limitations:
    - Reddit meme dataset has no captions or class info
    - Meme generator dataset has a large class imbalance and broken links
- Overcame these issues by scraping data from QuickMeme and other sources
- Created a dataset of 1.1 million memes in 128 classes with base images and captions

**Exploring the Data**
- Sampled 5,000 memes for analysis
- Performed clustering to identify 5 distinct clusters (Figure 1a)
- Observed that every meme can be associated with a broad "theme" based on words in captions

**Theme Identification**
- Segregated meme classes into themes using clustering algorithm
- Labeled themes as: **Normie**, **Savage**, **Depressing**, **Unexpected**, **Frustrated**, and **Wholesome** (Figure 1b)
- Table 1 shows the assignment of classes to their corresponding themes

**Confirmation of Hypothesis**
- Created image vectors for each meme using VGG16 convnet
- Clustered these vectors and assigned themes as labels
- Inferred that the theme of a meme depends on words in its caption, not the background image.


## 3 MEMEIFY: Our Proposed Architecture

**Meme Generation Model**
- **Problem**: Memes generation as a language model task to produce funny and apt captions given an image or class label prompt
- **Approach**: Train deep learning models (LSTM networks and variants) on meme corpus, but find limitations:
  - Inaccurately capture class information
  - Difficulty reproducing humor
- **Solution**: Use transformer-based GPT-2 architecture as base language generative model, incorporating class information in captions to generate class-specific meme captions
- **Benefits**: GPT-2 solves humor expression issues due to self-attention capabilities, large-pretraining, and multiple task adaptability

**Memeify System**
- **Generation Methods**:
  - Randomization: Users select theme and class, system generates caption and retrieves corresponding image
  - Customization: Users upload images, system identifies theme and class using similarity matching algorithm and generates caption
- **Web Application**:
  - Landing page with options to generate random or custom memes
  - Backend uses Flask to interact with trained model for caption generation

**Efficiency Improvements**:
- Cache generated memes on backend using Redis to avoid repetition for single users
- Asynchronous AJAX data transfers between webpage and server for seamless user experience


## 4 Evaluation and Analysis

**User Satisfaction Study**
- **Participants**: 20 human experts, social media experts aged 25 to 40 years
- **Evaluation Tasks**:
   - Rate generated and original memes from 1 (lowest) to 5 (highest) based on caption-content, humor, and originality
   - Averaged results for each theme
- **Findings**:
   - Generated memes were almost as good as original memes in terms of user satisfaction
   - Model outperformed baseline model across all themes

**Differentiation Ability of Users**
- **Goal**: Understand if the generated memes were significantly different from the original ones
- **Evaluation**:
   - Generated a batch of 50 memes for each theme (randomly picking classes) for both the model and the baseline model
   - Showed generated and original memes to volunteers and asked them to classify them as generated or original
- **Findings**:
   - Volunteers misclassified generated memes as original 66.67% of the time, vouching for the authenticity of the model

**Theme Recovery**
- **Goal**: Understand if the idea of themes holding true across volunteers
- **Evaluation**:
   - Showed a set of 10 memes per theme to volunteers
   - Generated 100 memes (from the model) across themes and asked volunteers to classify them into the 6 themes
- **Findings**:
   - High overall classification accuracy, confirming the existence of themes across meme classes
   - Low accuracy for 'Normie' theme due to large number of low-similarity classes compared to other themes


## 5 Conclusion

**MemeFaceGenerator using GAN with Attention Module**

    1. Utilizes Chinese meme-face generation task with GAN architecture and attention module
    2. Employs meme-face template information during training for improved results
    3. Implements precise data cleaning process
    4. Generates meme-faces consistent with text inputs
    5. Captures various semantics between images and text captions (details, facial expressions)

