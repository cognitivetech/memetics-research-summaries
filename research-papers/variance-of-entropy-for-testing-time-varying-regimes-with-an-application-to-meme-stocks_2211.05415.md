# Variance of entropy for testing time-varying regimes with an application to meme stocks

[Variance of entropy for testing time-varying regimes with an application to meme stocks](https://arxiv.org/abs/2211.05415)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
	- [The GameStop case](#the-gamestop-case)
- [2 Methodology and Dataset](#2-methodology-and-dataset)
- [3 Simulation study](#3-simulation-study)
- [4 Empirical application: the case of meme stocks](#4-empirical-application-the-case-of-meme-stocks)
	- [4.1 Market efficiency](#41-market-efficiency)
	- [4.2 Meme stocks](#42-meme-stocks)
	- [4.3 IT stocks](#43-it-stocks)
	- [4.4 Quarterly training sets](#44-quarterly-training-sets)
- [5 Conclusions and discussion](#5-conclusions-and-discussion)
- [Appendices](#appendices)


## Abstract

**Study Title:** Variance of Entropy for Testing Time-Varying Regimes: An Application to Meme Stocks

**Authors:** Andrey Shternshis(1), Piero Mazzarisi(1,2)

**Affiliations:**
- Scuola Normale Superiore, Piazza dei Cavalieri 7, Pisa, Italy, 56126 (1)
- University of Siena, Department of Economics and Statistics, Piazza S. Francesco, 7-8, Siena, Italy, 53100 (2)

**Abstract:**
- Proposed hypothesis testing procedure to determine constant Shannon entropy in time series data
- Goal: Test null hypothesis of constant entropy versus significant variation between periods
- Obtained explicit formulas for central moments of binomial and multinomial distributions describing Shannon entropy distribution
- Found optimal length of rolling window for estimating time-varying Shannon entropy through a self-consistent criterion
- Corroborated findings by applying methodology to test for time-varying entropy regimes in meme stocks, revealing periods of market efficiency

**Keywords:**
- Entropy distribution
- Approximate computation of entropy variance
- Hypothesis testing for market efficiency
- Meme stocks.


## 1 Introduction

**Introduction:**
- Shannon entropy is used to measure randomness in various fields including finance
- Measuring market efficiency through entropy estimation of price returns
- Market efficiency assumption: when price reflects all relevant information, it's a martingale and has maximum entropy
- Inefficient markets can exhibit predictable price dynamics with lower Shannon entropy estimates
- Many factors can cause deviations from market efficiency, including supply/demand imbalances, feedback loops, irrational agents, etc.
- Importance of filtering out known market predictability patterns before using entropy as a measure of market efficiency

**Problems:**
1. Finding the variance of Shannon entropy estimator using Empirical Frequencies method
2. Optimal length (bandwidth) of rolling window for time-varying entropy estimation

**Shannon Entropy Variance:**
- Basharin [22] and later [23] provided first order approximation of variance using Eq. 1, but it holds only in the asymptotic regime
- Need to estimate time-varying entropy for finite samples
- Inconsistent estimator when all probabilities are equal (D1(ˆH) = 0)
- Proposed method: variance formula as a sum of central moments of binomial and multinomial distributions
- Accuracy of order O(n−4)
- Ricci et al. [25] found bias term in naive entropy estimator approximation, but our proposed estimation is unbiased

**Statistical Test for Entropy Variation:**
- Previous research tested independence using permutation entropy test statistics [26]
- Rejection of null hypothesis signals statistically significant variation between any two possible entropy values.

**Optimal Bandwidth (Length) Selection:**
- Problem of bias-variance tradeoff: reducing window length increases timeliness but increases variance
- Self-consistent criterion introduced for in-sample optimal bandwidth selection
- Minimum entropy variations occur when the window is close to ω=1, while it's zero at ω=T.
- Simulations show counting function has one maximum corresponding to the optimal bandwidth.

**Application:**
- Investigating changes in efficiency of New York Stock Exchange with a focus on meme stocks
- Lower price return time series entropy indicates higher predictability and potential inefficiency
- Case study: GameStop's significant price increase in January 2021.


### The GameStop case

**The GameStop Case (2021)**

**Background:**
- Dramatic increase in share prices of certain stocks, including GameStop, from late December 2020 to early January 2021
- Driven by individual investors on Reddit and other online platforms
- Two crucial aspects leading to the price surge:
  1. Absence of trading frictions through off-exchange market makers and fintech innovations
  2. Coordination in long trades among individual investors
- Resulted in a rebellion against short selling professional investors

**Impact:**
- Sharp increase in prices, further amplified by coverage of short positions by professionals
- Intermediaries performed extraordinary operations during the period

**Market Inefficiency During GameStop Rally:**
- Focus on market (in)efficiency and predictability of price pattern
- Signal of inefficiency through Shannon entropy and statistical variations

**Structure of the Paper:**
1. Section 2: Test of Equality of Entropies and Method for Choosing Interval Length
   - Variance estimation (Section 2.2)
   - Proposed method for sliding window length (Section 2.4)
2. Section 3: Testing Hypothesis on Simulated Data
3. Section 4: Testing Hypothesis for Price Returns of Meme Stocks
4. Conclusion (Section 5)

**Additional Information:**
- The paper discusses the manipulative nature of trading behavior coordinated via social networks and interprets the GameStop rally as a revenge against Wall Street for the 2007-2008 crisis.


## 2 Methodology and Dataset

**Empirical Frequencies Method for Estimating Shannon Entropy**
- Discussed method for estimating Shannon entropy using Empirical Frequencies (EF)
- Definition of k-th order entropy: Hk(p) = −∑ln p(xk) log p(xk), where xk is a sequence of length k and p is the probability distribution
- EF method uses empirical frequencies f(ak|xn) to estimate k-th order entropy ˆHk(xn): 
  - f(ak|xn) = number of occurrences of symbol ak in sequence xn of length n - k + 1
  - ˆHk(xn) = −∑ln f(ak|xn)/n for all symbols ak in the alphabet A
- Process entropy can be estimated as ATE(xn) = lim k→∞ ˆHk(xn)

**Variance of Entropy's Estimator**
- Let M events with probabilities p0, ..., pm−1 occur independently n times, frequency fj is distributed as Binomial B(pj, n), and estimation ˆH = −∑ln fj/n
- Variance of ˆH estimated using Theorem 1: Var(ˆH) = 1/n * (H2 + ∑j pjln2(pj)/M + 6n3/(3M+1) + O(n−4))
  - H = −∑j pjln(pj), where ln is the natural logarithm
- Variance of the estimation error: E[Var(ˆH)] = Var(Var(ˆH)) = Var(E[ATE(xn)])

**Hypothesis Testing for Equality of Entropies**
- H0: Entropies H1 and H2 are equal, Ha: They are not
- Z-score z = ˆH2 − ˆH1√Var2 + Var1 is distributed with zero mean and variance 1
- Reject H0 if |z| > quantile corresponding to 99% confidence level

**Determining Bandwidth for Entropy Estimation**
- Choose bandwidth w, the length of a rolling window, to detect significant changes in entropy
- Small values of w give small z-scores due to high variance, large values may not catch largest changes
- Objective function f(w) = max(|z(w)|), where z(w) is the z-score for the given bandwidth w
  - Maximizes the largest absolute z-score
- Set upper bound nmax = ceil(n/2) to test all adjacent non-overlapping intervals


## 3 Simulation study

**Entropy Analysis:**
- Finding quantiles of entropy distribution
  * Basharin showed that large M leads to normal distribution [22]
  * If probabilities are equal, distribution converges to chi-square [31]
- Empirical quantile calculation:
  * N=2×104 Monte Carlo simulations with length n=2×105 and k=7
  * Var(ˆHmax) = (M−1/(n−k+1)² + M²/(n−k+1)³) [Eq. 3]
  * Normal distribution: empirical quantiles are 3.30722 (99%) and 2.54542 (95%)
  * Large sequences have thicker tails than normal distribution
- Testing short independent sequences:
  * Fix k=4, maximum entropy is 4ln|A| = 4ln4, M=256
  * False positive rate for level of significance α=0.01 (0.05) is acceptable

**Testing Entropy Estimator:**
- Hypothesis testing using Eq. 5 with variance from Eq. 4
- Power and size of the test:
  * Two sequences with entropy H(τ), length n=10000, false positive rate = 0.86%
  * Table 1 shows power for different values of τ

**Non-stationary Process:**
- Sequence with alphabet of four symbols and entropy H(τ) given by Eq. 8
- Three parts: stationary on both ends, middle with varying entropy
- Variance of entropy's estimator is time-varying, estimated using Equation 4
- Optimal bandwidth wopt determined from Section 2.4
  * Figure 2 shows optimal bandwidth for different values of l
  * Figure 3 plots objective function (Eq. 6) for four random iterations
  * The larger the argument of maxima corresponding to wopt, the larger l
- Fixing l=10000 and taking τ from 0.25 to 0.5: Figure 5 shows optimal bandwidths for different values of τ
  * τ=0.25 corresponds to a stationary process, larger bandwidth is more accurate
  * Deviation of wopt when τ=0.25 is high due to first type error in hypothesis testing


## 4 Empirical application: the case of meme stocks

### 4.1 Market efficiency

**Market Efficiency**

1. Definition: A market where prices reflect all available information is called efficient.
2. Weak form of efficient market hypothesis (EMH): Information set is historical prices only.
3. If a market is efficient in weak form, future prices cannot be predicted better than their current value.
4. Maximum degree of randomness: Full uncertainty about future price values implies maximum entropy for price returns.
5. Rejecting the null hypothesis (H0) of efficiency and observing time-varying entropy suggests predictability in price returns.
6. Low entropy relatively to past estimates indicates potential market inefficiency or predictability.


### 4.2 Meme stocks

**GME, BBBY, and AMC Stocks Analysis**

**Data Filtering**:
- Intraday volatility pattern filtered using ARMA model
- Optimal bandwidth (wopt) determined using training set
- Volatility and price staleness defined by minute

**Entropy Calculation**:
- Shannon entropy calculated for testing set using rolling window with length wopt
- Comparison of entropies in adjacent intervals: decrease, increase, no significant change

**Results**:
- Table 2 presents results for each stock
- Figure 6 shows entropy estimation, price, and trading volumes for GME stock
- Dots on plots indicate statistically significant changes in entropy

**GME Stock Analysis**:
- Two series of decreases: [17.07.20 - 14.09.20] and [7.12.20 - 19.01.21]
- Entropy was already low for AMC during record volumes and sharp price rise in January 2021

**BBBY Stock Analysis**:
- Three series of decreases: [06.03.20 - 05.05.20], [10.12.20 - 28.01.21], and [06.05.21 - 21.06.21]

**AMC Stock Analysis**:
- Four series of decreases: [05.03.20 - 17.04.20], [10.08.20 - 08.09.20], [08.03.21 - 30.03.21], and [05.05.21 - 27.05.21]
- Time intervals highlighted in bold correspond to sharp increases in price values.


### 4.3 IT stocks

**Comparison of Stock Entropies: Apple, Salesforce, Microsoft**

**Entropy Plots and Optimal Bandwidths:**
- Calculated entropies plotted in Fig. 7 (see below)
- Optimal bandwidths recorded in Table 2

**Stock Comparison:**
- **Apple (AAPL):**
  * Entropy exhibits time-varying behavior
  * Statistically significant changes detected
  * Negative f(wopt) indicates stationarity
- **Salesforce.com (CRM):**
  * Entropy defined as non-stationary in 2019
  * Optimal bandwidth and hypothesis testing results in Table 2
- **Microsoft (MSFT):**
  * Entropy exhibits time-varying behavior
  * Statistically significant changes detected
  * Negative f(wopt) indicates stationarity

**Optimal Bandwidths and Test Results:**
- Calculated on training set
- Number of tests: amount of adjacent intervals with length wopt in testing set
- Increases and decreases: statistically significant changes in entropy between adjacent intervals

**AAPL Entropy Time Series:**
| Date          | Time (5-day moving average) | H     | Decrease | Increase | Entropy |
|---------------|-----------------------------|-------|----------|----------|---------|
| 20.04.20      |                             | AAPL  | -        | -        | 5.5245  |
| 15.05.20      |                             | Hndecrease| 14.07.20| 02.10.20 | 5.5305  |
| 15.06.20      |                             |       | -        | -        | 5.5325  |
| 13.07.20      |                             |       | -        | -        | 5.5340  |
| 05.08.20      |                             |       | -        | -        | 5.5360  |
| 28.08.20      |                             |       | -        | -        | 5.5375  |
| 23.09.20      |                             |       | -        | -        | 5.5385  |
| 16.10.20      |                             |       | -        | -        | 5.5395  |
| 10.11.20      |                             |       | -        | -        | 5.5405  |
| 07.12.20      |                             |       | -        | -        | 5.5410  |
| 04.01.21      |                             |       | -        | -        | 5.5415  |
| 28.01.21      |                             |       | -        | -        | 5.5420  |
| 24.02.21      |                             |       | -        | -        | 5.5435  |
| 19.03.21      |                             |       | -        | -        | 5.5450  |
| 15.04.21      |                             |       | -        | -        | 5.5465  |
| 11.05.21      |                             |       | -        | -        | 5.5480  |
| 04.06.21      |                             |       | -        | -        | 5.5495  |
| 28.06.21      |                             |       | -        | -        | 5.5525  |
| 20.07.21      |                             |       | -        | -        | 5.5545  |

**CRM Entropy Time Series:**
| Date          | Time (5-day moving average) | H     | Decrease | Increase | Entropy |
|---------------|-----------------------------|-------|----------|----------|---------|
| 21.02.20      |                             | CRM   | -        | -        | 5.5225  |
| 18.03.20      |                             |       | -        | -        | 5.5245  |
| 14.04.20      |                             |       | -        | -        | 5.5265  |
| 08.05.20      |                             |       | -        | -        | 5.5285  |
| 05.06.20      |                             |       | -        | -        | 5.5305  |
| 01.07.20      |                             |       | -        | -        | 5.5325  |
| 29.07.20      |                             |       | -        | -        | 5.5340  |
| 24.08.20      |                             |       | -        | -        | 5.5360  |
| 21.09.20      |                             |       | -        | -        | 5.5385  |
| 16.10.20      |                             |       | -        | -        | 5.5405  |
| 11.11.20      |                             |       | -        | -        | 5.5420  |
| 10.12.20      |                             |       | -        | -        | 5.5435  |
| 11.01.21      |                             |       | -        | -        | 5.5465  |
| 05.02.21      |                             |       | -        | -        | 5.5525  |
| 05.03.21      |                             |       | -        | -        | 5.5600  |
| 01.04.21      |                             |       | -        | -        | 5.5710  |
| 30.04.21      |                             |       | -        | -        | 5.5980  |
| 26.05.21      |                             |       | -        | -        | 5.6315  |
| 23.06.21      |                             |       | -        | -        | 5.6805  |
| 20.07.21      |                             |       | -        | -        | 5.7495  |


### 4.4 Quarterly training sets

**Impact of Changes in Data Regularities on Stock Market Volatility**

**Entropy**:
- Measures uncertainty or randomness in a system
- Decrease in entropy can lead to increased predictability and more statistically significant changes in stock prices

**Meme Stocks vs IT Companies**:
- Meme stocks exhibit lower entropies (more predictable prices) than IT companies

**Effect of Changing Data Regularities**:
- The structure of data regularities may change over time, affecting the intraday volatility pattern
- This can lead to more significant changes in entropy for certain stocks

**Impact on Individual Stocks**:
- Examples of statistically significant changes in entropy for selected stocks:
  - GME: Decrease starting from [03.08.20...] and [29.12.20...], corresponding to price increases
  - AMC: Multiple periods of low entropies, including [25.03.20...], [30.09.20...], and [05.05.21...], also associated with price spikes
  - BBBY: Entropy becomes significantly low starting from [07.08.20...], during rapid growth in price and trading volumes
- AMC does not have enough non-zero returns before 2019 to accurately determine intraday volatility pattern for all minutes, leading to missing values in the filtered return time series

**Conclusion**:
- Changes in data regularities can impact stock market volatility, with meme stocks exhibiting more predictable prices than IT companies.


## 5 Conclusions and discussion

**Method for Detecting Changes in Entropy Value of a Sequence**
- **Novel procedure**: hypothesis testing to determine if two discrete sequences have different entropy values
- Used to detect changes in the entropy value of a sequence
- **Entropy** can change over time, so interval length cannot be fixed

**Contributions**:
1. Approximation of entropy's variance for hypothesis testing
2. Unbiased estimation of approximation of variance to evaluate variance from sequence
3. Method for finding optimal interval length

**Application**:
- Analyzed return time series of meme stocks (GME, BBBY, AMC) and IT companies (AAPL, CRM, MSFT)
- Found that entropy is **time-varying** in 2019 for all stocks except CRM
- Low entropy values indicate **predictability** of return time series

**Findings**:
- For GME: low entropy before price spike
- For AMC: low entropy when price increased in January 2021 and again before maximum in June 2021
- For BBBY: low entropy from December 2020 to end of January 2021, corresponding to price drop and spike in February 2021

**Significance**:
- **Drop in entropy** precedes growth in prices and trading volumes for GME and AMC
- Indicates **early warning signal** of market inefficiency and potential turmoil period


## Appendices

**Theorem 1 Proof:**
- Need five propositions: Proposition 1, 2, 3, 4, and a result from [24, 37]
- Proposition 1 (Central moments of multinomial distribution): can be defined recursively using formulas in proposition
- Proposition 2 (Central moments of binomial distribution): special case of Proposition 1 with p2=k=0
- Proposition 3 (Expected value of pln p): given by Eq. (
ef{11}) in text, derived using Taylor expansion around p
- Proposition 4 (Variance of entropy estimation): not explicitly stated but can be obtained from Eq. (
ef{12}) and the approximation of second moment of pln(p) provided earlier
- Result from [24, 37]: moments with m+k <= 4 coincide with results given in those papers

**Theorem 2 Proof:**
- Introduce random variable V ar
- Use equations and approximations to show that E(V ar) = p j ln(p j ) + 2 − H + O(n −4 )

**Appendix:**
- Figures showing estimated entropies, prices, and trading volumes for BBBY and AMC stocks provided.

---

Thank you to arXiv for use of its open access interoperability.
