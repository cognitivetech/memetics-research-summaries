# Social Meme-ing: Measuring Linguistic Variation in Memes

[Social Meme-ing: Measuring Linguistic Variation in Memes](https://arxiv.org/abs/2311.09130)

## Table of Contents
- [Social Meme-ing: Measuring Linguistic Variation in Memes](#social-meme-ing-measuring-linguistic-variation-in-memes)
- [1 Introduction](#1-introduction)
- [2 Methods](#2-methods)
- [3 SEMANTIC MEMES](#3-semantic-memes)
- [4 Evaluation](#4-evaluation)
- [5 Linguistic variation](#5-linguistic-variation)
- [6 Linguistic innovation](#6-linguistic-innovation)
- [7 Linguistic acculturation](#7-linguistic-acculturation)
- [8 Related work](#8-related-work)
- [9 Conclusion](#9-conclusion)
- [10 Ethical considerations](#10-ethical-considerations)
- [A Details on visually clustering templates](#a-details-on-visually-clustering-templates)
- [B Details on the semantic clusters](#b-details-on-the-semantic-clusters)
- [C Model evaluation details](#c-model-evaluation-details)
- [D Further semantic cluster examples](#d-further-semantic-cluster-examples)

## Social Meme-ing: Measuring Linguistic Variation in Memes

**Social Meme-ing: Measuring Linguistic Variation in Memes**

**Background:**
- NLP research exploring sociolinguistic variation in text
- Argument that memes exhibit meaningful social variation as multimodal forms of language
  - Visual templates and text

**Methodology:**
- Construct computational pipeline for clustering individual instances of memes
  - Advantage of their multimodal structure
- Resulting dataset: SEMAN-TICMEMES, containing 3.8M images clustered by semantic function

**Findings:**
- Socially meaningful variation in meme usage exists between subreddits
- Patterns of meme innovation and acculturation within communities align with previous findings on written language.


## 1 Introduction

**Introduction:**
- Variationist sociolinguistics: study of social factors contributing to language use differences
- Natural language processing research focuses on geography, community, time, and other social factors (Eisenstein et al., 2010; Hovy and Purschke, 2018; Demszky et al., 2021; Del Tredici and Fernández, 2017; Zhu & Jurgens, 2021b; Lucy & Bamman, 2021; Hamilton et al., 2016)
- Understanding language variation important for improving NLP tools (Blodgett et al., 2016) and uncovering social meaning (Campbell-Kibler, 2009; Zhang, 2005)
- Work mostly focused on lexical or morphosyntactic variation in written texts

**Multimodal Language:**
- Language exists beyond text and speech: co-speech gestures, facial expressions, body movement (Perniss, 2018)
- In online communication: interplay between images and text (Kress & Leeuwen, 2001; Zhang et al., 2021; Hessel et al., 2023)
- Understanding memes important for understanding multimodal online language

**Meme Analysis:**
- Meme templates and fills have semantic value (Figure 2)
- Set of functionally equivalent templates form a semantic cluster
- Variationist sociolinguistics treats templates as variants and clusters as variables
- Identify semantic clusters using visual structure of meme plates and linguistic structure of meme fills
- Create SEMANTIC MEMES dataset: 3.8M Reddit memes grouped into semantic clusters, validated with human evaluation
- Case studies demonstrating the use of semantic clusters in studying linguistic variation, innovation, and acculturation

**Findings:**
1. Socially meaningful variation exists in template choice between subreddits.
2. Subreddits that first introduce a new template continue to use it more than others.
3. Users who stay in a subreddit for longer tend to use distinctive templates within that subreddit.

**Conclusion:**
- Memes function as multimodal acts of communication
- Computational sociolinguistics methods shed light on meaningful variation within memes.


## 2 Methods

**Meme Analysis Methods**

**Identifying Meme Variation:**
- Use clustering algorithms to group memes based on visual similarity (§2.1) and linguistic function (§2.2)
- Visual clustering: isolate base image, extract templatized memes using perceptual hashing, and cluster instances into templates (Leiden algorithm)
- Linguistic clustering: extract fill text, learn semantic representations of templates, and cluster based on similar functions

**2.1 Visually Clustering Instances:**
- Preprocess images to remove solid color framing elements
- Extract templatized memes using perceptual hashing algorithm
- Compute pairwise Hamming distance between image hashes
- Use Leiden clustering algorithm for splitting into well-connected subgraphs

**2.2 Linguistically Clustering Templates:**
- Extract fill text from meme instances using EasyOCR
- Remove identical text in over 90% of memes within a template cluster
- Fine-tune RoBERTa classifier or CLIP model on sequence classification task to predict templates given fill text
- Generate embeddings for templates and fine-tune CLIP model with contrastive loss between image and text data
- Calculate difference between fine-tuned and pretrained CLIP embeddings (CLIP-diff)
- Concatenate CLIP-diff and RoBERTa embeddings
- Use Leiden clustering algorithm on standardized template representations for semantic clusters.


## 3 SEMANTIC MEMES

**Semantic Meme Dataset**
- **Dataset**: 27.9M images collected from Reddit's top 1000 active subreddits with "meme" in the name
- **Timeframe**: Spans the decade between 2011 and mid-2021
- **Metadata**: Includes author, timestamp, and subreddit information
- **Model Training**: Fine-tuned RoBERTa and CLIP models for three epochs on memes with at least 100 appearances in the dataset
- **Split**: 80/10/10 split of train, dev, and test data to avoid leakage of fill text
- **Results**: Generated 784 semantic clusters spanning 6,384 templates and over 3.8M meme instances
- **Cluster Examples**: Figure 4 shows some templates that appear in the same semantic cluster
- **Subreddits and Users**: Includes posts to 655 subreddits by 908,917 users
- **Descriptive Statistics**: Included for clusters generated with each embedding model (not provided in text)


## 4 Evaluation

**Evaluation Methodology**

**Human Judgment**:
- Evaluate coherence and visual diversity of semantic clusters derived from each model using human judgment
- Annotators presented with pairs of templates, randomly varied if from same or different semantic clusters
- Asked to evaluate:
  - **Semantic similarity**: Ability to substitute text from one template into the other with minor changes
  - **Visual similarity**: Sharing a similar art style or source (e.g., Spongebob)

**Evaluation Metrics**:
- **Model Precision**: Probability that a pair of templates are semantically similar if they appear in the same cluster
- **Model Visual-adjusted Precision**: Calculated as padj = ps - pv, where:
  - **ps**: Probability that a pair of templates are semantically similar if they appear in the same cluster
  - **pv**: Probability that a pair of templates are visually similar if they appear in the same cluster
- Negative score means the model clusters based on visual similarity instead of semantic coherence

**Findings**:
- CLIP-based models yield clusters biased towards visual features
- RoBERTa embeddings have highest **visually-adjusted precision** for semantically coherent and visually diverse clusters
- Semantic clusters provide strong separation between content (semantic cluster) and style (template within cluster)


## 5 Linguistic variation

**Linguistic Variation**
- Sociolinguistics studies variation in language based on different ways of saying the same thing (Tagliamonte, 2006)
- Choice of variation systematically depends on speaker identity, relationships with interlocutors, and sociopragmatic context
- Linguistic variation conveys social meaning (Nguyen et al., 2021)

**Computational Analysis of Variation**
- Focus often on lexical variation (Bamman et al., 2014; Zhang et al., 2017; Zhu and Jurgens, 2021a), semantic variation in online communities (Lucy and Bamman, 2021; Del Tredici and Fernández, 2018), or orthographic variation in online text (Eisenstein, 2015; Stewart et al., 2017)

**Research Question: Variation in Memes**
- RQ1: Does the template choice within a semantic cluster vary systematically between communities?

**Methods:**
- Semantic clusters form variable context
- Templates within each cluster represent discrete choices with the same semantic value
- Use weighted log odds-ratio to compute extent of template specificity in subreddits compared to all others (Monroe et al., 2017; Jurafsky et al., 2014)
- Find templates statistically significantly associated with a subreddit and their semantic clusters exhibit variation

**Results:**
- 94 out of 784 semantic clusters show significant variation
- 391 different templates across these clusters

**Examples:**
- r/Animemes uses orange Drake template frequently, while alternative versions are used in other subreddits (fig. 5c)
- r/dndmemes replaces Drake with Matthew Mercer to index into localized cultural knowledge
- Multimodality of memes permits greater expressiveness and can explicitly index into specific community aesthetics.


## 6 Linguistic innovation

**Linguistic Innovation: Meme Templates and Language Change**

**Background:**
- Study of diachronic linguistic change in natural language processing (NLP)
- Understanding innovation of meme templates within semantic clusters

**Research Questions:**
1. **RQ1**: Do new meme templates coexist or monopolize a cluster?
   - Competition between lexical choices: new words replace old, but similar words may coexist
2. **RQ2**: Entropy of semantic clusters over time
   - Measure entropy of template distribution within each cluster
   - Older clusters have larger confidence intervals in later years (Figure 6)
3. **RQ3**: Do new templates diffuse widely or occupy a niche?
   - Language change is socially motivated: communities may use specific variants to distinguish themselves
4. **Methods:**
   - Measure entropy of semantic clusters using the number of posts per year
   - Identify "seed posts" and origin subreddits for templates occurring at least 200 times
   - Calculate PPMI (Positive Pointwise Mutual Information) between templates and subreddits to measure specificity
5. **Results:**
   - Entropy increases over time, suggesting steady variation in meme templates
   - New templates are more specific to their origin subreddit (Figure 7)
6. **Conclusion:**
   - Innovation occurs in meme templates, leading to linguistic change within semantic clusters.


## 7 Linguistic acculturation

**Linguistic Acculturation Study**

**Research Questions**:
- RQ4: Do veteran users in a subreddit use more community-specific templates?

**Methods**:
- Measure average specificity of user's posts in successful months after joining a subreddit
- Calculate PPMI (Positive Prefix Matching Index) of templates for each 30-day window starting from the first post
- Filter dataset to users with at least 10 lifetime posts and subreddits with at least 30 such users
- Sample up to 100 users from each subreddit to compute average across all subreddits

**Results**:
- Acculturated users use templates that are more specific to the communities they post in (Pearson's r= 0.074, p < 0.001)
- Aligns with existing literature on linguistic acculturation and theories in new media regarding memes as cultural capital
- Demonstrates user's assimilation into a shared language and identity through "correct" use of memes


## 8 Related work

**Meme Understanding and Modeling**

**Focus of Prior Research**:
- Meme understandng: classifying harmful messages, labeling emotions, detecting humor/figurative speech
- Generating open-ended explanations of visual humor using language models

**Contribution of Current Work**:
- Inferring semantic variables in an unsupervised approach
- Modeling template semantics separately from fills
- Contributing method of construing templates as semantic predicates to the body of research

**Related Research on Memes**:
- Understanding meme origins and spread
- Treating meme templates as discrete tokens

**Existing Research in Social Computing**:
- Qu et al. using CLIP to understand meme evolution
- Modeling high-level concepts indexed by particular variants

**Current Work's Approach**:
- Using fill text of memes to model low-level template semantics


## 9 Conclusion

**Meme Analysis: Understanding Semantics Through Multimodal Structures**

1. Analyzed memes as a linguistic form with sociolinguistic variation.
2. Proposed method to learn semantic representations of meme templates from an unlabeled dataset.
3. Demonstrated coherent, visually diverse clusters of semantically similar memes on Reddit.
4. Made clusters and code publicly available for further research.
5. Studied language variation and change in subreddits using these clusters.
6. Found socially meaningful variations between meme templates and textual language usage.


## 10 Ethical considerations

**Ethical Considerations**

* Data from ReddIT 2021 (publicly available)
* Potentially offensive, hateful, or sexual content
* No generative models trained
* Warn against generating outputs without caution.


## A Details on visually clustering templates

**Image Preprocessing for Template Clustering**

**Step 1: Removing Text Frames**
- Detection of potential text patches using a rectangular kernel
- Replacement of text patches with background color
- Identification of bounding box for source image without excess borders (Figure 9)

**Step 2: Image Hashing**
- Creation of a 64-bit perceptual hash for each preprocessed image in the dataset
- Preprocessed images used only for hashing, not other steps
- Examples of images with identical preprocessed versions in Figure 10 (Figure 10)

**Step 3: Hash Clustering**
- Computation of pairwise Hamming distance between all hashes
- Discarding pairs with a Hamming distance greater than 10
- Construction of a network of hashes, edges calculated as 11−dij for Hamming distance dij
- Use of Leiden algorithm with Constant Potts Model (CPM) quality function to cluster hashes
- Results in aggressively split clusters where each cluster is coherent but some memes may be merged (Figure 11)

**Duplicate Hash Clusters**
- Find that duplicate hash clusters often merge when generating semantic clusters.


## B Details on the semantic clusters

**Semantic Clusters and Edge Weights**

**Calculating Edge Weights:**
- Construct a weighted adjacency matrix for each template embedding
- Keep top 10 nearest neighbors: wa(b) = λra(b) where wa(b) is the weight of the edge between templates banda, ra(b) is the rank of cosine similarity

**Outputs:**
- RoBERTa model generates 784 semantic clusters with an average size of 8.7
- Statistics for cluster sizes: Table 2 in document
- Distribution of clusters is highly skewed: Figure 12
- Largest 103 clusters account for 50% of posts in Reddit dataset
- Largest 10 clusters account for 12% of all posts.


## C Model evaluation details

**Model Evaluation Details**

**Annotator Instructions**:
- Presented with pairs of images
- Answer two "yes/no" questions for each pair:
  1. **Semantic Similarity**: Can the text be copied and pasted, with minor changes, while still making sense?
  2. **Visual Similarity**: Do the images have the same characters, art style, etc.? If the layout is the same but the characters are different, mark it as "not visually similar"

**Evaluation Metrics**:
- Calculate metrics on the model judgments across all annotated pairs
- Allows evaluation on a larger set of annotations and highlights differences between models

**Findings**:
- **CLIP-based methods**: Included clusters that were visually similar but semantically different
  - Example: Cluster with Star Wars characters, despite different semantic functions (Figure 14)
  - Precision score for visual similarity was -2.08
- **Failure Case**: Over-indexing on visual similarity not limited to creating semantically incoherent clusters
  - CLIP-diff and Concat embeddings good at surfacing less-used variants of templates, but split into several stylistically delineated semantic clusters (Figure 15)


## D Further semantic cluster examples

**Meme Pairs for Annotation**:
- Figure 13: Example meme pairs for annotation

**Low Visual-Adjusted Precision Cluster**:
- Figure 14: This Concat cluster has a low visual-adjusted precision.
  - RoBERTa Cluster 0 (a)
  - Concat Cluster 2 (b)
  - Concat Cluster 31 (c)
  - Concat Cluster 134 (d)

**Stylistically Delineated Semantic Clusters**:
- Figure 15: Templates that are clustered together by RoBERTa appear in stylistically delineated semantic clusters in the Concat clusters.
  - Samples from each cluster:
    - **Cluster 0** (a)
    - **Cluster 1** (b)
    - **Cluster 10** (c)
    - **Cluster 30** (d)

**RoBERTa Clusters**:
- Figure 16: Samples from RoBERTa clusters.
  - Cluster 0 (a)
  - Cluster 1 (b)
  - Cluster 36 (c)
  - Cluster 23 (d)

**CLIP Clusters**:
- Figure 17: Samples from CLIP clusters.
  - Cluster 0 (a)
  - Cluster 1 (b)
  - Cluster 32 (c)
  - Cluster 22 (d)

**CLIP-diff Clusters**:
- Figure 18: Samples from CLIP-diff clusters.
  - Cluster 0 (a)
  - Cluster 1 (b)
  - Cluster 15 (c)
  - Cluster 29 (d)

**CLIP-diff + RoBERTa Clusters**:
- Figure 19: Samples from CLIP-diff + RoBERTa clusters.

---

Thank you to arXiv for use of its open access interoperability.
