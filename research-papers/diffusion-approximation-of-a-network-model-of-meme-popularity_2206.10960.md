# Diffusion approximation of a network model of meme popularity

[Diffusion approximation of a network model of meme popularity](https://arxiv.org/abs/2206.10960)

## Table of Contents
- [Diffusion approximation of a network model of meme popularity](#diffusion-approximation-of-a-network-model-of-meme-popularity)
- [I Introduction](#i-introduction)
- [II The diffusion approximation](#ii-the-diffusion-approximation)
  - [A. Fluctuation cases](#a-fluctuation-cases)
  - [B. Finite Variance Degree Distribution](#b-finite-variance-degree-distribution)
  - [C. Infinite-variance degree distribution](#c-infinite-variance-degree-distribution)
  - [D. Popularity](#d-popularity)
- [III Results](#iii-results)
  - [B. Fokker-Planck equation and its moments](#b-fokker-planck-equation-and-its-moments)
  - [C Dependence on n, or time step t](#c-dependence-on-n-or-time-step-t)
- [IV. DISCUSSION](#iv-discussion)

## Diffusion approximation of a network model of meme popularity

**Meme Propagation on Social Networks: Analyzing Individual Trajectories**

* Researchers Kleber A. Oliveira, Samuel Unicomb, and James P. Gleeson from University of Limerick propose a model for meme propagation on social networks using stochastic processes.
* They derive popularity distributions at a system-wide level analytically but investigate individual meme trajectories.
* Memes' diffusion treated as a one-dimensional stochastic process.
* Local network dynamics aggregated through classic and generalized central limit theorems based on stable distribution theory.
* Decoupling competing meme popularity trajectories for parallelization and Fokker-Planck equation expression.


## I Introduction

**Dynamics of Information Dissemination in Networked Systems**

**Background:**
- Extensive research on memes as transmissible information units [1]
- Meme popularity studied through social media sharing [3-6]
- Heavy-tailed distributions characterize meme popularity [7]

**Competition-Induced Criticality (CIC) Model:**
- Meme in competition for user attention [8]
- Representation of finite attention with a "screen" per user [9-12]
- Transmission occurs when users broadcast content to followers, overwriting their screens
- Dynamic quantities described using branching processes and tree-like approximations [14]
- Neutral model: no meme inherently grows more popular than others; popularity controlled by macroparameters [16, 17]

**Discrete-to-Continuous Limit:**
- Discrete time jump process for meme popularity evolution in simulations [20]
- Continuous variable for fraction of screens occupied by memes suggested [18]
- Stochastic equations and generalized central limit theorems used to model popularity dynamics [18, 19]

**Structure of Paper:**
- Description of CIC model and simulation scheme [II]
- Identification of local fluctuations and central limit theorems application [II A]
- Finite-variance and infinite-variance degree distributions [II B, II C]
- Validation of analysis through comparison to computational simulations [III]


## II The diffusion approximation

**Diffusion Approximation of Meme Popularity Model**

**Network Assumptions:**
- Directed network of size N
- Edge direction represents information flow in a social network
- Out-degree k: number of followers (e.g., Twitter)
- Distribution p(k)
- Average degree h, variance σ²
- Assumed integer and h→ki-regular distribution
- Configuration model: maximally random up to in- and out-degree

**Nodes & Meme Display:**
- Each node represents a screen for meme display
- Discrete type or color
- Overwritten by tweeting nodes' memes

**System Updates:**
- One node selected uniformly at random to tweet per update
- Probability µ: innovate original meme (overwrite current and neighbors') or retweet existing meme
- dt = 1/N: elementary time unit between successive updates
- Macroscopic time step: N updates
- Initialization: every screen is blank, blank screens innovate new memes with probability 1

**Previous Study:**
- Branching process approximation for distribution of meme popularity (accumulated number of retweets) in Ref. [8]

**Current Focus:**
- Characterizing stochastic trajectories of individual memes
- Discrete-to-continuous approximation to study fraction of screens occupied by a meme at a given time.


### A. Fluctuation cases

**Red Meme Evolution Model**

**Focus on Red Meme (s)**:
- Occupies a fraction s of all screens in the system
- Temporal evolution is stochastic function of:
  - Network topology (p k)
  - Innovation rate (µ)
  - Current density (s) of meme itself

**Update Step Outcomes**:
- **Cases 1, 2, and 4**: Selected node innovates original content or retweets a different meme, diminishing red memes
- **Case 3**: Selected node contains red meme and overwrites followers with it, increasing red memes

**Fluctuation Modeling**:
- Use probability generating functions (pgfs) to model changes in s due to each update case
- Aggregate fluctuations using central limit theorems to estimate effective change in s over time interval

**Central Limit Theorem Approximation**:
- Sum of random variables Z converges to a standard normal distribution (classic CLT) or stable distribution (generalized CLT)
- Relate scale and shift constants, a j,n and b j,n, to the variable s and model parameters to approximate ∆s

**Time Evolution of s**:
- Repeat sampling random variables Z and updating constants a j,n and b j,n according to CLT
- Time step is the number of updates n, with system time advancing by ∆t

**Absorbing Boundary Condition**:
- Treat s = 0 as an absorbing boundary condition, corresponding to red meme going extinct.


### B. Finite Variance Degree Distribution

**Fluctuations of Meme Density**
- When out-degree distribution pk has finite variance σ², fluctuations in meme density s have finite variance
- This is true for fluctuations of each type j
- Sum of fluctuations approximated by (Zj + bj,n) / aj,n, as per classic central limit theorem

**Computing aj,n and bj,n**
- Require mean and variance of fluctuations of each type Cj
- Mean and variance are straightforward to compute

**Drift and Diffusion Terms**
- Aggregate terms aj,n and bj,n to produce drift g(s) and diffusion h(s) terms
- Functions of s, innovation rate µ, and underlying network topology

**Integrating Equations (2) and (3)**
- Use discrete time steps (Euler-Maruyama scheme) to produce trajectories of s over time
- Initial condition for s: (1 + k)/N, where k is the number of followers and N is system size

**Dependent Variables**
- h(s) and g(s) depend on s through Table II's hCji and σj² terms
- Noise term Z associated with h(s) in Eq. (2) is drawn from standard normal distribution N (0, 1)

**Accuracy of Approximation**
- Can be seen in Fig. 1(a) and (b)


### C. Infinite-variance degree distribution

**Properties of Generating Functions g j (x) for Central Limit Theorems**

**Fluctuations in Density s:**
- Infinite variance in out-degree distribution p k leads to:
  - Non-application of classic central limit theorem
  - Generalised central limit theorem applicability
    - Fluctuations of each type j have tail probabilities decaying with power-law exponent γ (2 < γ < 3)
    - Sum of fluctuations C j is asymptotically α-stable, where α = γ − 1
  - Stable variable Z j drawn from the standardised stable distribution S(α, β)

**Underlying Degree Distribution:**
- Power-law degree distributions: p k ~ k−γ (2 < γ < 3)
- Sum of degrees is asymptotically α-stable with α = γ − 1
- Fluctuations have tail probabilities decaying with power-law exponent γ

**Tail Weights c j:**
- Determined by the relative weights of upper and lower tail probabilities of the variable being summed (β)
- For stable distributions, degrees are totally skewed to the right
- Tail weights c j of fluctuations C j are related to c through s

**Scale Term a j,n:**
- Given by Eq. (8) in the generalised central limit theorem
- Depends on α, Γ(α), sin(πα²), and c j

**Diffusion Term h(s):**
- Given by Eq. (9) in the generalised central limit theorem
- Dependent on s via tail weights c j
- Random term Z drawn from standardised stable distribution with shape parameters α and β = (−c₁ − c₂ + c₃ − c₄) / (c₁ + c₂ + c₃ + c₄)

**Differences in Eqs. (2) and (3):**
- In finite variance case, noise Z scales as Δt¹/²; in infinite variance case, scales as Δt¹/α
- Z is independent of s in Eq. (2), but dependent on s in Eq. (3) via skewness parameter β.


### D. Popularity

**Model Dynamics: Popularity (y)**
* **Popularity**: Non-negative integer indicating number of times a meme has been retweeted since appearance
* Associated with screen density s in the model introduced in Ref. [8]
* Observable in online social networks like Twitter through retweets
* Model evolution of y alongside s

**Modeling Popularity (y)**:
- Incremented by one when a selected node contains red meme and retweets rather than innovates
- Describes case j = 3 with probability π³, as per Table I
- Fluctuations in popularity modeled as n samples from Bernoulli distribution:
  * Probability of selecting red meme: π³
  * Standard deviation: √(1 − π³)²N
* Equation for popularity change: Δy = g(s)Δt + h(s)ΔtZ, with Z ~ N(0, 1)
* Boundary condition: y remains constant if s goes to zero
* Note that y is continuous due to noise term and rounded when reporting.


## III Results

**Validation of Diffusion Approximation**

1. Experimental comparison to CIC model:
   - Section III A: Verify effectiveness with various parameters
   - Fig. 1: Recover experimental results from network simulations (Fig. 1(a)) using diffusion approximation

2. Fokker-Planck equation derivation (Section III B):
   - Express time evolution of density moments for a given memory model
3. Examination of time step effect on accuracy (Section III C)


### B. Fokker-Planck equation and its moments

**Fokker-Planck Equation and Its Moments**

**Fokker-Planck Equation**:
- Describes time evolution of probability density function p(s, t) of screen fraction s as a function of time t
- Derived from Langevin equation (Eq. 2) describing single trajectory
- Cannot be solved explicitly, but can be integrated numerically

**Moments of s**:
- Given by Eq. (12): m Z hsi = 1 s^m p(s, t)ds
- By multiplying and integrating over s, obtain ordinary differential equation describing time evolution of mth moment
- Tractable for first-order terms in drift and diffusion expressions g(s) and D(s), respectively

**Solution for hsi and σs**:
- For m = 1 and 2, the resulting equation can be solved using standard techniques
- Yields Eq. (13) and Eq. (14) for hsi and σs, respectively
- **κ1** = (hki + 1)/N: initial value of s
- **κ2** = (µ+hki+(hki^2 + σ^2 )(1− µ))/µN^2: increasing function of hki and σ

**Comparison with Network Simulation**:
- Solid curves in Fig. 2 show network simulation results for CIC
- No significant systematic error apparent in σs, though linearization of diffusion term may cause it
- No such error observed in hsi (Fig. 2a)


### C Dependence on n, or time step t

**Effect of Parameter n on Diffusion Approximation:**
* Determines aggregated update events for a single time step (Eq. (1))
* Affects quality of approximation: central limit theorem and finite-difference solution
* Larger values improve normal distribution approval but may not be accurate if s varies significantly over interval.

**Competing Effects:**
1. Improved central limit theorem application when s is small, especially at early times
2. Finite-difference methods are more accurate with smaller time steps (∆t) and constant values of s

**Choosing Value of n:**
* Difficult to determine a priori
* Central limit theorem requires large enough value for approximation to apply
* Finite-difference solution benefits from small values of ∆t (n)
* In practice, a value of n = 10^3 is commonly used unless stated otherwise.

**Effect of Increasing n:**
* Visible distortion in popularity curves as n increases (Fig. 3(a) and (b))
* Solid curves represent results from diffusion approximation with various values of n.

**Numerical Results:**
* Similar settings as Fig. 1(b) for memes at age a = 10
* Baseline result is reproduced from Fig. 1(a) with n = 10^3.


## IV. DISCUSSION

**Discussion of Meme Popularity Model as Stochastic Process**
- Approximated meme popularity as a one-dimensional stochastic process
- Effective in recovering critical spreading phenomena on networks

**Variance of Degree Distribution**
- Finite variance case: only first two moments (hki and σ) of follower distribution pk play a role
- Infinite variance case: mean (hki), power-law exponent α, and tail weight c important
- Approximation using full out-degree distribution is wasteful in infinite variance case

**Independence of Memes**
- Memes can be modeled independently of one another
- Trajectories can be computed in parallel, impossible in network-based simulations

**Advantages of Diffusion Approximation**
- Allows for easier analysis and derivation of analytical tools (Fokker-Planck equation)
- Gives accurate closed-form solutions for small linearizations
- Allows for the study of different meme spreading dynamics, such as fitness models

**Limitations**
- Assumption of constant in-degree across network leads to small disagreements in results
- Extending analytical results to account for arbitrary in-degree distribution is a potential direction for future work.


---

Thank you to arXiv for use of its open access interoperability.