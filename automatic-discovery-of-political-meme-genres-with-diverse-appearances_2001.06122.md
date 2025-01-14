# Automatic Discovery of Political Meme Genres with Diverse Appearances

[Automatic Discovery of Political Meme Genres with Diverse Appearances](https://arxiv.org/abs/2001.06122)

## Table of Contents
- [Automatic Discovery of Meme Genres with Diverse Appearances](#automatic-discovery-of-meme-genres-with-diverse-appearances)
- [Introduction](#introduction)
- [Related Work](#related-work)
- [Meme Genre Discovery](#meme-genre-discovery)
- [Experiments](#experiments)
- [Observations on the 2019 Indonesian Election](#observations-on-the-2019-indonesian-election)
- [Conclusions](#conclusions)

## Automatic Discovery of Meme Genres with Diverse Appearances

**Abstract Forms of Human Communication:**
- Not static; evolve due to technological advances
- Example: image-based memes as dominant form of political messaging
- Originally used for spreading jokes on social media
- Now impact public perception significantly

**Challenge in Automatic Meme Analysis:**
- Developing a strategy to match memes within the same genre despite varying appearances

**Approach Introduced:**
- Scalable automated visual recognition pipeline
  - Ingests meme images from social networks
  - Applies computer vision techniques for local feature extraction and indexing new images into a database
  - Organizes memes into related genres

**Validation:**
- Large case study on the 2019 Indonesian Presidential Election using over two million images collected from Twitter and Instagram
- Examined humorous memes posted to Reddit

**Results:**
- Approach can discover new meme genres with visually diverse images that share common stylistic elements
- Paves the way for further work in semantic analysis and content attribution.


## Introduction

**Meme Memes on Social Media:**
* Image-based memes popular form of communication
* Originated from online communities on 4chan and Reddit
* Spread freely among casual users
* Advanced image editing software increased production
* Varied genres with diverse visual forms (Fig. 1)
* Mimicry or remix in politics: "get out the vote" campaigns to anti-social narratives

**Research on Memes:**
* Computer vision used for automatic discovery and tracking
* Challenges include matching small, localized objects
* Our work introduces an end-to-end processing pipeline (Fig. 1)
* Primary advantage: matches based on detected objects and themes

**2019 Indonesian Election:**
* Over two million related images collected from social media
* Goal: detect and study election trends expressed in images
* Spontaneous, coordinated campaigns to influence different aspects of the election

**Approaches for Meme Clustering:**
* Recent literature suggests various meme clustering approaches (Dang et al., Dubey et al., Zannettou et al.)
* Our pipeline relies purely on visual features extracted from localized objects
* Designed to match both mimicry and remix

**Case Study: Indonesia:**
* Large number of Internet users, diverse population, democratic culture
* Opportunity to study the spread of political memes during 2019 election
* Results can be applied to model what might happen in other middle-income democracies with recent Internet participation
* Opinion polls and election results monitored to understand public views and government outcomes.


## Related Work

**Meme Genres:**
- Concept of diverse form categorization (Shifman, 2013)
- Examples: Stock Character Macros, Reaction Photoshops, Photo Fads
- Variety implies need for automated analysis addressing visual diversity

**Non-automated Meme Analysis:**
- Researchers target specific social media ecosystems or memes of interest (YouTube, Reddit, 4chan)
- Important step towards understanding process of drawing inferences from genres of memes

**Meme Clustering:**
- Automatically tracking and grouping memes based on textual content (Dang et al., 2015; Dubney et al., 2018)
- Use text clustering as proxy for meme clustering or deep learning features extraction
- Perceptual hashing (PHASH) to describe and compare visual content (Zannettou et al., 2018)

**Content-Based Image Retrieval:**
- CBIR algorithms focus on two matching tasks: near duplicate images and semantically similar images
- Importance of retrieving every meaningful piece of query for data clustering in meme analysis (Brogan et al., 2019)

**Image Forensics:**
- Detection of inconsistencies in images is not helpful for analyzing memes as manipulation is not hidden
- Semantic analysis of images, such as image phylogeny and provenance analysis, are closer to meme discovery (de Oliveira et al., 2016; Bharati et al., 2019)

**Content Understanding:**
- This work can aid further research in social media content understanding (Dewan et al., 2017; Blandfort et al., 2019).


## Meme Genre Discovery

**Meme Genre Discovery (MGD) Pipeline**

**Overview**:
- Multi-stage pipeline to detect related images based on visual content
- Constructs clustering of content within a dataset unsupervised, without human intervention or prior knowledge

**Pipeline Steps**:
1. **Indexing of Images based on Local Features**
   - Fast and scalable image searches using an indexing strategy from the OS2OS algorithm
   - Image features describe aspects of a target spatial region, invariant to transformations
   - Index built using SURF features (Bay, Tuythaeals, Van Gool 2006) and Inverted File (IVF) index with Optimized Product Quantization (OPQ) (Ge et al. 2013)

2. **Construction of Affinity Matrix**
   - Build approximate affinity matrix A based on image relationships from the index
   - Sample set of images Q to query the index and obtain match results Mq for each query qi
   - Weighted edges formed between matched images, representing affinity score S(qi,mj)

3. **Spectral Clustering of Affinity Matrix**
   - Multiclass spectral embedding and clustering to assign images to hypothesized meme genres
   - Diagonalize and decompose A into principal components via eigendecomposition
   - Reproject data onto the first V eigenvectors in a new matrix R, which contains the coordinates for all N images
   - Run K-means clustering on the V dimensions to obtain final clusters representing meme genres.


## Experiments

**Data Collection:**
- Collected data from Twitter and Instagram using Chrome plugin and Python program
- Gathered images for 11 months before Indonesian presidential election in 2019
- Used Google Chrome plugin to collect images from 11 hash tags and 3 users on Twitter
- Collected data from 15 hashtags and 5 users on Instagram using InstaLooter
- Total of 174,328 images from Twitter and 1,851,411 images from Instagram

**Genre Detection:**
- Used MGD pipeline to discover meme genres in the union of images collected from Twitter and Instagram
- Detected 7,691 clusters with example images for three separate clusters shown in Figure 5
- Computational efficiency scales linearly with number of images and can be processed parallelly
- Approximately 10,000 images can be processed per hour

**Validation:**
- Impostor-host methodology used to evaluate coherence and interpretability of detected clusters
- Human annotators presented with five images: four from same cluster and one impostor image
- Annotators tasked with selecting the impostor image
- Accuracy of human annotators was 51.21%, significantly better than chance (20%)
- Indicates MGD pipeline can detect cohesive clusters reliably

**Human Interpretation:**
- After validating detected clusters, a team of undergraduate students manually labeled them into five super-genres: Advertisement, Dyed Finger, Tweet or Text, Political, and Not Related
- Labeling helped understand content in each cluster

**Feature Extractor Comparison:**
- Compared MGD with PHASH (Monga and Evans 2006) and VGG Convolutional Neural Network (CNN) on a smaller dataset of 44,612 images
- Recomputed clusters using PHASH, VGG, and MGD feature extractors
- Differences in number of images per cluster observed between methods

**Generalization to Other Data:**
- Performed experiment on Subreddit r/photoshopbattles dataset to show approach generalizes beyond Indonesian election data
- MGD achieved an accuracy of 72.39% and normalized average accuracy of 16.15%, while VGG and PHASH clusters contained mostly single images (96% and 90.67%)

**Sensitivity to K-means Parameter:**
- Performed experiment with increasing values of K to study effect on distribution of images across clusters
- MGD distributes images more evenly, while VGG and PHASH maintain stable but larger maximum cluster sizes
- Choice of K = 100 for comparison experiments was reasonable.


## Observations on the 2019 Indonesian Election

**Findings from Indonesian National Election Dataset using MGD Genre Discovery System**

**Technical Challenges**:
- Clustering of meme images and other visually related content
- Unique perspective on major world election with a well-defined focus

**Positive Social Messages**:
- Prevalence of positive messages like dyed finger mimicry meme
- Pro-social public service announcement (PSA) messages
  - Warnings about fake news and propaganda

**Negative Campaigning**:
- Negative online campaigning by supporters of Jokowi Widodo
- Memes mocking Prabowo Subianto's gaffe

**Advertisements**:
- 21.5% of images fell into "Advertisement" super-genre
- Prevalence of parasitic advertising for dubious health supplement "Super Grow Up"
- Attempts by supporters of Subianto to promote evidence of voter fraud

**Image Manipulation**:
- Difficulty determining if images have been manipulated
- Belief in manipulated images among Indonesian citizens


## Conclusions

**Meme Analysis Research: Summary**

**Background:**
- Situated within growing body of meme analysis research
- Introduced new data set for Indonesian presidential election images (2 million) and open source pipeline
- Discussed limitations and potential improvements for current approach

**MGD Pipeline:**
- Addresses shortcomings in feature extraction methods
- Clusters images based on visual similarity without meta-data
- Data and code available through Google drive

**Limitations:**
- No temporal context from meta-data used
- Inability to handle images related to more than one cluster
- Potential for improving clustering accuracy and fusion of different feature extractors (VGG, MGD)
- Developing a semantic analysis mechanism integrating visual, textual, and contextual data

**Future Research:**
- Understanding memes as a form of communication in various populations
- Investigating how long it takes for a population to become "fluent" in a meme
- Studying political memes spreading in authoritarian countries without democratic elections (China, Hong Kong)
- Applying meme discovery pipeline to collections of memes from other countries.

**Examples:**
- Hand gestures indicating support for specific candidates found in clusters.

