# Sleeping Beauties in Meme Diffusion

[Sleeping Beauties in Meme Diffusion](https://arxiv.org/abs/1604.07532)

## Table of Contents
- [Sleeping Beauties in Meme Diffusion](#sleeping-beauties-in-meme-diffusion)
- [I Introduction](#i-introduction)
- [II Materials and Methods](#ii-materials-and-methods)
  - [A Datasets](#a-datasets)
- [III Results](#iii-results)
  - [A Exponential intervals between wake ups](#a-exponential-intervals-between-wake-ups)
  - [B The comparison between two wake ups](#b-the-comparison-between-two-wake-ups)
  - [C Modeling the popularity dynamics of sleeping beauties](#c-modeling-the-popularity-dynamics-of-sleeping-beauties)
- [IV Discussion](#iv-discussion)

## Sleeping Beauties in Meme Diffusion

**Sleeping Beauties in Meme Diffusion**

**Background:**
- Phenomenon of "sleeping beauties" in information diffusion: ideas or innovations experience hibernation before sudden spikes of popularity
- Widely found in citation history of scientific publications

**Findings:**
1. **Two consecutive sleeping beauties**: information, such as scientific topics, search queries, or Wikipedia entries (memes), will go unnoticed for a period and then suddenly attract attention, followed by another period of dormancy and another unexpected peak of popularity
2. **Intervals between two wake-ups**: follow an exponential distribution
3. **Second wake-up peak**: generally reaches its peak at a higher velocity than the first wake-up
4. **Volume of the first wake-up**: leads to even much higher popularity during the second wake-up with great odds
5. **Upgraded Bass Model**: presented to describe the dynamics of memes on different media, helping understand common mechanisms behind propagation of various memes and locating tipping points in marketing or science publications

**Data and Code:**
- Datasets and code employed in the research are available at: https://figshare.com/articles/Meme_popularity_and_difffusion/3187159/1


## I Introduction

**Meme Propagation and Sleeping Beauties**

**Definition of Meme**
- Cultural unit that spreads between individuals
- Analogy of genes for explaining idea propagation
- Diffusion studied extensively through various media

**Meme Diffusion in Different Media**
- Mathematical models, epidemiology, log-normal distributions used to understand growth and decline [2, 13, 23, 34, 36]
- Competition, homogeneity, network cooperativity impact spread [8–10, 16, 17, 37]
- Differential roles of individuals revealed [4] and [47]
- Simulation models established to replicate meme diffusion in Twitter [3, 41–44, 46]
- Common features of successful memes across online social networks [11, 12, 33, 35]

**Sleeping Beauties in Meme Diffusion**
- Phenomenon of delayed recognition and awakening in meme popularity [14, 15, 18, 21, 25, 38]
- Long-lived memes experience multiple sleeping beauties [24]
- Similarity between scientific publications, social media slang words [47]
- Common rule for meme diffusion through investigation of sleeping beauties

**Investigation of Sleeping Beauties in Meme Diffusion**
- Focus on three datasets: utilization volume of n-grams in scientific publication titles, search queries in Google, page view statistics of Wikipedia entries
- Memes come from different backgrounds for generalization
- Time granularities vary between year, month, week, and day for each dataset
- Six typical memes demonstrated with their popularity dynamics (Figure 1)
- Identification of two sleeping beauties in each meme's diffusion
- Exponential distribution of time intervals between two wake-ups
- Higher first spike leads to much higher popularity of the second spike.

**Modeling Sleeping Beauties in Meme Diffusion**
- Two sleeping beauties modeled based on classical Bass diffusion model [1, 29]
- Results reveal fundamental rule that drives popularity dynamics of memes in different media.


## II Materials and Methods

### A Datasets

**Datasets Used:**
- **PubMed**: metadata for all records from 1809 to 2013, including title, authors, and year of publication
- Segmented into uni-grams (n=1), bi-grams (n=2), and tri-grams (n=3)
- Obtained 741 memes with two remarkable sleeping beauties from the total dataset

**Wikipedia and Google Trends Datasets:**
- Contain search queries for Cartoon, comic, movie, and celebrity names
- Search frequency in Google Trends and page views in Wikipedia collected by [45]
- Data reflects collective attention on particular subjects in the real world

**Identifying Sleeping Beauties:**
1. Locate candidate peaks in meme's popularity dynamics by filtering out noisy cascades using an algorithm proposed by [31]
2. If there exists at least two peaks, the meme is labeled as a candidate sleeping beauty
3. Filter sleeping beauties according to the beauty coefficient of different peaks for each can didate meme
4. Define Awakening Time (ta) and Falling Asleep Time (tf) based on reference lines lat and lft in the time-popularity plane
5. Compute Beauty Coefficient (B1, B2) for the two sleeping beauties of filtered candidate memes using equations (7) and (8)
6. Memes with a linearly growing popularity or concave function citation trajectory have B=0 and B<0, respectively
7. If both B1 and B2 are greater than αS(t1) and αS(t2) (α=1/3), the candidate meme is identified as a sleeping beauty.


## III Results

**Sleeping Beauties in Different Media:**

- Two types of Sleeping Beauties found in different media
- Convincing proxies for common mechanism
- Exponential time intervals between wake-ups
- Faster propagation velocity and higher popularity for the second sleeping beauty
- Key characteristics to model meme popularity dynamics.


### A Exponential intervals between wake ups

**Meme Analysis: Sleeping Beauty Meme Patterns**

**Data Collection:**
- Obtain first and second awakening times (timeta1, t1, tf1, ta2, t2, tf2) for memes with two sleeping beauties in diﬀerent media
- Measure time intervals between wake ups (ta2 - tf1) for each meme

**Findings:**
- Time intervals follow stable exponential distribution s in diﬀerent media
- Coefficients are very close to each other: λ = [0.02, 0.08]
- Existence of a common and media-independent mechanism beyond meme diffusion

**Analysis:**
- Time intervals between wake ups predict second awakening time for observed memes
- Stable exponential distribution indicates temporal patterns may not be enough to predict second awakening
- Popularity definition varies based on data source: Google Trends (normalized search frequency), Wikipedia page views.

**Distribution of Time Intervals:**
- Figure 3 shows distributions of time intervals between wake ups for diﬀerent media and time granularities
- R values represent Pearson product-moment correlation coefficients and better ﬁttings have higher values
- N-grams of publication titles: y = 121.62e−0.0511x, R = 0.9463
- Search queries of Google Trends: y = 89.442e−0.0461x, R = 0.9117
- Wikipedia page views: y = 93.396e−0.0218x, R = 0.9523
- Time interval (day): y = 51.303e−0.0792x, R = 0.8994
- Time interval (month): y = 59.313e−0.0263x, R = 0.906
- Time interval (week): y = 100x, R = 0.9523 (for all data sources)


### B The comparison between two wake ups

**Meme Popularity During Wake Up Cycles**

**Total Popularity Comparison**:
- Total popularity during first wake up (m1) correlates with total popularity in second wake up (m2)
- Correlation coefficient: R = 0.6844 - 0.9081
- More attention in first wake up leads to more popularity in second wake up
- Figure 4 shows the correlation between m1 and m2 for different datasets

**Rising Velocity Comparison**:
- Average rising velocity in second wake up is 3-5 times faster than first wake up
- Rising velocity predicts formation of popularity spikes
- Figure 5 compares rising velocities in first (G1) and second (G2) wake up cycles

**Cascade Size Feature**:
- Consistent with finding that cascade size is a feature of the popularity rise


### C Modeling the popularity dynamics of sleeping beauties

**Bass Model for Memes Popularity Dynamics**

**Neglecting Detailed Factors**:
- Focus on general framework based on statistics from two "sleeping beauties"

**Upgrading the Bass Model**:
- Originally depicts diffusion of innovation and imitation
- Separate meme diffusion into two generations Gi (i=1,2)
- Define Si(t) as popularity during generation i at time t
- Define Fi(t) as diffusion rate of istdiffusion at time t

**Calculating Innovation Coefficient**:
- pi = Si(tai) + Si(tai+1)²
- Consider the popularity at next point cooperatively to estimate innovation coef

**Calculating Imitation Coefficient**:
- qi = ∫(qi/pi) * e^(-(pi+qi)*t) dt from ta1 to t2
- Represents internal factors shaping popularity dynamics

**Distribution of pi and qi**:
- All memes' pifollow a Gaussian-like distribution
- First beauty possesses higher averaged value than second
- Higher pi suggests more significant external factor influence in first beauty
- Higher qi cannot guarantee broader diffusion due to rising velocity in second beauty

**Model Evaluation**:
- Compare observed trend of popularity to simulated dynamics using Pearson correlation coefficient
- Obtain well simulation for locations and high correlation between simulated and observed popularity dynamics
- Validity of using mean to estimate innovation coef for different memes, domains, and time granularities.


## IV Discussion

**Understanding Information Diffusion through Internet**
- **Internet provides unprecedented opportunity to deeply understand dynamics of information diffusion**
- Previous studies focus on different factors influencing meme propagation:
  - Intrinsic infectiousness
  - System network structure
  - Time-spatial factors
- Nonparametric model may be a better way to investigate propagation of diﬀerent information

**Sleeping Beauties Phenomenon in Information Diffusion**
- **Study of sleeping beauties in citation history of scientific publications**
- Surprisingly, sleeping beauty phenomenon pervasively exists in diffusion of diﬀerent information from diﬀerent media
- Systematically explore basic features of two beauties and establish Bass-model-based approach to replicate popularity dynamics
- Promising result demonstrates mechanism behind diﬀerent memes and its function in driving popularity dynamics can be reflected by the two sleeping beauties

**Significance of Findings**
- Higher volume of ﬁrst spike leads to even much higher popularity of second spike with great odds, leading to outstanding peak in lifetime of diffusion
- Conventional thought is that outstanding peak is caused by tipping point or prince of sleeping beauty, so approach can help locate timing of tipping point in specific media (awakening time of second beauty)
- Findings and solutions can be important for practical applications like marketing business and scientific impact prediction

**Limitations**
- Investigations only focus on two remarkable beauties of memes from diﬀerent datasets, not further exploration of phenomenon of multi sleeping beauties
- Future work: Concentrate on memes with more than twice sleeping beauties and develop more detailed models to capture ﬁne-granular dynamics of memes and provide prediction both in volume and timing simultaneously.


---

Thank you to arXiv for use of its open access interoperability.
