# Toward Emerging Topic Detection for Business Intelligence: Predictive Analysis of `Meme' Dynamics

[Toward Emerging Topic Detection for Business Intelligence: Predictive Analysis of `Meme' Dynamics](https://arxiv.org/abs/1012.5994)

## Table of Contents
- [Toward Emerging Topic Detect ion for Business Intelligence: Predictive Analysis of ‘Meme’ Dynamics](#toward-emerging-topic-detect-ion-for-business-intelligence-predictive-analysis-of-meme-dynamics)
- [1. Introduction](#1-introduction)
- [2. Problem Formulation](#2-problem-formulation)
- [3. Predictive Analysis](#3-predictive-analysis)
	- [3.1 Predictability assessment](#31-predictability-assessment)
	- [3.2 Monitoring"](#32-monitoring)
	- [3.3 Prediction](#33-prediction)

## Toward Emerging Topic Detect ion for Business Intelligence: Predictive Analysis of ‘Meme’ Dynamics

**Detecting Emerging Topics for Business Intelligence: Predictive Analysis of 'Meme' Dynamics**

**Introduction:**
- Monitoring Web to spot emerging memes (distinctive phrases) as tracers for topics and consumer trends
- Early detection of new topics and trends beneficial for businesses

**Problem Statement:**
- Identifying measurables predictive of meme success
- Novel methodology presented for predicting which memes will propagate widely versus not

**Identifying Predictive Measurables:**
- Not traditional prediction metrics
- Subtle measures of meme dynamics

**Classifier Development:**
- Based on identified measurables
- Predicts if a given meme will propagate widely or not

**Utility Demonstration:**
- Analysis of online memes from second half of 2008.


## 1. Introduction

**Social Media's Impact on Businesses:**
- Popularity of social media challenges traditional business models (1-5)
- Control over information shifts from companies to consumers
- Opportunity for increased responsiveness and agility
- Significant amount of consumer opinions online (6,7)

**Importance of Monitoring Social Media:**
- Detection of emerging topics and consumer trends
- Quick address of negative information
- Leveraging positive "buzz" early on
- Strategic advantage in various industries

**Challenges in Exploiting Social Media Data:**
- Enormous scale of data makes automated methods necessary
- Identification of relevant topics among irrelevant content

**Automated Topic Discovery:**
- Research focus on detecting and characterizing emerging trends (1-3)
- Meme tracking method proposed for early discovery (8)
- Challenge: Most memes attract little attention before fading away
- Interest in predictive analysis of meme dynamics

**Limitations of Predictive Analysis:**
- Recent research questions the assumption that "viral" events are qualitatively different from non-viral ones (9,10)
- Individuals influenced by others: importance of social influence in prediction process

**Proposed Solution:**
- Careful consideration of individual influence through social networks
- Novel network dynamics-based metrics for predictive analysis
- Develop machine learning-based classification algorithm using these metrics
- Demonstration of utility and power through empirical study (second half of 2008)

**Findings:**
- Memes propagate for weeks, but useful predictions can be made within the first twelve hours after detection.


## 2. Problem Formulation

**Meme Dynamics:** Understanding and Predicting Meme Propagation in Online Sources

**Defining Interested Memes and Problem Formulation**
- Focus on phrases that appear as quoted material and propagate largely unchanged through sequences of news articles and blog posts.
- Data source: publicly available datasets archived at http://memetracker.org [15], extracted from Spinn3r's data.
- Goal: Develop capabilities for meme monitoring (identification of sensor blogs) and prediction (distinguishing successful and unsuccessful memes early in their lifecycle).

**Data Collection:**
- Time series data for slightly more than 70,000 memes obtained from [15].
- Randomly selected 100 "successful" and 100 "unsuccessful" meme trajectories based on post count.
- Collected a large Web graph (G_web) including websites mentioned in the meme time series and sampled text surrounding memes in posts.

**Characteristics of Meme Dynamics:**
- Strongly right-skewed distribution, most memes receive little attention while a few attract significant interest.
- Variable times to acquire first few or final posts: some memes gain popularity quickly while others take longer.

**Meme Monitoring and Prediction Problems:**
1. Investigate existence of good sensor blogs for memes, characterize them, and increase efficiency/effectiveness of detection method [8].
2. Identify measurables predictive of meme success (post sentiment, early meme dynamics), use them to classify memes into successful or unsuccessful groups early in their lifecycle.


## 3. Predictive Analysis

**Predictive Analysis**
- **Summary of Predictability Assessment Process**:
    - Applied to a simple model of meme diffusion
    - Identifies two features of network dynamics:
        - Useful for distinguishing successful and unsuccessful memes early in their lifecycle

- **Meme Monitoring Problem**:
    - Objective is to identify and characterize blogs and other online sources that consistently detect successful memes early in their lifecycles
    - Discovering such news sources would enable more efficient Web monitoring
    - Also useful for meme prediction, as the appearance of a meme on one or more of these sites may be an exploitable early indicator of meme success

- **Meme Prediction**:
    - Developed a machine learning-based classification algorithm that employs novel network dynamics metrics to accurately predict, very early in a meme's lifecycle, whether that meme will propagate widely or not
    - Performance of the prediction algorithm is illustrated through an empirical study involving successful and unsuccessful memes associated with topics of discussion that emerged in social media during 2008.


### 3.1 Predictability assessment

**Predictability Assessment Procedure for Social Diffusion**

**Overview:**
- Simple model of information diffusion: individuals combine beliefs and observations of others to decide whether to pass along new information
- Difficulty determining which characteristics are predictive of speed or reach of diffusion
- Proposed approach to predictability assessment in [11,12]

**Predictability Assessment:**
- Determine probabilities of reaching specific system state subsets (SSI) from candidate starting sets (CSS)
- Unpredictable if outcomes depend on uncmeasurable factors
- Identify measurables with highest predictive power to increase predictability

**Modeling Social Diffusion:**
- People affected by others' actions in social and information networks
- Dynamics of information diffusion dependent on network topology: right-skewed degree, transitivity, community structure, core-periphery structure

**Stochastic Hybrid Dynamical Systems (S-HDS):**
- Powerful mathematical formalism for representing social diffusion on realistic networks
- Feedback interconnection of discrete and continuous dynamical systems

**Results:**
- Predictability of social diffusion depends on network topology, particularly community and core-periphery structures
- Two candidate predictive features identified through theoretical analysis:
  1. Early dispersion across network communities predicts significant ultimate reach
  2. Early diffusion activity within the k-max shell (network core) predicts significant ultimate reach


### 3.2 Monitoring"

**Identifying "Better Than Random" Sensor Blogs:**
* Assemble set of 50 successful memes from [15]
* Form null hypothesis: blogs post on topics of interest, equally good at posting early, independent performance on other memes
* Determine if any blogs statistically significantly better than random at early detection of successful memes
* Characterize graph-topological properties of such ES blogs

**Results:**
* Approximately 2400 online sources post early for at least one meme
* Only 33 ES blogs identified as statistically significantly better than expected under null hypothesis (p < 0.05)
* Few ES blogs detect more than half of successful memes within first 3% of their lifespan
* Four ES blogs less likely than random to mention unsuccessful memes and contribute to meme success

**Graph Topology Measures:**
* In-degree: weak correlation with number of early detected memes, insufficient for discovering ES blogs
* K-core value: potential predictor of meme success, 67% of ES blogs located in the core of G web (top 0.1%) and 64% of strong ES blogs in k max-shell
* Simple way to identify influential blogs to monitor for early detection of emerging topics and associated memes.


### 3.3 Prediction

**Meme Prediction Using Machine Learning: Early Sensor Blogs and Online News Sources**

**Developing a Meme Classifier:**
- Goal: accurately predict meme success based on post content and dynamics
- Two classification algorithms tested: Naive Bayes (NB) and Avatar ensembles of decision trees (A-EDT)
- A-EDT algorithm is more accurate, results reported

**Meme Features:**
1. **Language-based measures**:
   - Bag of words feature vector x representing document text
   - Sentiment and emotion quantified using lexicons: IBM lexicon for sentiment, ANEW lexicon for emotion
2. **Dynamics-based metrics:**
   - #posts(t): cumulative number of posts mentioning the meme at time t
   - post rate(t): estimate of the rate of post accumulation at time t
3. **Network dynamics-based features:**
   - community dispersion(t): cumulative number of network communities containing posts at time t
   - #k-core blogs(t): cumulative number of k-core blogs with posts mentioning the meme at time t
   - #ES blogs(t): cumulative number of early sensor (ES) blogs with posts mentioning the meme at time t

**Early Sensor Blogs and Online News Sources:**
- Set of 33 online sources effective for detecting successful memes early in their lifecycles
- Four sources especially good at avoiding unsuccessful memes: chicago.craigslist.org, huffingtonpost.com, news.google.com, and online.wsj.com

**Meme Prediction Results:**
- A-EDT algorithm with language features achieves 66.5% prediction accuracy (ten-fold cross-validation)
- Simple language "intrinsics" not very predictive
- Network dynamics features show significant predictive power, even with limited early time series data
  - Accuracy: 83.5% at 12 hours, 91.5% at 24 hours, 92.8% at 48 hours, and 97.5% at 120 hours
- Predictive accuracy using most predictive intrinsic and dynamics features as a function of early time series availability (Figure 7)

