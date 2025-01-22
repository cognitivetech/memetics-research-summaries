# Exercise? I thought you said 'Extra Fries': Leveraging Sentence Demarcations and Multi-hop Attention for Meme Affect Analysis

[Exercise? I thought you said 'Extra Fries': Leveraging Sentence Demarcations and Multi-hop Attention for Meme Affect Analysis](https://arxiv.org/abs/2103.12377)

## Table of Contents
- [Abstract](#abstract)
- [Introduction](#introduction)
- [Related Work](#related-work)
- [Proposed Methodology](#proposed-methodology)
	- [Unimodal Feature Extraction](#unimodal-feature-extraction)
	- [Multi-hop Attention for Unimodal Feature Representation](#multi-hop-attention-for-unimodal-feature-representation)
	- [Attention-based Multi-modal Fusion (ATMF)](#attention-based-multi-modal-fusion-atmf)
	- [Context-aware Classiﬁcation](#context-aware-classiﬁcation)
- [Experiments](#experiments)
- [Experimental Results](#experimental-results)
	- [Unimodal Evaluation](#unimodal-evaluation)
	- [Bi-modal Evaluation](#bi-modal-evaluation)
	- [Comparative Study](#comparative-study)
	- [Ablation Analysis](#ablation-analysis)
	- [Interpretability of MHA-Meme](#interpretability-of-mha-meme)
- [Conclusion](#conclusion)

## Abstract

**Memes Analysis: Leveraging Multi-hop Attention for Emotion Classification**
* **Background:**
  * Internet is filled with memes (humorous, satirical, or ironic)
  * 33% of social media users aged 13−35 send memes daily
  * Virality depends on novelty of content
  * Memes can convey positive or negative messages
* **Challenges:**
  * Effective analysis of memes not adequately attempted
  * SemEval'20 organized pioneering attempt: Memotion Analysis competition
* **Objectives and Contributions:**
  * Propose multi-hop attention-based deep neural network framework, MHA-Meme
  * Leverage spatial correspondence between visual modality (image) and textual segments for fine-grained feature representations
  * Evaluate on SemEval'20 Memotion Analysis dataset: sentiment classification, affect classification, and affect quantification
  * Achieve state-of-the-art performances compared to top systems in the competition
  * Consistent results across all three tasks
  * Validation on another set of manually annotated test samples
  * Interpretability of MHA-Meme established.


## Introduction

**Memes: Understanding Their Emotional Expression**

**Introduction:**
- Internet memes have become a frequent entity on social media platforms
- Described as cultural ideas or symbols that transmit opinions, emotions, and expressions of a community
- Memes replicate and mutate like genes during propagation on social media
- Difficult to understand the inherent sentiment/emotion expressed by memes using automated methods due to textual and visual modalities

**Challenges:**
- Memes contain both textual and visual information that overlap but are complementary
- Monotonous information elimination is necessary for analysis
- Same image can convey different semantics based on text
- Subjective Perception Problem: individual perception varies, leading to discrepancy in annotated data

**Motivation:**
- Analyze emotion expressed by a meme through understanding both textual and visual modalities
- Eliminate monotonous information and consider the relationship between meme and reference situation

**Proposed Method: MHA-Meme (Multi-Hop Attention for Meme Analysis)**
1. Perform OCR to extract texts from meme
2. Segment text depending upon spatial positions
3. Process each textual segment separately using two attention frameworks - unimodal multi-hop attention (MHA) and attention-based multi-modal fusion (ATMF)
4. Combine all processed text segments in a multi-hop attention framework for classification
5. Enables leveraging fine-grained features for achieving the final goal

**Evaluation:**
- Evaluate MHA-Meme on Memotion Analysis dataset from SemEval-2020 shared task
- Perform extensive experiments for sentiment classification, affect classification, and affect quantification tasks
- Compare results with various existing systems on leaderboard and observe improved performance in a range of +0.5% to +2.2%
- Collect and annotate additional 334 memes to validate generalizability

**Analysis:**
- Ablation experiments demonstrating importance of extracting fine-grained features through segmented text and sophisticated attention mechanism for meme emotion classification
- Use LIME (Locally Interpretable Model-Agnostic Explanations) to visualize the importance of relevant features in prediction

**Contributions:**
1. Leverage correspondence between a meme and its constituent texts depending upon spatial locations
2. Propose an attentive framework that effectively selects and utilizes complementary features from textual and visual modalities to capture emotions expressed by a meme
3. Report benchmark results for all three tasks - sentiment classification, affect classification, and affect quantification
4. Validate the generalizability of MHA-Meme by collecting and annotating additional 334 memes and checking its performance
5. Establish interpretability of MHA-Meme using LIME framework

**Reproducibility:**
- Present detailed hyperparameter configurations in Table 2 and experiment section
- Full dataset and code for MHA-Meme publicly available at https://github.com/LCS2-IIITD/MHA-MEME


## Related Work

**Multimodal Sentiment Analysis (MSA)**
- Gaining increasing attention due to surge of multimedia data on Internet and social media
- Involves analyzing visual, acoustic, and textual modalities for accurately inferring emotion states

**Challenges in Multi-Modal Framework:**
- Utilizing and fusing relevant and complementary information for prediction

**Multimodal Fusion:**
- Three main types: early, late, and hybrid

**Early-Fusion:**
- Integrates multiple sources of data into a single feature vector
- Uses a single classifier for prediction from combined representation
- Can't exploit complementary nature of modalities and produces large redundant feature vectors

**Late-Fusion:**
- Aggregates decisions from separate sentiment classifiers trained on each modality
- Assumes modalities are independent in feature space, leading to limited performance when they are interconnected

**Hybrid-Fusion:**
- Employs an intermediate shared representation layer by merging modality-specific paths
- Most successful fusion strategy in literature

**Multitask Learning Framework:**
- Associates a cross-modal relevance score to each LSTM for MSA
- Introduces context-level inter-modal attention framework for sentiment and emotion prediction

**Meme Emotion Analysis:**
- Growing importance due to ubiquity of memes on social media
- Challenging due to inherent complex cognitive aspects of emotions

**Recent Work:**
- SemEval-2020 Task 8: Memotion Analysis (Sharma et al., 2020)
- Top participants used various methods for unimodal feature extraction, such as FFNN, Naive Bayes, ELMo, MMBT, BERT, Inception-ResNet, Polynet, DenseNet, and PNASNet
- None of these methods can guarantee non-redundant features from two highly correlated modalities to capture every aspect of emotions expressed by a meme.

**Proposed Approach:**
- Introducing multi-hop attention and image encoding filter based sentiment classifier network which extracts complementary features from both modalities with overlapping information
- Demonstrates significance of spatial information for effective fusion of both modalities
- Extensive experiments reveal importance of text segmentation and fine-grained feature extraction to capture multiple aspects of emotion for meme affect analysis.


## Proposed Methodology

**Proposed System for Meme Analysis: MHA-Meme**

**Input**: Meme is taken as input

**Step 1: Text Extraction**
- Google OCR Vision API used for text extraction
- Segmented text (ti) and image (I) pair extracted

**Step 2: Feature Extraction using Bidirectional LSTM and VGG-19 networks**
- Each segmented text and image pair encoded through:
  - **Bidirectional Long Short-Term Memory (LSTM)** network
  - **VGG-19** convolutional neural network

**Step 3: Text-aware Filtering**
- Fine-tune the image encoding through a text-aware filter
- Restrict system to extract features from spatial region of text in meme

**Step 4: Unimodal Multi-hop Attention (MHA) Framework**
- Extract relevant features from respective encodings for affect classification and quantification
- Positive effect on sentiment classification, suggesting capability of extracting diverse features

**Step 5: Multi-Modal Fusion**
- Employ attention-based multi-modal fusion (ATMF) mechanism to leverage correspondence between textual and visual modalities

**Repeat for each Textual Segment**
- Compute multimodal feature representations for each text segment

**Step 6: Combine Representations through MHA Module**
- Attend to relevant segments for the given meme using another multi-hop attention module
- Context-aware attended representation obtained

**Output**: Final prediction is fed to sequence of fully-connected layers for output

**Affect Classification and Quantification**
- Learn all four affect dimensions together in joint framework

**Architecture**: Figure 2 shows the architecture of MHA-Meme.


### Unimodal Feature Extraction

**Textual Feature Extraction:**
- Use 200-dimensional GloVe word embeddings for encoding each word of the textual segment
- Achieve 77:22% word coverage, initialize OOV words randomly
- Train network in dynamic mode to fine-tune embedding layer via backpropagation
- Use a 2-layered BiLSTM with hidden dimension u for textual feature extraction
  * Maps 200-dimensional embedded word vectors to 2-dimensional hidden states
  * Forward, backward, and combined hidden representations: ht, ht−1, ht ∈ R2u
  * Use u=256 to match with visual feature dimension

**Image Encoding Filter:**
- Use pretrained VGG-19 model on ImageNet for extracting local feature maps
- Extract 7x7x512 feature maps from last pooling layer (pool5) of VGG-19
- Reshape the matrix into a matrix F(f₁;…;fm), where each fk corresponds to a local spatial region
- Ensure textual modality does not establish direct correspondence with image content by filtering redundant visual features
  * Define an affinity matrix C ∈ Rn×m based on similarity between feature vector pairs (hi, fi)
    + Use tanh(WHbF/uni22BA) for computing the similarity matrix Wb ∈ R512x512 during training
  * Compute normalized weight hij to denote relevance of word i to image region j
- Weighted summation of all word representations: ahj = exp(cij)/∑n=1 exp(cij)
- Relevance matrix R(fi;ahj) as cosine distance between attended sentence vector ahj and image region feature fi
  * Use 1−f⋅ahj/parallel.alt1fi/parallel.alt1ahj/parallel.alt1 to filter the redundant features
- Weighted summation of all regions gives modified image representation U: U = m∕∑j=1 R(fi;ahj)⋅fi.


### Multi-hop Attention for Unimodal Feature Representation

**Multi-hop Attention for Unimodal Feature Representation**

**Semantic Attention Mechanism**:
- Some words in a sentence have higher relevance to a particular task
- Semantic attention mechanism is beneficial for NLP tasks

**Visual Attention Mechanism**:
- Some visual regions are more informative to represent certain emotions
- Visual attention mechanism is effective for emotion representation

**Traditional Self-attention Mechanism**:
- Focuses on a specific component, reflecting only one aspect of the semantics
- Cannot cater to diverse and task-specific relevant features

**Multi-hop Attention Mechanism**:
- Attends to diverse and task-specific relevant features in a joint-framework
- One hop attends to features relevant for humor classification
- Other hop focuses on sarcasm detection

**Computation of Multi-hop Attention**:
1. Given a unimodal feature matrix (textual/visual): H ∈ Rn×512 or U ∈ Rm×512
2. Extract k distinct set of relevant features corresponding to the input representation
3. Compute attention weight matrices A ∈ Rk×n for textual representation and B ∈ Rk×m for visual representation
4. Use softmax function along second dimension to normalize the weights
5. Compute resulting embedding matrices M ∈ Rk×512 and N ∈ Rk×512 using attention weight matrices and unattended features

**Parameters**:
- Wh1, Wu1, Wh2, Wu2: Parameter matrices for textual and visual modalities to be learned during training
- d: Dimensionality of the hidden layer
- k: Number of distinct sets of relevant features to extract
- α: Hyperparameter for softmax function


### Attention-based Multi-modal Fusion (ATMF)

**ATMF Multimodal Fusion Network**

**Overview**:
- Utilizes attention-based mechanism to fuse unimodal features from textual and visual modalities
- Different contributions of same modality for different utterances and meme samples

**MHA-Meme Algorithm**:
1. **OCR and Segmentation (M)**: Extract text segments from the meme image
2. For each segment:
   a. BiLSTM (tseg): Process text using bi-directional LSTM
   b. VGG 19pool5(I): Extract visual features using pretrained model
   c. ImageEncodingFilter (Hseg, Fseg): Combine and normalize textual and visual features
3. Multi-hopAttention (Hseg): Generate modality attention scores
4. Multi-hopAttention (Ffiltseg): Generate additional attention to reduce repetitive features in short text segments
5. ATMF (Mseg, Nseg): Fuse weighted textual and visual features using attention scores
6. Classifier: Predict affect classes based on fused multi-modal representation

**Image Encoding Filter**:
1. Compute affinity matrix C
2. Calculate weights for each modality (textual and visual) based on affinity scores
3. Concatenate weighted modalities and perform final attention computation
4. Return the filtered representation

**Multi-Modal Fusion Network**:
- Consists of two major parts:
   a. Modality attention generation
   b. Weighted feature concatenation
- Uses a sequence of dense layers followed by softmax to generate modality attention scores
- Original unimodal features are weighted using their respective attention scores and concatenated together

**Dataset Statistics**:
- **Memotion Analysis (Sharma et al. 2020)**: Train, Test A, and Test B datasets
  - Train: 6601 text segments, 14032 image segments
  - Test A: 1879 text segments, 4184 image segments (original test set)
  - Test B: 334 text segments, 748 image segments (developed to validate generalization of MHA-Meme)

**Affects**:
- A meme can belong to one or more affective classes.


### Context-aware Classiﬁcation

**Context-Aware Classification**
* Final stage of network
* Leverage contextual multimodal representation for classification
* Sentiment or affective dimension may relate to specific textual segments
* Employ multi-hop attention module at meme-level
	+ Highlight diverse features for underlying tasks
* Matrix X contains multimodal features for each textual segment: X ∈ R^(512x12)xL
* Number of segments in a meme is L
* Each xi ∈ R^512 is the modal feature representation for ith segment
* Multi-hop segment-level representation X∗ is flattened and forwarded to softmax layers
	+ One softmax layer for sentiment classification
	+ Four softmax layers each for affect classification and quantification tasks
* Z = softmax(X\*\nW\_soft+b\_soft)
* y^ = arg max_j(Z[j]) ∀j∈class
* W\_soft and b\_soft are learnable weights
* ^y is the final predicted class.


## Experiments

**Dataset:**
- Memotion51.0 dataset (Sharma et al., 2020) for meme analysis
- Consists of 8,480 manually annotated English memes from 52 unique and globally popular categories
- Annotated through Amazon Mechanical Turk with three sentiment classes (positive, neutral, negative) and four affect classes (humor, sarcasm, offense, motivation)
- Contains quantification scores for each affect expression
- Addresses the "Subjective Perception Problem" by performing multiple annotations and adjudicating through majority voting
- Each instance includes an image (meme) and unsegmented OCR-extracted text
- Original dataset has 6,992 training and 1,879 test memes

**Data Preprocessing:**
- Extract textual segments using Google OCR Vision API for building models
- Encountered alignment issues with ~500 memes in the training set, manually corrected most of them
- Extracted 14,032 textual segments from 6,601 memes in the training set and 4,184 textual segments from 1,879 memes in the test set
- Distributions of sentiment and affect classes for both train and test sets are provided

**Hyperparameters:**
- Used for training MHA-Meme on Pytorch framework with a Tesla T4 GPU
- Employed pre-trained GloVe Twitter embedding model for fine-tuning during training
- Randomly initialized with zero-mean Gaussian distribution of standard deviation 0.02
- Assigned larger weights to minority classes in loss calculation to minimize the effect of label imbalance
- Trained using Adam optimizer and negative log-likelihood (NLL) loss as the objective function

**Baselines for Comparison:**
- Guoym: Five base classifiers combined through data-based and feature-based ensemble methods, ranked 2nd to 1st in three subtasks
- Vkeswani IITK: Simple feedforward neural network with Word2vec embedding, utilized domain knowledge to improve performance
- George.Vlad Eduardgzaharia UPB: Multimodal multi-task learning architecture combining ALBERT for text encoding and VGG16 for image representation
- Honomai Hitachi: Fine-tuned pre-trained visual and textual models to capture cross-modal correlations between modalities
- Mayukh Memebusters: Transfer learning for image and text feature extraction using attention-based recurrent architectures
- Gundapu Sunil: Extracted textual features with LSTM and GloVe word embeddings, visual features with pre-trained VGG16, fused them for classifications
- Souvik Mishra Kraken: Hybrid neural Naive-Bayes, Support Vector Machine, and Logistic Regression to solve multimodal classification problem
- NowsheCSECU KDE MA: Convolution and BiLSTM based attention framework to jointly learn visual and textual features from a meme
- Prhlt upv: Pre-trained BERT for textual features and VGG19 for visual features, combined them using simple concatenation-based fusion technique
- Xiaoyu: Similar to Prhlt upv but used DenseNet instead of ResNet for visual feature extraction


## Experimental Results

**Experimental Results:**

* Reported findings for MHA-Meme and its variants
* Macro-F1 score evaluation metric used
* Evaluated on Test A and Test B sets
* Comparison with state-of-the-art systems from SemEval-2021
* Micro-F1 reported during ablation study.


### Unimodal Evaluation

**Results Obtained**
* Unimodal Inputs: BiLSTM and BERT used for encoding text
  + Macro-F1 scores: sentiment classification (0.338, 0.336), affect classification and quantification (0.421, 0.302) with BiLSTM; (0.422, 0.295) with BERT
* Performance gain after including OCR text segments:
  + BiLSTM: macro-F1 scores improved for all tasks (+1.4%, +5.4%, +1.7%)
  + BERT: performance improvement of +1.3%, +5.0%, +1.1%
* Textual segmentation leads to better performance and supports hypothesis
* Inferiority of BERT compared to BiLSTM with both segmented and unsegmented inputs:
  * Shorter text segments in memes cause LSTM's performance advantage
  * Lack of context in noisy, grammatically incorrect text
* Visual modality: pre-trained image feature extractors used (InceptionV3, VGG-16, and VGG-19)
* Macro-F1 scores for sentiment classification, affect classification, and affect quantification with VGG-19: 0.325, 0.413, 0.292 respectively.
* Marginally better results observed with VGG-19 compared to other two tasks (0.2-0.5% performance improvement)
* Choice of using VGG-19 encoding for all further experiments.


### Bi-modal Evaluation

**Multimodal Meme Classification: Comparison of BiLSTM and BERT**

**Combining Modalities**:
- Combine text and image encoding in a single system
- Experiment with BiLSTM and BERT variants for textual encoding

**Results**:
- **BERT Variant**: Macro-F1 scores: 0.356, 0.508, 0.325 for sentiment classiﬁcation, affect classiﬁcation, and affect quantiﬁcation, respectively
- **BiLSTM-based MHA-Meme**: Macro-F1 scores: 0.376, 0.523, 0.332 for sentiment classiﬁcation, affect classiﬁcation, and affect quantiﬁcation, respectively
- Improvements of +2.0%, +1.5%, and +0.8% against BERT-based system for the three tasks, respectively
- **BiLSTM encoding** preferred over BERT in proposed MHA-Meme
- Bi-modal system obtains +2.4%, +4.8%, and +1.3% improvements against best unimodal scores for the three tasks, respectively
- Textual modality has higher influence on overall performance as meme text contains richer information than images

**Table 3: Results on Test Bin**
- Better results obtained with multimodal inputs compared to both text and image unimodal inputs
- BiLSTM variant yields the best results for all tasks.


### Comparative Study

**Comparative Study Results**

**Baseline vs. State-of-the-art Systems**:
- Official evaluation metric: Macro-F1 score from "Memotion Analysis" shared task (Sharma et al. 2020)
- **MHA-Meme**:
  - Performs better on TestA than BERT variant on bi-modal input
  - Generalizes well on unseen random samples in TestB
  - Consistent performance across two test sets

**Comparison to State-of-the-art Systems**:
- MHA-Meme outperforms top three systems (on average) for sentiment classification:
  - Vkeswani IITK: 0.35446
  - Gyoum: 0.35197
  - Aihaihara: 0.35017
- Improvement over top system, "Vkeswani IITK": +2.2% (0.35446 vs. 0.37621)
- MHA-Meme achieves new state-of-the-art performance for sarcastic classiﬁcation in affect classification:
  - Previous best: 0.51590 (George.Vlad Eduardgzaharia UPB)
  - MHA-Meme: 0.51936
- Improvement over previous best in humor and motivation classiﬁcation: −0.3% (0.52670 vs. 0.52992, 0.53102)
- MHA-Meme ranks third for offense classiﬁcation: 0.51731

**Fusion Mechanisms Comparison**:
- BiLSTM + OCR + VGG19 (Single-hop and Multi-hop attention)
- ATMF vs. D-Fusion
- MHA-Meme performs better than top system in four out of five comparisons across affect classification and quantiﬁcation tasks.


### Ablation Analysis

**Multi-hop Attention and Fusion Modules in MHA-Meme**

**Ablation Studies**:
- Multi-hop attention introduced by Lin et al. (2017) to represent overall semantics of an utterance
- Important for meme sentiment analysis as one utterance can capture multiple emotions
- Incorporate multiple hops of attention mechanism over the same input
- Single-hop vs. multi-hop performance shown in Table 5
- Multi-hops yields ~2% improvement for different model variants on Test A and Test B

**Attention-based Multimodal Fusion (ATMF)**:
- Employs a hierarchical attention mechanism to amplify the contribution of important modality during fusion
- Compared with:
  - **D-Fusion**: Direct fusion, no textual segmentation at input
  - **AT-Fusion**: Originally introduced by Poria et al. (2017b), takes audio, visual, and textual modalities as input
    - Modified to exclude audio modality for the experiments

**Results**:
- Reported scores on Test A and Test B in Table 5
- Superiority of ATMF compared to D-Fusion and AT-Fusion observed.


### Interpretability of MHA-Meme

**Interpreting Complex Deep Neural Models: Meme Understanding**

**Problem of Interpreting Complex Models**:
- Nontrivial problem
- Important for further exploration
- **Meme understanding**:
  - Requires high level of abstraction, background knowledge, and subjectivity
  - Challenging due to various topics, subjects, and genres in Memotion 1.0 dataset

**Model Performance Analysis**:
- **Success of the model**: Heavily depends on simultaneous image and text understanding
- **LIME (Locally Interpretable Model-Agnostic Explanations)**:
  - Consistent model-agnostic explainer to explain predictions in an explicated and faithful manner
  - Performs by learning an interpretable model locally around the prediction

**Example Meme Analysis**:
- Correctly classified as 'positive' sentiment
- **Image analysis**: Smiling face of character contributes to positive class, with green pixels
- **Text analysis**: Words 'SMILE' and 'MORE' have significant contributions to positive class, reducing prediction probability without them
- **Attention weights analysis**: Word 'SMILE' has highest attention weight in both segments

**Conclusion**:
- MHA-Meme framework extracts and attends to relevant features from input representations.


## Conclusion

**MHA-Meme: An Attention-Rich Neural Framework for Affect Analysis of Memes**

**Tasks Addressed**:
- Sentiment classification
    - Positive, Negative, Neutral labels
- Affect classification and quantification
    - Humor, Sarcasm, Offense, Motivation dimensions

**Proposed Framework**:
- MHA-Meme: Analyzes the interaction between visual and textual modalities at fine-granular level
- Extracts fine-level feature representations for each textual segment in a meme
- Multi-hop attention module for unimodal feature extraction
- Attention-based multimodal fusion module to compute modality interaction
- Combines enriched multimodal representations via multi-hop attention layer and outputs for classification

**Performance**:
- Evaluated on "Memotion Analysis" dataset of SemEval-2020 shared task
- Extensive experiments for each task, compared against 11 baseline systems
- Performance improvements:
    - Sentiment classification: +0.5% to +2.2%
    - Affect classification and quantification: Consistent good performances (1st-3rd place) across 8 affect dimensions
- Baseline systems did not report consistent performance for all tasks or affect dimensions.


---

Thank you to arXiv for use of its open access interoperability.