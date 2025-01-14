# The echo chamber effect resounds on financial markets: a social media alert system for meme stocks

[The echo chamber effect resounds on financial markets: a social media alert system for meme stocks](https://arxiv.org/abs/2203.13790)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Literature Review](#2-literature-review)
- [3 Data](#3-data)
- [4 Methodology](#4-methodology)
- [5 Results](#5-results)
	- [5.1 Event detection](#51-event-detection)
	- [5.2 Analysis of the abnormal returns](#52-analysis-of-the-abnormal-returns)
	- [5.3 Regression analysis](#53-regression-analysis)
- [6 Final discussion](#6-final-discussion)
- [A Data download](#a-data-download)
- [B The Social Network of Reddit users](#b-the-social-network-of-reddit-users)
- [C Subscriber rank](#c-subscriber-rank)
- [D Predictive regression](#d-predictive-regression)


## Abstract

**Echo Chamber Effect on Financial Markets: Early Warning System for Meme Stocks**
* **Gianstefania et al., IMT Lucca (2022)**

**Abstract**:
- Revealed impact of retail investors using social media on financial markets through the Gamestop (GME) short squeeze
- Devise early warning signal to detect suspicious social network activity that may affect market stability
- Apply approach to r/WallStreetBets subreddit, comparing meme stocks (GME, AMC) with non-meme stocks (AAPL, MSFT)

**Methodology**:
- Two-stage alert system:
  * Detects extraordinary social network activity
  * Identifies coordinated user actions to create a bulk movement
- Event study analysis of market reactions to alert system triggers
- Regression analysis of meme vs. non-meme stocks' response to social networks

**Keywords**:
- Market manipulation
- Social network analysis
- Alert system
- Event study
- Reddit

**JEL Codes**: G14, G18, G41, 039

**Authors**:
- Ilaria Gianstefani (ilaria.gianstefani@imtlucca.it)
- Luigi Longo (luigi.longo@imtlucca.it)
- Massimo Riccaboni (massimo.riccaboni@imtlucca.it)


## 1 Introduction

**Retail Investors and Social Media Impact on Financial Markets**

**Background:**
- Retail investors once considered noise traders, but their impact is growing
- GameStop (GME) short squeeze example: coordinated by Reddit community r/WallStreetBets
  - Popular subreddit for financial markets and stock trading
  - Users employ aggressive strategies
  - GameStop faced sharp decline in sales and share price
  - Institutional investors sold short, retail investors bought
  - Coordinated effort surged GME's price
- Social media networks impact on financial price information gaining attention

**Impact of Retail Investors:**
- Large numbers of retail investors can influence market significantly
- Previously underestimated in their ability to cause substantial effects
- Increasing decentralization and accessibility of financial system through online platforms

**Social Media Manipulation:**
- SEC defines market manipulation as artificial effect on security's supply or demand
- Social media coordination considered potential market manipulation
- No regulation specifically addressing social media impact on markets

**Methodology:**
- Social listening and social network analysis to identify suspicious behavior
- Real-time interventions for prevention of instability in financial markets.

**GameStop Case Study:**
- Dramatic magnitude and effects on market
- Coordinated effort by retail investors on Reddit led to significant price surge
- Short sellers suffered substantial losses due to high volatility, liquidity issues

**Implications:**
- Misconduct behaviors in online social networks can result in potential market manipulation
- Urgent need for alert system to monitor suspicious activities and prevent instability.


## 2 Literature Review

**Impact of Digital and Online Social Networks on Financial Markets**

**Rising Importance of Retail Traders:**
- Classical market microstructure models overlooked noise traders
- De Long et al. (1990): recognized relevance of irrational traders with stochastic beliefs
- Proliferation of internet and social media transforming markets

**Impact of Social Media on Financial Markets:**
- Improved ability to access information in real-time
- Analysis of impact on markets: volume, sentiment, and search engine traffic

**Research Focused on Social Media's Impact:**
- Mao et al. (2012), Bordino et al. (2012), Ruiz et al. (2012), Preis et al. (2013)
- Empirical extrapolation, focus on various techniques

**Specific Market Manipulation: pump-and-dump scheme**
- Renault (2018): abnormal social media activity associated with price reversals

**New Model for Noise Traders:**
- Pedersen (2021): investment strategies propagate in a social network
- Four types of investors: rational short/long, fanatics, naive
- Belief formation process and market impact

**Implications on Financial Markets by Social Media Investment Analysts:**
- Dim (2021): non-professional social media investment analysts influence markets

**Our Paper's Contribution:**
- Detecting extreme situations to prevent market instability
- Two red flags: extraordinary social network activity and user network structure analysis
- Influential users, or "fanatics," tracked for their centrality and vocal contributions.


## 3 Data

**Data Analysis**

**Stocks Studied**:
- GameStop (GME)
- American Multi-Cinema Entertainment (AMC)
- Apple Inc. (AAPL)
- Microsoft Corporation (MSFT)

**Market Data**:
- Daily resolution time series of price and traded volume for each stock
- Computed daily returns: `Rt_s = Pt_s - Pt_s-1`

**Reddit Data**:
- Downloaded posts containing the ticker as a keyword in the title and related comments
- Limited data download to the subreddit r/WallStreetBets from October 2020 to June 2021
- Extracted every post and its corresponding comment tree

**Analysis**:
- Interested in emerging collective phenomena among retail investors affecting the financial market
- Excluded messages generated by bots (identified with the 'moderator' tag) from analysis
- Modeled each conversation thread as a directed tree with nodes representing messages and edges connecting parent-child comments
- Measured daily activity by number of posts, comments, submitters, and commenters for each stock

**Social Network Analysis**:
- Reconstructed the daily user interaction network from the raw data
- Defined a network where nodes represent active users and edges represent commenting activity
- Simplified the network representation to point all links to the author of the initial submission
- Identified hubs (central nodes) in the network, representing users driving influential messages or ideas
- Example of user interaction network for GME on January 14, 2021, with 6,465 users and 8,741 edges.


## 4 Methodology

**Alert System Design and Functioning**

**1. Alert System Overview**:
- Devised to detect potential misconduct behaviors on social media networks
- Cooperation among users can impact financial market stability
- Query-dependent system that monitors specific keywords

**2. First Stage of the Alert System**:
- Screens days with extensive ticker activity on social networks
- Uses volume-related metrics: submissions, active users, overall activity
- Variables created: relative number of daily submissions, absolute number of daily submissions, etc.
- Triggers when at least 4 variables exceed their thresholds
- Minimum alert activation condition is that all 6 variables exceed their critical threshold for at least one day
- Remains on until the following condition verifies:
  - Ten authors with highest relative incoming links are connected in a directed graph of the top users

**3. Second Stage of the Alert System**:
- Determines abnormal returns using market model to eliminate market fluctuations
- Abnormal trading volume defined as volume traded on a given day divided by average volume over estimation window [T0:T1]


## 5 Results

**Empirical Analysis: Results**

1. Present anomalous days identified by alert tool.
2. Event study analysis of associated abnormal returns.
3. Regression analysis:
   a. Understanding drivers for meme stocks vs non-meme stocks.
   b. Social network variables significantly impact meme stock performance.
   c. Market-related variables primarily affect non-meme stocks.


### 5.1 Event detection

**Event Detection: Identifying Suspicious Activity on Social Media**

**Daily Time Series Analysis**:
- Price and traded volume for stocks under analysis
- Days alert system detects extraordinary activity and cooperation on social network

**Alert System Findings**:
- 21 suspicious movements on social network for GME
- 4 for AMC
- 2 for AAPL
- 1 for MSFT

**GME Stock**:
- Most incredible attention and chattering on social media
- Short squeeze in January 2020: most striking episode of social network cooperation impacting financial economy
- Alert tool can detect abnormal movements days before affecting the market
- Can narrow down users driving the movement for investigation by surveillance authority

**AMC Stock**:
- Considerable attention on social media during same period as GME frenzy
- Retail investors attempt pump-and-dump scheme, but create instability on May 2021
- Price rose about 7 times in 10 days after warning on May 19, 2021

**AAPL and MSFT Stocks**:
- Financial performance unaffected by social media activity
- Leading users aware these stocks are challenging for pump-and-dump schemes or driving price away from fundamental value
- Alert system rarely triggered, identified events insignificant compared to meme-stocks


### 5.2 Analysis of the abnormal returns

**Analysis of Abnormal Returns**

**Procedure**:
- Submissions from influencers during days of unusual activity are considered as potential triggers for financial market response
- Analyze abnormal returns constructed with a market model to evaluate whether submission triggers reaction in the financial markets
- For each detected event:
  - Compute abnormal return on estimation window [-21:-11] (L1=10) and event window [-10:10] (L2=21 trading days)
  - Abnormal return is defined with a market model using CRSP index as proxy for market returns
  - Impose minimum of 10 days between two events to avoid contagion on the event window and consider them independent
  - If an event happens on non-trading day, consider next trading day as event date

**Findings**:
- For GME: 8 events identified by alert system (DeepFuckingValue, Ackilles, SIR JACK ALOT, etc.)
- For AMC: 4 events identified by alert system (Nauzzaki, Mysterious|-, Tilthefatladysings)
- For AAPL and MSFT: 2 (Nauzzaki for AAPL and Tilthefatladysings for MSFT), but no clear upward trend after submission
- Results show significant abnormal returns following alert dates only for meme-stocks, GME and AMC.

**Significance of Events**:
- Influencers aim to move price up by massively buying the stock
- Evaluated based on highest positive abnormal returns in the event window

**Table 1**: List of events spotted by alert system for each stock under analysis, including date and user(s) involved.

**Table 2**: Event study for GME on January 14th, 2021 (event day). Shows abnormal returns, cumulative abnormal returns, and abnormal volumes on [-10:+10] days event window around the event day.


### 5.3 Regression analysis

**Regression Analysis**

**Dependence of Abnormal Returns on Social Network-Retrieved Information**:
- Focus on differences between meme and non-meme stocks' abnormal returns
- Assess dependence between abnormal returns and social network-retrieved information
- Find different patterns for the two stock categories

**Regression Model**:
- Time-series regression of abnormal stock returns on social network-related variables
- Controlling for market-related and stock-specific variables
- Estimated using OLS with HAC estimator for variance by Newey and West (1987) for each stock

**Social Network-Related Variables**:
- **ARt;s**: Higher popularity of the subreddit, as measured by the number of users
- **Ot;RH**: Dummy assuming a value of 1 when website DownDetector.com reports malfunctioning of Robinhood
- **ABNt;sis**: Average branching number, a proxy for the daily virality of comment trees
    - Inspired by Choi et al. (2015), where conversations' threads are defined as tree Tk\ns
    - The average branching number quantifies the average number of comments a node generates

**Results**:
- **AAPL** is not significant, while **MSFT** remains positive and significant, but lower in magnitude than meme-stocks
- Increase in number of reports may be related to high activity in the stock market on Wallstreetbets community
    - Associated with an increase in abnormal returns, more so for meme-stock
- **ABNt;sis** positively impacts abnormal returns during outages of Robinhood platform
    - Interacting it with outages positively impacts abnormal returns for GME
        - May disentangle e¤ect of noisy traders rather than big corporations on the stock
- **Transaction volume** is negative for non-meme stock, in line with liquidity theory
    - Higher trading volume commands lower expected stock return due to increased risk
- Transaction volume has unexpected significant positive effect on abnormal returns for meme-stock

**Echo Chamber Effects**:
- Regression of abnormal volume as a dependent variable to evaluate users' trading of meme and non-meme stocks


## 6 Final discussion

**Social Media and Market Manipulation:**
* Social media platforms, like Reddit, used for stock market manipulation (indirect)
* Evidence of echo chamber effect on financial markets
* Naive investors manipulated by experienced traders or "fanatics"
* Coordinated efforts can disrupt financial market stability
* Designing an alert system to detect abnormal stock activity and potential manipulators
* Retail investors not just "noise traders," can collectively impact the market
* Meme stocks vs non-meme stocks: significant differences identified
* Detection system finds alerts for both categories, but only meme stocks experience abnormal returns.
* Social network information significant in determining prices of meme stocks through social activity and potential coordination.


## A Data download

**Reddit Comment Tree Structure**

**Data Frame Columns:**
- **title**: textual content of initial submission
- **body**: textual content of comment
- **name**: id of author (prefixed with 't1' for comments, 't3' for top-level posts)
- **parent_id**: id of parent comment or submission
- **author_name**: name of author who posted initial submission
- **depth**: level of comment tree
- **score**: number of upvotes - downvotes on comment
- **score_submission**: number of upvotes - downvotes on submission
- **upvote_ratio**: percentage of upvotes on total votes for submission
- **time_submission**: date and time of initial submission publication
- **time_comment**: date and time of comment publication
- **num_comments**: number of comments below initial submission
- **flair**: tag used to categorize post by topic (YOLO, DD, Discussion, Gain, Loss, Earnings Thread, Daily Discussion, Mods)
- **distinguished**: 'Moderator' if automated bot, otherwise blank for non-automatic user

**Initial Submission:**
- Single row with empty values for comments-related variables


## B The Social Network of Reddit users

**Figure 11: Network User Graph (January 31st, 2021)**

- Example of a user interaction graph on a platform.
- Ticker symbol: AMC.
- Total nodes: 15.534 users.
- Total edges: 21.032 interactions.
- Central nodes (highest in-degree centrality) are colored.

**Figure 12: Network Graphs for AAPL and MSFT (June 22nd, 2021 - AAPL; May 20th, 2021 - MSFT)**

- Comparison of user interaction graphs for non-meme stocks.
- Feeble social network activity during extraordinary occasions for non-meme-stocks.


## C Subscriber rank

**Figure 13:** *Representation of Reddit Subscriber Rank Variation (2013-2022):*

- Shows change in Reddit subscriber rank over time between years 2013 and 2022.


## D Predictive regression

**Understanding Social Network Information and Abnormal Stock Returns**

**Regression Results**:
- Regression performed on future abnormal returns dependent on market-related variables and social network variables (Reddit)
- Variables: Volt, Meme stock (GME), AMC, ART, CAR, GME Network, Financial Data, Alert Days for GME and AMC

**Visualizations**:
- Figure 4: Reddit network on January 14th, 2021, reporting interactions of users posting 'GME' with 6,465 nodes and 8,741 edges
- Figure 5: Financial data for GME stock from October 2020 to June 2021, showing daily price, traded volume, and alert days
- Figure 6: Similar information as Figure 5 but for AMC stock
- Figure 7: Financial data for AAPL stock from October 2020 to June 2021
- Figure 8: Financial data for MSFT stock from October 2020 to June 2021
- Figures 9, 10: Abnormal returns and cumulative abnormal returns for GME and AMC single event in a [-10:10] day window centered on the event date
- Figures 11, 12, 13: Visualizations related to AMC stock on May 19th, 2021; AAPL/MSFT on May 20th, 2021; and subscriber rank from 2013 to 2022

**References**:
- Various studies cited throughout the text.

