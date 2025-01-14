# Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator

[Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator](https://arxiv.org/abs/2110.06190)

## Table of Contents
- [Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator](#exploring-the-endogenous-nature-of-meme-stocks-using-the-log-periodic-power-law-model-and-confidence-indicator)
- [2 Introduction](#2-introduction)
- [3 Methods](#3-methods)
- [4 Results and Discussion](#4-results-and-discussion)
- [5 Conclusion](#5-conclusion)

## Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator

**Log-Periodic Power Law (LPPL) Model and Conidence Indicator (CI) for Meme Stocks**

**Background:**
- Study examines endogenous nature of negative bubbles in meme stocks using LPPL CI
- Meme stock: gains significant attention on social media platforms like Yahoo! or Reddit

**Meme Stocks Examined:**
- Tesla, Inc. (TSLA)
- GameStop Corp. (GME)
- Koss Corporation (KOSS)
- AMC Entertainment Holdings Inc (AMC)

**Findings:**
- LPPL CI can detect numerous bubbles forming in meme stocks
- Difficulty predicting social media-induced rallies due to external causes like short squeezes
- Model provides proof for previous bubbles that could have catalyzed meme stocks' rallies

**Implications:**
- Real unpredictability of many black-swan events
- Further studies needed on exogenous bubbles

**Keywords:**
- Market Crash
- Financial Bubble
- Endogenous nature
- Log-Periodic Power Law Model
- Meme Stock


## 2 Introduction

**Meme Stocks and Speculative Bubbles:**

**Background:**
- Recent rise in commission-free stockbrokers and retail investors
- Accessible social media platforms (Reddit, Twitter, Discord) impacting investors and stock market
- Members of r/WallStreetBets creating movements around single stocks with speculative reasons
- Example: GameStop Corporation experienced massive short squeeze in January 2021
- Meme stocks characterized by belief in potential among social media platforms users

**Meme Stocks vs Traditional Bubbles:**
- Speculative gains non-traditional
- Retail investors openly coordinating stock decisions
- Differentiated from institutional investor decisions

**Study Methodology:**
- Analyzing endogenous nature of speculative bubbles using Log-Periodic Power Law (LPPL) model
- Detects positive and negative bubbles, crashes, and rallies
- Collecting daily data through Yahoo! Finance for TSLA, GME, KOSS, and AMC from memestocks.org.

**LPPL Model:**
- Devised by Sornette et al to detect positive bubbles or crashes
- Assumes collective behavior of "noise" traders imitating rational traders
- Observes faster than exponential growth in asset's price and accelerating log-periodic volatility fluctuations.

**Previous Studies:**
- Sornette et al first proposed and illustrated application on S&P 500 and Dow Jones historical data
- Filimonov and Sornette simplified calibration process
- LPPLS Confidence Indicator (CI) used for real-life bubble crashes analysis
- Wheatley et al used LPPLS model to analyze Bitcoin bubbles
- Shu et al utilized CI to examine Covid crash of US market and Chinese stock market bubbles.

**Negative Bubbles:**
- Opposite of positive bubbles
- Characterized by critical points as lows, "bursts" as rallies or sideways movements.

**Research Objective:**
- Examine significantly high sell positions in meme stocks and nature of negative bubbles
- Determine if recent phenomenon is exogenous or endogenous using LPPL model and CI.


## 3 Methods

**The Log-Periodic Power Law Model (LPPL)**

**Overview**:
- Devised by Sornette et al. [3]
- Incorporates assumptions of:
  - Rational expectation of traders
  - Herding and imitation of traders
  - Use of diffusion model concept from statistical physics and mathematics
- Characterizes bubble by:
  - Faster-than-exponential growth of price deviating from fundamental value
  - Accelerating log-periodic oscillations near crash point

**Dynamics of Price**:
- Follows equations (2) and (3) in the text

**Positive and Negative Bubbles**:
- Increase in accelerating oscillation as it reaches critical time following log-periodic frequency of 2^(-1/2) [16, 17]

**Calibration**:
- LPPL model has 7 parameters, optimizing is an arduous task
- Filimonov and Sornette's calibration method:
  - Represents LPPL model with 4 linear and 3 non-linear parameters
  - Significantly reduces complexity

**LPPL Representation**:
- Equation (5) in the text, with 3 non-linear (tc, ω, β) and 4 linear (A, B, C1, C2) parameters

**Optimization**:
- Least-squares method used to minimize cost function F(tc, β, ω, A, B, C1, C2)
- Linear parameters solved using matrix equation

**Complexity Reduction and Search Method**:
- Nelder-Mead simplex method used to find minima
- Algorithmic code devised by Joshua Nielsen [21]

**LPPL Calibrated Indicator (LPPL CI)**:
- Defined as "fraction of fitting window in which LPPL calibrations satisfy specified filter conditions" [7]
- Suggests possibility of bubble if seen in multiple time scales
- Small values indicate fragility, may not capture LPPL model sufficiently
- Calculated by fitting specified time window and gauging model against filter constraints
- Algorithms and conditions standardized for all datasets used in study.


## 4 Results and Discussion

**LPPL Model Study on Negative "Meme Stocks" Crashes**

**Findings**:
- LPPL model used to examine negative, non-traditional crashes in TSLA, GME, KOSS and AMC stocks
- All stocks experienced large gains followed by oscillating price declines
- CIs indicated local minima for stock prices in many cases
- Rallies forecasted using negative bubble indicator
- Positive bubbles also identified as Nielsen's code calculated them

**Stock Price Figures**:
- Figure 1: TSLA stock price from July 2017 to Feb 2021, LPPL CI in green and positive LPPL CI in red.
- Figure 2: GME stock price from Sept 2016 to Aug 2021, LPPL CI in green and positive LPPL CI in red.
- Figure 3: KOSS stock price from Sept 2016 to Sep 2021, LPPL CI in green and positive LPPL CI in red.
- Figure 4: AMC stock price from Sept 2016 to Aug 2021, LPPL CI in green and positive LPPL CI in red.

**Rally Statistics**:
- Red denotes positive bubble indicators, green denotes negative bubble indicators
- All datasets have more than 900 data points as per Demirer et al. recommendation for long-term studies
- Summary of rally statistics and related information in Table 1

**Interpretation of Data**:
- LPPL indicators showed potential bubble spikes more often than actual bubbles
- Relevant signals are indicator values greater than or equal to 0.3
- Study focused on negative bubble indicators that accurately predicted rallies

**Stock Analysis**:
- TSLA: Negative bubble indicator peak in June 2019 signaled rally in March 2020, generating 404% profit for investors
- GME: Highest negative bubble indicator peak in August 2019 signaled bounce-back in price but failed to capture enormous rally in second half of 2020
- KOSS: Negative bubble indicator cluster around April 2020 captured rally, with highest indicator value about 0.15
- AMC: LPPL model failed to capture positive bubble spike in January 2021 due to exogenous influence from meme stock phenomenon

**Conclusion**:
- CIs may not show oscillations caused by short squeezes triggered by retail traders' simultaneous buying on social media platforms.


## 5 Conclusion

**Study on Meme Stocks Bubbles:**
* Examined sudden rallies using LPPL model and its indicators: TSLA, GME, KOSS, AMC
* Many stocks experienced weekly gains >50% (Table 1)
* Endogenous nature of such gains considered for prediction using LPPL bubble model
* Results showed some endogenous signals before actual rallies
	+ GME: spike in LPPL Conidence Indicator around August 2019 with CI value of approximately 0.8
		- Negative LPPL bubble pattern due to higher than exponential decline in stock price
		- Actual rally barely captured possibly due to exogenous factors (short squeezes)
* LPPL model adequately predicted bubbles months in advance but market instability resulted in different causes of rallies.
* Further studies needed to examine exogenous natures of bubbles using LPPL model or otherwise.

