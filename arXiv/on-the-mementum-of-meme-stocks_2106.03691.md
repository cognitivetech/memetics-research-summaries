# On the "mementum" of Meme Stocks

[On the "mementum" of Meme Stocks](https://arxiv.org/abs/2106.03691)

## Table of Contents
- [On the “mementum” of Meme Stocks](#on-the-mementum-of-meme-stocks)
- [1 Introduction](#1-introduction)
- [2 On meme stocks and meme periods](#2-on-meme-stocks-and-meme-periods)
- [3 Procedure for identifying the 'mementum'](#3-procedure-for-identifying-the-mementum)
- [4 Conclusions](#4-conclusions)

## On the “mementum” of Meme Stocks

**"Meme Stocks: Understanding their Unique Characteristics through Cointegration Analysis"**

* This note explores meme stocks and their distinctive market dynamics.
* Identifies a unique "momentum" characteristic using a regime-switching cointegration model.
* Discusses price, trading volume, and social media activity stylized facts for meme stocks.
* Offers insights for investors and market authorities.
* Keywords: Meme Stocks, Social Media, Social Trading, Cointegration, Regime Switching.


## 1 Introduction

**Meme Stocks Phenomenon**

**Background:**
- Recent attention on "meme stocks" as social media used for stock coordination
- Retail investors coordinate buying signals through social media, contrasting with institutional strategies
- GameStop short squeeze in January 2021 as prominent example

**Characteristics:**
1. **Retail Investors**: Majority of actors initially involved
2. **Open Coordination**: Voluntary and open coordination of purchasing decisions
3. **Multi-platform Activity**: Cross-platform communication reinforces reach
4. **Impact on Price and Volume**: Significant increase in stock prices, financial losses for hedge funds
5. **Longer Duration**: Lasted several days
6. **Openness**: Ideal for decentralized coordination processes

**Evidence of Meme Stocks:**
- First evidence provided on the dynamics of price, trading volume, and social media activity on Twitter
- Formalize concept of "mementum" or meme period: synchronized buying signals originated on social media impact stock's price and traded volume

**Methodology:**
1. Characterization based on pairwise cointegration dynamics: price-trading volumes, trading volumes-social media activity, price-social media activity
2. Use regime-switching cointegration model to identify meme period(s) of a stock
3. Data-driven approach for inferring mementum
4. Applied to S&P1500 constituents: find that some popular stocks exhibit meme periods, others do not.

**Implications:**
- Framework allows understanding if a stock has experienced mementum or not
- Not limited to specific social platform or stock

**Examples of Meme Tweets:**
1. Left: References GME (GameStop), AMC, and an image describing the path towards "stunk success"
2. Right: Refers to GME and an image of a space rocket.


## 2 On meme stocks and meme periods

**Meme Stocks and Social Media Coordination:**

**Contrast Between Professional vs Retail Investors:**
- Professional investors: monitored through portfolio risk managers and financial analysts' reports
- Retail investors: "feel the mood" of the market by coordinating on social media
  - Viewed as noise traders

**Social Media Coordination Process:**
1. Population of retail investors discuss stocks openly on social media
2. Group of retail investors coordinate to synchronously buy large quantities of a stock using images and emojis
3. Increased traded volumes lead more investors to buy, creating a "bandwagon effect" and skyrocketing prices

**Data Collection:**
- Construct daily count time-series for each stock based on posts containing the official ticker symbol preceded by # or $
  - Include tweets and retweets, but remove retweets that share preexisting content
  - Remove posts without images

**Characterization of Meme Stocks:**
1. Contemporaneous relationship between price, Twitter posts with images, and trading volumes
2. Synchronization in time for these relationships during a meme period
3. Persistence of the relationships after a regime switch
4. Minimum duration condition to remove isolated and short-lived events

**Example Time Series:**
[GameStop (GME), AMC Entertainment (AMC), KOSS Corporation (KOSS), Moody's (MCO), Pfizer (PFE), Disney (DIS)]

- Memo stocks (GME, AMC, KOSS) showed abrupt spikes in mid-January 2021 without any shock to fundamentals
- Social media series drove synchronized market effect on volumes and prices
- Other stocks (MCO, PFE, DIS) more volatile with spikes related to COVID-19 events captured by social media.


## 3 Procedure for identifying the 'mementum'

**Time Series Cointegration**

**Definition:**
- Cointegration among time series (I(0) or I(1)): presence of stationary linear combinations
- Standard static setting: each relationship interpreted as long-run relationship, cointegration rank r
- Time-varying cointegration framework enables identification of dynamic price-tweet and volume-tweet pairwise relationships

**Model (1):**
- ∆yt = c +yt−1Πt + ∆yt−1B + ǫt, where ∆ is first difference operator, Πt is time-varying cointegrating matrix
- If at time t there exists a non-empty set of cointegrating relationships, then Πt has rank rt<n and admits low rank decomposition as Πt=βtαt
- Allows for alternating cointegrated and noncointegrated states, time-variation in the cointegrating parameters

**Estimation:**
- Performed using Bayesian approach with Markov chain Monte Carlo algorithm to approximate joint posterior distribution
- For each stock, estimated model (1) for price-tweet and volume-tweet pairings

**Meme Period Identification:**
- Retain starting dates of cointegration regimes lasting at least d days
- Filter out noisy estimates by requiring preceding non-cointegrated regime
- Merge closely following cointegrated intervals
- Identified periods: January 13, 2020 (GameStop), January 15, 2020 (AMC), January 25, 2020 (KOSS)

**Figure 4:**
- Shows the dynamics of inferred cointegrating relationships and meme periods for each stock: GameStop (GME), AMC Entertainment (AMC), KOSS Corporation (KOSS), Moody's (MCO), Pfizer (PFE), Disney (DIS)

**Figure 5:**
- Example of "meme Tweet" mentioning KOSS posted at the end of 2020. Tweet link: https://twitter.com/greenwoodstocks/status/1343690011678486529

**Conclusion:**
- Proposed framework able to discriminate meme periods from other events that affect prices and traded volumes.


## 4 Conclusions

**Impact of Meme Stocks on Financial Markets:**
- Significant impact on financial markets (1)
- New challenges and policy issues arising
- Initial attempt to characterize meme periods using regime switching cointegration and data identification methods

**Characteristics of Meme Stocks:**
- Transitory periods with coordinated social media originating from stock's price and volumes
- Example: GameStop's momentum - 57.39% increase in one day, traded volumes jumped dramatically (2)
- Further investigation required on asset pricing and market efficiency regarding the impact of social investors as an organized entity (3)

**References:**
1. "...significant impact on financial markets..."
2. GameStop's first day for meme momentum: 57.39% increase in price, 144,501,736 traded volumes
3. Further investigation needed into asset pricing and market efficiency with organized social investor impact.

