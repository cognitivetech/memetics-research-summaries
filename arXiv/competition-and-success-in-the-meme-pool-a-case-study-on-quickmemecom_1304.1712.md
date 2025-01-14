# Competition and Success in the Meme Pool: a Case Study on Quickmeme.com

[Competition and Success in the Meme Pool: a Case Study on Quickmeme.com](https://arxiv.org/abs/1304.1712)

## Table of Contents
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 The Data](#3-the-data)
- [4 Detecting Meme Relationships](#4-detecting-meme-relationships)
	- [4.1 Null Model](#41-null-model)
	- [4.2 Meme Collaboration](#42-meme-collaboration)
	- [4.3 Meme Competition](#43-meme-competition)
- [5 Meme Success](#5-meme-success)
	- [5.1 Meme Features](#51-meme-features)
	- [5.2 Measuring Success](#52-measuring-success)
	- [5.3 Extracting and Interpreting the Decision Tree](#53-extracting-and-interpreting-the-decision-tree)
- [6 Conclusion and Future Works](#6-conclusion-and-future-works)

## 1 Introduction

**Internet Meme Research: A Case Study on Quickmeme.com**

**Background:**
- Social media allows insights into information and culture (Dawkins, 1976)
- Memes as cultural units that spread from mind to mind
- Internet memes leave traceable footprints for analysis

**Previous Research:**
- Focuses on interactions between users in networks
- Studies meme ecology rather than characteristics and dynamics

**Objective:**
1. Prove memes on Quickmeme have fundamental meme traits (interaction through competition and collaboration)
2. Study characteristics leading to successful memes in Quickmeme

**Contributions:**
- Study intrinsic meme characteristics without focusing on network effect
- Detect and study memes in social media using high quality data from Quickmeme
- Identify competition and collaboration in the meme pool of Quickmeme
- Define characteristics leading to successful memes in the dataset

**Methodology:**
1. Review related literature: information spread, memetics (Section 2)
2. Present data source and cleaning process (Section 3)
3. Analyze Quickmeme methodology and evidence for relationships (Section 4)
4. Define characteristics leading to successful memes in the dataset (Section 5)
5. Conclude with future developments (Section 6).


## 2 Related Work

**Topics Covered in Memetics Research:**
- **Meme ecology**: study of how social network and media allow memes to spread
- Competition among memes (Wei et al., 2012; Weng et al., 2012)
- Information spread analysis in networks (Goyal, Bonchi, and Lakshmanan, 2008; Hoang and Lim, 2012; Berlingerio, Coscia, and Giannotti, 2009; Myers and Leskovec, 2012)
- Memes in social media websites (Leskovec, Backstrom, and Kleinberg, 2009; Fowler and Christakis, 2010)

**Related Works:**
- **Bauckhage (2011)**: addresses issues of collaboration and competition in internet memes but does not focus on meme functionality.
- Researchers in computer science have studied various aspects of user behavior in social media websites, such as emergence of conventions, critical feature selection, privacy, "follow" and friendship dynamics (Kooti et al., 2012; Tang and Liu, 2012; Quercia et al., 2012; Pennacchiotti et al., 2012; Adamic et al., 2011).
- Pioneering works in memetics (Hofstadter, 1991; Brodie, 2004; Lynch, 1999) focus on memes but are not data-driven, as internet memes leave a measurable footprint.


## 3 The Data

**Quickmeme Meme Analysis**

**Quickmeme Overview**:
- Website provides system to create and implement memes
- Users provide humorous captions following tacit concept of the meme

**Meme Definition**:
- Combination of a picture and a concept linked to it
- Symbolized as "m"
- Implementation refers to the picture with a particular caption

**Quickmeme Dynamics**:
- Users are versatile in meme use, combining, evolving, and collaborating on memes
- Website provides scoring system as proxy for meme "success"
- Users can vote on memes: "awesome", "average", or "bad"
- Memes with sufficient popularity can be "Featured"

**Data Collection**:
- Crawled 499 memes with at least one featured implementation on October 15, 2012
- Downloaded 178,801 meme implementations in total

**Meme Rating Distribution**:
- Quickmeme saw growth in positive ratings during the first weeks
- Reached peak in Q1 of 2012, then slowly declined
- Power law distribution: some very popular memes, most have low rating
- Noticeable deviations: hunch around 500-2,000 ratings and exponential cutoff
- "Front page" effect: popular memes receive extra ratings from being exposed on the website's front page.


## 4 Detecting Meme Relationships

**Influence of Memes on Popularity:**
- **Competition**: Negative influence between memes leading to lower ratings for one meme due to success of another.
- Weekly total ratings (w1(m) to w53(m)) are used to determine meme's success.
  - Sum of ratings collected by all implementations in a week: w(m) = Pn i=1 j=1 wij(m).
- If an increase in one meme's success causes a fall in another, they are said to be competing.
- Meme rating vector (w(m)) determines meme's success.

**Analysis:**
- Weekly total ratings for memes analyzed to identify competition or collaboration.
- Competition: negative influence on each other's popularity.
- Collaboration: opposite effect, positive influence on each other's popularity.

**Meme Rating Vectors:**
- Determined by looking at a meme's success (rating vector).
- Weekly total ratings collected from all implementations in a week (w1(m) to w53(m)).
- Sum of these weekly ratings gives the meme rating vector (w(m)).


### 4.1 Null Model

**Null Model**
- Two meme rating vectors may not be comparable due to:
  - **Competition**: One meme is consistently more popular than another, leading to false positive correlations even when there's no competition.
  - **Website popularity fluctuations**: Fluctuations in ratings can be explained by meme and website popularity without indicating competition or collaboration.
- **Null model** is used to eliminate these meaningless fluctuations:
  - Preserves total sums of rows (memes) and columns (weeks) in the matrix.
  - Allows calculation of ratio between observed and expected values for each cell.

**Normalized Meme Rating Vectors**
- Observed cell values are tested against corresponding null model cell values.
- Normalized values (ranging from 0 to 1) represent the ratio between observed and expected ratings, given website popularity and meme overall popularity.
  - If expected value is 0, the ratio is undefined but treated as 1.
  - If expected value is less than 1, it's treated as equal to 1 for simplification.

**Rating Vectors Comparison**
- Calculate conditional probabilities:
  - Probability of meme being more/less popular than expected given the popularity of another meme and overall website.
- Memes are in **competition**:
  - If all the following inequalities hold true:
    - Probability of one meme being more popular given the other is lower than its independent probability.
    - Reverse for both memes.
- Memes are in **collaboration**:
  - If all the following inequalities hold true:
    - Probability of one meme being more popular given the other is higher than its independent probability.
    - Reverse for both memes.

**Discarding Relationships**
- Discard competition and collaboration relationships if:
  - Memes were not present together on Quickmeme website for more than 25 weeks.
  - Check using N1\nm;w and N2\nm;w null matrices to ensure observed relationships are not due to external factors.

**Output: Cm;m Matrix**
- Resulting matrix (Cm;m) contains rows and columns as memes, with values of 1 for collaboration, -1 for competition, and 0 for independence.


### 4.2 Meme Collaboration

**Meme Collaboration**

- **Cm;m Matrix**: Symmetric square matrix (499x499) representing reciprocal meme relations
- **Probabilities for Memes in Cluster #45:**
  - Success against "First World Problems": 20.75%, 18.87%
  - Success against "Hipster": 79.25%, 81.13%
- **Success and Unsuccessful Cases:**
  - Both memes successful: 60.00%, 54.55%
  - Meme1 successful, Meme2 unsuccessful: 11.63%, 9.52%
  - Meme1 unsuccessful, Meme2 successful: 40.00%, 45.45%
- **Meme Implementation of "Scumbag Reddit meme":** Figure 7 illustrates two different variations.


### 4.3 Meme Competition

**Meme Competition**
- Some memes have disproportionate amount of anti-correlations with other memes
- Explanation: Users use these memes to critique other memes

**Examples:**
- "Scumbag Reddit" (SR) meme used for self-critique on Reddit.com
  - SR is the second most competitive meme, as shown in Figure 7
  - Users often adopt this meme to criticize other memes:
    * Figure 7(a): refers to "First World Problems" memes
    * Figure 7(b): refers to "Hipster" memes

**Impact on Success Odds:**
- The popularity of SR meme negatively influences the success odds of other memes and vice versa, as shown in Table 3.


## 5 Meme Success

**Characteristics of Successful and Unsuccessful Meme:**

**Defining Meme Features**:
- Study characteristics correlated with meme success
- Define set of meme features:
  * **pmi(<=mi)>1**: Probability of successful meme given a specific example
  * **pmi(<=mi)<1**: Probability of unsuccessful meme given a specific example
  * **pmi(=>mi)>1j=>mj)>1**: Success probability when both **mi** and **mj** are greater than 1
  * **pmi(=>mi)>1j=>mj)<1**: Success probability when **mi** is greater than 1 but **mj** is less than 1
  * **pmi(<=mi)<1j=>mj)>1**: Success probability when **mi** is less than 1 but **mj** is greater than 1
  * **pmi(<=mi)<1j=>mj)<1**: Success probability when both **mi** and **mj** are less than 1

**Determining Meme Successfulness**:
- Establish criterion for successful/unsuccessful meme

**Meme Probability Analysis**:
- Use decision tree algorithm to describe how features impact success probability.


### 5.1 Meme Features

**Features of Meme Success:**
- **Number of collaborators**: memes classified as highly collaborative, average or low based on number of collaborations
  - Highly collaborative: more than 77 collaborators (172 memes)
  - Average collaborative: between 50 and 77 collaborators
  - Lowly collaborative: less than 50 collaborators (174 memes)
- **Number of competitors**: memes classified as highly competitive, average or low based on number of competitors
  - Highly competitive: more than 77 competitors (172 memes)
  - Average competitive: between 50 and 77 competitors
  - Lowly competitive: less than 50 competitors (174 memes)
- **Meme organism**: memes classified as part of an organism or not
  - In organism: present in a cluster with at least two other memes
  - Not in organism: not part of any such cluster
- **Peak popularity relative to average**: memes classified as above or below average based on the ratio of peak popularity to average
  - Above average: peak popularity 25 times or more higher than average (number unknown)
  - Below average: peak popularity lower than 25 times the average (number unknown)


### 5.2 Measuring Success

**Measuring Meme Success**
- Many ways to measure meme success
- Cannot use total number of ratings as proxy due to pop-ularity peak being a feature
- Instead, look at number of **implementations**: more implementations = more persistent in people's minds
- For each **meme mi**: check if **jmij** (number of its implementations) is higher than the average
- If jmij > average, consider the meme successful, otherwise unsuccessful
- Threshold = 358 implementations based on 178,801 meme implementations and 499 memes
- Figure 10 depicts distribution of number of implementations per meme, black line represents threshold
- Table 4 reports number of (un)successful memes

**Example: Socially Awkward Penguin Mememe**:
- Has 1,413 meme implementations, making it a successful meme
- Other features:
  - 48 competitors
  - 285 collaborators
  - Popularity peak at 3.91 (average popularity)
  - In an organism with 11 other memes
- According to Table 4, this meme is: **competition**: below average, **collaboration**: above average, **InOrganism**: True, **peak**: below average, **Successful**: True.


### 5.3 Extracting and Interpreting the Decision Tree

**Decision Tree Algorithm for Memes Success**

**Procedure**:
- Each **meme** generates a record using the described procedure
- Records are used as input to a **decision tree algorithm**
- The **target variable** is "Success"
- Decision tree implementation based on (Borgelt and Timm 2000)
- Tree pruned if it contains too many levels
- Some leaves merged for interpretation

**Final Decision Tree**:
- Nodes contain the percentage of successful memes in that node
- **Root node**: Baseline probability of a meme being successful (17.47%)
  - Out of 499 memes, 35.47% were successful
- Each node split based on features that best separate successful from unsuccessful memes

**Key Findings**:
- **Peak**: If there was a high popularity peak, odds of being successful lower (13.41%)
  - Memes with low popularity peaks have higher success probability (54.47%)
- High popularity peaks make the number of competitors negatively correlated to odds of being successful:
  - Large/average number of competitors: 6.25% and 12.65% chance of success, respectively
  - Small amount of competitors: slightly more likely to be successful (17.3%)
- For memes without high popularity peaks, number of competitors positively correlated with success odds:
  - Highly competitive memes: 75% chance of success
  - Average/lower than average competitors: 36.48% and 38.02% chance of success, respectively
- For memes without a peak and low number of competitors, higher number of collaborators correlates with success odds
- For memes without a peak and high number of competitors, best correlation is when it is in a **coherent meme organism** or has many collaborations with other memes
  - Increased odds of being successful (80.3%)
- If the meme is not in an organism, having a high number of collaborators still highly correlates with success rate (79.31%)
- Having a low/average number of collaborators decreases success odds to 58.62%

**Explanation**:
- If a meme has both high popularity peaks and many competitors, it may not be used frequently enough due to similarity to other memes
- If there is no popularity peak, users are likely to stick with the meme, keeping it in use together with other memes, thus increasing competition


## 6 Conclusion and Future Works

**Approach to Studying Memes: An Empirical Perspective**

**Background:**
- Presentation of an empirical approach to meme study
- Focus on internet memes in Quickmeme.com
- Opposes network approach, emphasizes cultural patterns

**Key Findings:**
- Meme characteristics influence popularity odds
- Memes compete and collaborate in larger ensembles
- Future developments: combining network approach, dynamic timeline analysis

**Related Work:**
- [Adamic et al. 2011] Ratings of friends without making enemies
- [Bauckhage 2011] Insights into internet memes
- [Berlingerio et al. 2010, 2009] Mining temporal dimension in information propagation
- [Gotelli and Graves 2006] Null Models in Ecology
- [Goyal et al. 2008] Discovering leaders from community actions
- [Harvey et al. 1983] Null models in ecology
- [Myers and Leskovec 2012] Clash of the contagions: cooperation and competition in information diffusion

**References:**
- Brodie, R. (2004). Virus of the Mind: The New Science of the Meme
- Dawkins, R. (1976). The Selfish Gene
- Fowler, J. H., & Christakis, N. A. (2010). Cooperative behavior cascades in human social networks
- Hoang, T.-A., & Lim, E.-P. (2012). Virality and susceptibility in information diffusions
- Hofstadter, D. R. (1991). Metamagical Themas
- Kooti et al. (2012). The emergence of conventions in online social networks
- Leskovec, J., Backstrom, L., & Kleinberg (2009). Meme-tracking and the dynamics of the news cycle
- Lynch, A. (1999). Thought Contagion: How Belief Spreads Through Society
- Pennacchiotti et al. (2012). Making your interests follow you on Twitter
- Quercia et al. (2012). Facebook and privacy: The balancing act of personality, gender, and relationship currency
- Tang and Liu (2012). Unsupervised feature selection for linked social media data
- Wei et al. (2012). Competing memes propagation on networks: a case study of composite networks
- Weng et al. (2012). Competition among memes in a world with limited attention.

