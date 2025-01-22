# A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics

[A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics](https://arxiv.org/abs/1902.00533)

## Table of Contents
- [Abstract](#abstract)
- [A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics](#a-model-for-meme-popularity-growth-in-social-networking-systems-based-on-biological-principle-and-human-interest-dynamics)
- [I Introduction](#i-introduction)
- [II Biomimicry principle and empirical support](#ii-biomimicry-principle-and-empirical-support)
- [III Model construction](#iii-model-construction)
  - [A. Basic principles underlying the construction of a universal model for meme popularity dynamics](#a-basic-principles-underlying-the-construction-of-a-universal-model-for-meme-popularity-dynamics)
  - [B Beyond biomimicry: incorporation of human interest dynamics](#b-beyond-biomimicry-incorporation-of-human-interest-dynamics)
  - [C. Construction of model for dynamical evolution of meme popularity](#c-construction-of-model-for-dynamical-evolution-of-meme-popularity)
- [IV. RESULTS](#iv-results)
  - [A. Simulation Results](#a-simulation-results)
  - [B. Mathematical analysis of meme popularity growth model](#b-mathematical-analysis-of-meme-popularity-growth-model)
- [V Discussion](#v-discussion)
- [Appendix](#appendix)

## Abstract

**Study on Meme Popularity Growth in Social Networking Systems**

**Research Findings**:
- Analysis of data from various online social networking (OSN) systems reveals distinct growth behaviors:
  - Linear growth on recommendation and sharing platforms
  - Plateaued or "S"-shaped growth on bookmark collection websites
  - Exponential increase on the largest microblogging website in China

**Research Questions**:
- Is there a universal mechanism with common rules to explain these empirically observed behaviors?
- Can human factors be incorporated into a base model to accurately predict meme growth dynamics?

**Proposed Approach**:
- Inspired by biomimicry, a base growth model for meme popularity in OSNs is constructed based on cell population growth dynamics in microbial ecology.
- Human factors are taken into account by incorporating a general model of human interest dynamics.
- The final hybrid model contains few free parameters that can be estimated from data.

**Significance**:
- The model is shown to be universal, successfully predicting the distinct meme growth dynamics with a few estimated parameters.
- The study represents a successful effort to incorporate principles from biology to understand online social behaviors by integrating the traditional microbial growth model into meme popularity.
- The model can provide insights into classification, robustness, optimization, and control of OSN systems.


## A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics

**Online Social Networking (OSN) Systems:**
- Complex dynamical systems with drastic variations in network structure and dynamics due to user activities, breaking news events, and user interests.
- Analysis of meme growth dynamics in OSNs has attracted recent attention.
- Previous models focusing on individual level unable to account for group popularity.
- Need for a comprehensive model incorporating heterogeneity of users and memes to describe collective dynamics of meme popularity.
- Distinct growth behaviors observed across different OSNs: linear, plateaued (or S-shaped), and exponential.
- Proposed model provides an answer to the question of whether it's possible to construct a single model that explains distinct growth behaviors.

**Model Development:**
- Equivalence between meme evolution in OSNs and microbial cell population growth.
- Probabilistic, population-level base model where a meme can experience three events: posting/forwarding (division), being overwritten (exclusion), or simple survival.
- Memes are equivalent to microscopic elements of OSNs; possible events for a meme are similar to cell division, death, and survival in a microbial system.
- Additional model ingredients beyond the biological equivalence are necessary due to meme growth being human behavior.
- Incorporation of human-interest dynamics into the base growth model results in a hybrid model for meme popularity dynamics.
- The model contains four free parameters that can be determined from data.
- The model can predict detailed meme popularity growth behaviors in all real OSNs, regardless of their origins, providing validity and universal applicability.

**Significance:**
- Ability to predict dynamical evolution of memes is of great social, economic, and political interest.
- This paper proposes a universal model for this task with minimally required information.


## I Introduction

**Online Social Networking (OSN) Systems**
* Ubiquitous and increasingly important in modern society
* Provide platforms for communications among vast users worldwide
* Empirical analyses possible due to availability of massive data sets

**Previous Research on OSNs**
* Focused on issues such as:
  + Network and opinion coevolution
  + User behavior modeling on networks
  + Dynamics of users' activity across topics and time
  + Human interest dynamics in e-commerce and communication
  + Evolutionary dynamics of forwarding network in Weibo platform
  + Competition among different Twitter topics
  + Popular topic-style analyses in Twitter-like social media
* Developed mathematical and physical models to predict scaling laws

**Limitations of Previous Models**
* Dependent on the structure of underlying social network, limiting applicability to specific types of platforms
* Lack of a quantitative, generally applicable model for dynamical evolution of key variables

**Proposed Approach**
* Exploit biological principles (biomimicry) to develop a universal model for OSN meme growth dynamics
* Incorporate human aspects through human interest dynamics model.


## II Biomimicry principle and empirical support

**Biomimicry: From Microbial Ecology to Social Networks**

**Microbial Ecology:**
- In microbial ecology, quantitative analysis of cell populations is fundamental
- Cell models are typically at the population level due to computational constraints
- Typical cell population model contains: cell division (birth), death, and survival

**Online Social Networks (OSNs):**
- Unrealistic to study behavior of every single post in OSN system
- Can obtain data reflecting collective behaviors of posts
- Meme generation, disappearance, or association with user without change is analogous to cell division, death, and survival in microbial ecology

**Meme Probabilistic Model:**
- Based on probabilistic model of cell growth and mortality
- Three possible events for a meme: it can be forwarded, excluded (overwritten), or survive
- The probabilities of these events are represented as functions of time with parameters estimated from experimental data

**Example of an OSN System:**
- Bipartite network representing users and memes connected by posting or forwarding actions
- Users linked to a meme when they create, forward, or overwrite it
- Memes can be in the "survival state" between consecutive forwarding events, or regarded as excluded after the last forwarding event

**Meme Population:**
- Growth occurs when a population of a specific meme is first posted
- Population size increases as users continue to forward it
- Between each pair of consecutive forwarding events, the meme is in the "survival state"
- After the last forwarding event, the meme is regarded as excluded or dead

**Data Sets:**
- Four data sets analyzed: Delicious, Douban Book, Douban Movie, and Douban Music
- Records, Memes, Users, and Duration listed in Table I


## III Model construction

### A. Basic principles underlying the construction of a universal model for meme popularity dynamics

**Building a Model for Meme Popularity Dynamics**

**Principles**:
- Equivalence between meme evolution in OSN systems and microbial cell population growth
- Develop probabilistic, population-level base model using the biological equivalence (biomimicry)

**Model Building Steps**:
1. **Biomimicry**: Meme can experience events equivalent to cell population growth:
   - Posting/forwarding: division (generation)
   - Being overwritten (exclusion): death
   - Simple survival: survival

2. **Human Interest Dynamics**: Incorporate human interest dynamics into the base model:
   - Intuitively correlated with meme popularity

**Model Components**:
- Hybrid model for meme popularity dynamics
- Contains four free parameters determined from data

**Model Validation**:
- Predicts detailed meme popularity growth behaviors in all real OSN systems studied
- Provides a solid ground for validity and universal applicability

**Limitations**:
- Cell growth model captures certain features but cannot capture minuscule details in each data set
- Large errors may arise when attempting to predict the time evolution of forwarding and exclusion probabilities directly from empirical data


### B Beyond biomimicry: incorporation of human interest dynamics

**Biomimicry and Human Interest Dynamics in Meme Popularity Modeling**

**Principles of Meme Popularity Dynamics:**
- **Cell division, death, and survival**: fundamental elements in microbial ecology
- **Forwarding, exclusion, and survival**: corresponding elements for meme evolution in OSN systems

**Construction of a Universal Model:**
1. Biomimicry provides insights into meme popularity dynamics
2. Human interest plays a significant role, additional factors needed
3. Base model based on cell growth model with human interest dynamics
4. Discrepancies between microbial evolution and OSN systems
5. Incorporation of human factors: human interest dynamics
6. Previous studies on human behavior and interest dynamics
7. Differentiating factors from microbial cell evolution model
8. Algebraic scaling laws in human interest dynamics
9. Rules underlying human interest dynamics: preferential return, inertial effect, exploration of new interests
10. Development of a mathematical model to explain algebraic scaling laws
11. Application of human interest dynamics in constructing meme popularity models

**Schematic Illustration of the Proposed Biomimicry-based Hybrid Model:**
- Activated users selected based on sigmoid curve
- Forwarding actions occur at different times following probability p(τ)
- User has probability ρ to forward a new meme and (1 − ρ) for old one.

**Assumptions:**
- Probabilities p(τ) and ρ from human interest dynamics
- Individual interevent time follows τ−α distribution with sigmoid curve
- Activation curves exhibit agreement at detailed level, can be fitted by a single or multiple sigmoid functions
12. Comparison of empirical data sets: Delicious, Douban Book, Douban Movie, Douban Music, Weibo (Figs 4 & 5)
13. Parameters estimation from least-square fitting subject to standard Kolmogorov-Smirnov test.


### C. Construction of model for dynamical evolution of meme popularity

**Meme Popularity Evolution Model**

**Start:**
- Meme diffusion and human interest dynamics
- Microbial cell evolution and human behavior observations

**Model Foundations:**
1. Fixed group of users
2. Time steps: enabled users, meme posting/forwarding
3. Active user fraction (PA(L)): sigmoid function with parameters B and C
   - PA(L) ∼ 1 + e^(-B·(L−C))
4. Interevent time τ for an active user: power law distribution
5. Probability of forwarding old or new memes
   - (1 − ρ): old meme
   - ρ: new meme
6. Meme creation and diffusion modeled using microbial cell diffusion

**Active User Fraction:**
- PA(L) follows sigmoid function
  - 1 + e^(-B·(L−C))
- L represents the number of users in the group

**Interevent Time:**
- Power law distribution for an active user
- Determines when a meme is forwarded or posted by that user

**Meme Forwarding Probabilities:**
- Active user has probability (1 − ρ) to forward old memes
- Has probability ρ to forward new memes.


## IV. RESULTS

### A. Simulation Results

**Model Simulation**
- Consider a fixed group of **Nf = 1000 users**
- At each time step t, **Nf · PA(t)** randomly selected users become active
- Interevent time and event determination activities depend on two parameters: **α** and **ρ**

**Generating Forwarding Actions**
- For each activated user Ui:
  - Time interval between forwarding actions follows the distribution **p(τ) ~ τ−α**
  - Probability to forward a new meme is **ρ**, probability to forward an old meme is **(1 − ρ)**

**Recording Forwarding and Exclusion Probabilities**
- Record forwarding and exclusion probabilities at each time for different choices of parameters

**Empirical Data Analysis**
- Truncate F and W curves at peak values to exclude artificial death events
- Typically occur around 80% total duration

**Hybrid Model Parameters**
- Four parameters: **B**, **C**, ** Alf**, and ** Chi**
  - Regulate sigmoid activation rate, interevent time intervals, and event determination probabilities

**Simulating the Model for Different Parameter Choices**
- Compare results when modifying one parameter while keeping others constant
- Nominal values: **B = 0.5**, **C = 0.5**, ** Alf = 1.5**, and ** Chi = 0.5**

**Impact of Parameters on Forwarding and Exclusion Probabilities**
- **C**: Determines when users get activated, affecting early time probabilities (Figs. 6(a) and 6(d))
- ** Alf**: Indicates meme interevent time distribution concentration, influencing early growth (Figs. 6(b) and 6(e))
- ** Chi**: Affects new meme probability, leading to delayed increment in forwarding probabilities (Figs. 6(c) and 6(f))

**Model Validation by Setting Parameters from Real Data**
- Compare predicted normalized meme popularity growth curves with real data (Fig. 7)
- Agreement is remarkable regardless of data set nature and growth dynamics

**Conclusion**
- Model predictions agree well with real data at a detailed level, even for distinct meme popularity behaviors


### B. Mathematical analysis of meme popularity growth model

**Meme Popularity Model**

**Model Equation**:
- Eq. (1) describes meme population at time t
- Depends on numbers of survived and forwarded memes

**Survived and Forwarded Meme Relations**:
- N(t) = S(t)
  - S(t) described by relation: 
    ```
    0.0 0.5 1.0 0.0 0.5 1.0 0.0 0.5 1.0
    0.0 0.5 1.0 0.0 0.5 1.0 0.0 0.5 1.0
    Delicious Model Theory
    0.0 0.5 1.0 0.0 0.5 1.0 0.0 0.5 1.0
    Weibo Model Theory
    L      L   Label c
    ```
- Represents meme popularity growth curves for various OSN systems (Douban Book, Douban Movie, Douban Music, Delicious, and Weibo)

**Model Prediction vs. Real Data**:
- Figure 7 shows comparison between model predicted and real growth curves
- Dashed and solid curves represent model prediction and real results, respectively
- Shows good agreement for different types of growth behaviors: linear, \S-shape, and exponential

**Model Parameters**:
- B, C, and  estimated from data
- Different values lead to characteristically different meme popularity dynamics

**Analytic Solutions**:
- Solved Eq. (7) for various parameter choices
- Agrees well with empirical results

**Impact of Parameters on Meme Popularity Dynamics**:
- **B** and **C** in activation sigmoid function:
  - **B**: controls shape of function
  - **C**: modulates value of L when activation rate reaches 0.5
- Large **C** delays onset of popularity growth to later time, but grows at large rate when it starts
- Moderate **B** and **C** lead to \S-shape growth curves
- Small **B** and moderate **C** result in approximately linear growth behavior
- **C**: does not affect shape of growth curve, but affects absolute popularity value


## V Discussion

**Dynamics of OSN Systems: Understanding Meme Popularity Growth**

**Background:**
- Rapid growth of Online Social Networking (OSN) systems
- Replacing traditional social networks
- Importance in understanding for societal wellbeing
- Previous efforts to analyze OSNs through data analysis and quantitative modeling

**Challenges:**
- Diverse behaviors exhibited by OSNs
- Lack of common growth behavior for meme popularity
- Single universal model to capture different growth dynamics?

**Meme Popularity Growth Dynamics:**
- Analysis of empirical data from various OSNs reveals lack of common behavior: linear, S-shaped, or exponential
- Need for a model that can capture and predict characteristically different growth behaviors
- Free parameters depending on specific system

**Inspiration from Microbial Ecology:**
- Dynamics of cell evolution in microbial ecology similar to meme popularity growth dynamics
- Each event (division, death, survival) associated with probability function
- Significant resemblance between cell and meme popularity growth dynamics

**Hybrid Model:**
- Combines fundamental dynamic elements of underlying growth and spread of meme popularity
- Attributes modeling element beyond cell growth to human interest dynamics
- Four free parameters determinable from data

**Predictions:**
- Demonstrates ability to predict detailed, characteristically distinct growth dynamics of meme popularity in diverse OSNs
- First time a universal model has been successfully developed for capturing and predicting dynamical evolution of broadly nested entity in modern social networking systems

**Future Directions:**
- Additional factors not considered: friendship reciprocity, visibility, intrinsic interaction among users, or regular operations on past memes
- Current model does not account for user intrinsic activities on meme popularity and peer influences
- Potential applications: network design optimization, meme population control, robustness enhancement against external attacks.


## Appendix

**Results from Empirical Data Sets**
- Number of occurrences for each event in empirical data sets
  - Figures A1 and A2 illustrate results on numbers of forwards and overwrites, respectively
    * Line represents average number of forwards/overwrites
    * Shadow area represents error

**Effects of Parameter Variations**
- Users' intra-event activities described by two probabilities:
  - Probability of low-quality information
  - Probability of high-quality information

**Literature Cited**
- Various researchers have studied the dynamics of information spreading on social media platforms using different models and data sets:
  - Luo et al. (2017)
    * Inferring personal economic status from social network location
  - Lehmann et al. (2012)
    * Dynamical classes of collective attention in Twitter
  - Zaman et al. (2014)
    * Bayesian approach for predicting the popularity of tweets
  - Borge-Holthoefer et al. (2017)
    * Emergence of consensus as a modular-to-nested transition in communication dynamics
  - Hawkes (1971)
    * Spectra of self-exciting and mutually exciting point processes
  - Zhao et al. (2015)
    * Seismic: A self-exciting point process model for predicting tweet popularity
  - Pastor-Satorras and Vespignani (2001, 2015)
    * Epidemic spreading in scale-free networks
  - Trucco (1959, 1965, Part I & II)
    * Mathematical models for cellular systems: the von Foerster equation
  - Lu et al. (2004), Kutalik et al. (2005), Wang et al. (2010), Horowitz et al. (2010), Stukalin et al. (2013), Ribeiro (2014), Antunes and Singh (2015), Greenman and Chou (2016), Hierarchical kinetic theory of birth, death and aging in age-structured interacting populations
  - Widder et al. (2016)
    * Challenges in microbial ecology: building predictive understanding of community function and dynamics
  - Zhou et al. (2008), Gonionaleau et al. (2008), Song et al. (2010), Szell et al. (2012), Wu and Huberman (2007), Ye et al. (2010), Zhou et al. (2008), Ramasco et al. (2008), Corder and Foreman (1959), Trucco (1965, Part I & II)

**Additional References**
- Various other references related to the topic.


---

Thank you to arXiv for use of its open access interoperability.