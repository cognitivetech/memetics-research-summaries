# Competition-induced criticality in a model of meme popularity

[Competition-induced criticality in a model of meme popularity](https://arxiv.org/abs/1305.4328)

## Table of Contents

- [Competition-induced criticality in a model of meme popularity](#competition-induced-criticality-in-a-model-of-meme-popularity)
- [1305.4328](#13054328)
- [SUPPLEMENTARY MATERIAL](#supplementary-material)
- [S1 Derivation of Equation (2)](#s1-derivation-of-equation-2)
- [S2 Inverting PGFs using Fast Fourier Transforms](#s2-inverting-pgfs-using-fast-fourier-transforms)
- [S3 Old-age asymptotics](#s3-old-age-asymptotics)
- [S4 Assumptions of the model, and relevance to real networks](#s4-assumptions-of-the-model-and-relevance-to-real-networks)
- [S5 A modified model, with restricted retweeting](#s5-a-modified-model-with-restricted-retweeting)- [1305.4328](#1305-4328)
- [SUPPLEMENTARY MATERIAL](#supplementary-material)
  - [S1 Derivation of Equation (2)](#s1-derivation-of-equation-2)
  - [S2 Inverting PGFs using Fast Fourier Transforms](#s2-inverting-pgfs-using-fast-fourier-transforms)
  - [S3 Old-age asymptotics](#s3-old-age-asymptotics)
  - [S4 Assumptions of the model, and relevance to real networks](#s4-assumptions-of-the-model-and-relevance-to-real-networks)
  - [S5 A modified model, with restricted retweeting](#s5-a-modified-model-with-restricted-retweeting)

## 1305.4328

**Competition-Induced Criticality in a Model of Meme Popularity**

**Authors**: James P. Gleeson, Jonathan A. Ward, Kevin P. O’Sullivan, and William T. Lee

**Affiliations**:
- MACSI, Department of Mathematics & Statistics, University of Limerick, Ireland
- Centre for the Mathematics of Human Behaviour, Department of Mathematics and Statistics, University of Reading, Whiteknights, UK

**Dated**: 24 Dec 2013 (Dated: 21 Jan 2014)

**Keywords/PACS numbers**:
- 89.65.-s
- 05.65.+b
- 89.75.Fb
- 89.75.Hc

**Summary**:
- **Heavy-tailed distributions of meme popularity occur naturally** in a model of meme diffusion on social networks.
- **Competition between multiple memes for the limited resource of user attention** is identified as the mechanism that poises the system at criticality.
- The popularity growth of each meme is described by a **critical branching process**, and **asymptotic analysis predicts power-law distributions of popularity with very heavy tails (exponential α < 2, unlike preferential-attachment models)**.
- This is similar to the **power-law distributions of popularity** seen in empirical data.


## SUPPLEMENTARY MATERIAL

### S1 Derivation of Equation (2)

**Probability Generating Functions (PGF)**
* G(a,x): PGF of excess popularity distribution for a meme seeded at time a
* H(a,x): PGF of popularity distribution
* Relation between G(a,x) and H(a,x): H(a,x) = xG(a,x)f(G(a,x))
* G(k)(a,x): PGF of excess popularity distribution for a meme seeded by a node with out-degree k
* Outcome Analysis for G(k)(a,x)
  * Outcome (a): Screen overwritten by another meme, setting generating function to 1
  * Probability: zΔt
  * Contribution to G(k)(a,x): zΔtG(k)(a−∆t,x)
  * Outcome (b): Node selected as updater and innovates, terminating tree
  * Probability: µΔt
  * Contribution to G(k)(a,x): µΔt
  * Outcome (c): Node selected for update and retweets, adding size and starting new tree
  * Probability: (1−µ)Δt
  * Contribution to G(k)(a,x): (1−µ)ΔtG(k)(a−∆t,x)[G(a−∆t,x)]k
  * Outcome (d): Survival of tree without other outcomes occurring
  * Probability: 1−(z+1)Δt
  * Contribution to G(k)(a,x): (1−(z+1)Δt)G(k)(a−∆t,x)
* Summing contributions from all possible outcomes gives the expression for G(k)(a,x), correct to first order in Δt.
* Taking the limit Δt→0 yields an ordinary differential equation for G(k)(a,x).

**Relation between G(a,x) and G(k)(a,x)**
* Averaging over possible out-degrees of root node gives the following equation for G(a,x): ∂G∂a = z+µ−(z+1)G+(1−µ)x/summationdisplay kpkG(k)[G]k

**Approximation and Simplification**
* Approximation: G(k)[G]k ≈ Gf(G), which leads to a single differential equation for G(a,x).
* This simplifying moment-closure assumption will be examined in detail in further work.

**Generalizations**
* Allowing each node's screen to have capacity c≥1 and allowing tweeted memes to be accepted onto followers’ screens with probability λ≤1:
  * The resulting equation for G(a,x) is given by Eq. (S7).
  * Reduces to the base case of Eq. (2) in the main text for c=1 and λ=1.
* Mean popularity of age-a memes: μ(a)=∂H∂x(a,1) = 1+(λz+1)∂G∂x(a,1).
* Higher moments of the popularity distribution qn(a) can be obtained by repeated differentiation of Eq. (S7).
* Probabilities q1(a) for small values of n can be determined by expanding G(a,x) as a Taylor series about x=0.


### S2 Inverting PGFs using Fast Fourier Transforms

**Meme Popularity Probability Calculation**

**Determining qn(a)**
- Use PGF H(a,x) from Eq. (S14): qn(a) = n! * dH(a,x)/dx as x approaches 0
- Numerical differentiation inaccurate for large values of n
- Contour integration in complex x-plane instead [35, 36]

**Contour Integration Formula**
- Cauchy's theorem: qn(a) = 1 / (2πi) * ∫CH(a,x) *(x - (n+1)) dx
- All poles of H(a,x) outside contour C
- Complex integration with unit circle as a common choice [35]

**Integration Formula in Terms of eiθ**
- Substituting x = eiθ: qn(a) = 1 / (2πi) * ∫CH(a,eiθ) * e^(-inθ) dθ

**Numerical Integration Approximate Formula**
- Numerical integration using trapezoidal rule with M points: qn(a) ≈ 1 / M * sum((H(a,e^(iθ)) * e^(-2πin/M)), m=0, M-1) [36, 37]

**Implementation in Octave/Matlab**
- Code available for download at www.ul.ie/sdcs/people/kevin-osullivan


### S3 Old-age asymptotics

**Lemma 1:**
- Let **Φ(x)** be the PGF for distribution **πk**, with asymptotic series expansion (S19) as x→1:
- The leading order asymptotics of **πk** is given by equation (S20): **πk ~ c1Γ(−β1)k−β1−1** as n → ∞

**Lemma 2:**
- Let **H(∞,x)** be the PGF for distribution **qn**, with asymptotic behavior (S24) as w→0:
- The asymptotic form of **H(∞,x)** is given by equation (S25): **H(∞,1−w) ~ 1−w−(λz+1)φ(w)** as w→0
- Applying Lemma 1 allows the asymptotics of **qn** to be determined from the nonanalytic part of **φ(w)**.

**Case 1: f′′(1) = ∞, µ = 0:**
- The leading order behavior of G is given by equation (S29): **G(∞,1−w) ~ 1−1λ(DΓ(1−γ))−1γ−1w1γ−1** as w→0
- The asymptotic form of qn is given by equations (S30) and (S31): **qn ~ Bn−γ**, where **B = −(λz+1)(DΓ(1−γ))−1γ−1λΓ/(1−γ)**.

**Case 2: f′′(1) = ∞, 0< µ <1:**
- The leading order behavior of G is given by equation (S33): **G(∞,1−w) ~ 1−1−µµ(λz+1)w+DΓ(1−γ)λγ−1(1−µ)(λz+1)γ−1** as w→0
- The asymptotic form of qn is given by equations (S34) and (S35): **qn ~ Cn−γ**, where **C = D(λz+1)/(λ(1−µ)μ(λz+1)γ−1)**.

**Case 3: f′′(1) = ﬁnite, µ = 0:**
- The leading order behavior of G is given by equation (S36): **G(∞,1−w) ~ 1−λz+12f′′(1)/(2λ2)** as w→0
- The asymptotic form of qn is given by equations (S37) and (S38): **qn ~ An−3/2**, where **A = (λz+1)/(2πλf′′(1)+2z)**.

**Case 4: f′′(1) = ﬁnite, 0< µ ≪1:**
- The leading order behavior of G is given by equation (S39): **G(∞,1−w) ~ −µ(λz+1)+/radicalbig{µ2(λz+1)2+2λ(1−µ)2(λf′′(1)+2z)w}** as w→0
- The asymptotic form of qn is given by equation (S41): **qn ~ An−3e−nκ**, where **A = 2λ(λf′′(1)+2z)/(µ2(λz+1)2)** and **κ = 2λ(λf′′(1)+2z)**.


### S4 Assumptions of the model, and relevance to real networks

**Branching Process Theory Assumptions**
- Assumes underlying network is tree-like: no loops exist
- Assumes every node follows approximately 10 other nodes: in-degree distribution is homogeneous

**Real-World Network Violations**
- Spanish 15M network: 44% of links are reciprocal (node A follows node B, and vice versa)
- Tree-based theory performs well despite these violations on real networks

**Simulations on Rewired Networks**
- Pjk-rewiring: preserves joint distribution of in- and out-degrees, reduces clustering
- Pk-rewiring: preserves out-degree distribution, replaces in-degree with Poisson distribution, reduces loops

**Comparison of Simulation Results**
- Original network (blue squares), pjk-rewired network (green triangles), and pk-rewired network (red circles)
- Theory curves match closely to simulations on pk-rewired network
- Differences between original and pjk-rewired results are due to non-Poissonian in-degree distribution, almost negligible effect of clustering and loops.

**Future Work**
- Develop a theory that incorporates information on the network's in-degree distribution while retaining tree-based derivation for zero-clustering networks.


### S5 A modified model, with restricted retweeting

**Model Features:**
- Memes remain on users' screens after retweeting, allowing for multiple retweets of the same meme by a single user (except if it's an entire message)
- Modification of the basic model: nodes keep track of previously tweeted memes; if a node has already retweeted a meme, no action is taken
- Similar results are observed in numerical simulations with modified rule on network with z-regular out-degrees and µ=0 (Fig. S4)
- Criticality mechanism not strongly affected by the modification

**Modification Rule:**
- Node's screen is set to "empty" state after tweeting event
- Prevents successive tweets of the same meme but allows for rediscovery
- Results in a non-zero fraction of empty screens at any time t

**Steady-State Fraction of Non-Empty Screens:**
- Mean-field approach used to obtain the steady-state fraction of infected (non-empty) screens
- When a retweeting event occurs, subsequent emptying of tweeting node's screen reduces the number of infected screens by one
- Broadcast to followers leads to previously empty screens becoming non-empty, resulting in an expected change of zero in the number of infected screens at dynamical equilibrium

**Outcomes under Modified Rule:**
- (a) Overwriting of screen S1 by a meme tweeted by another node: probability zi∆t=(z−1)∆t
- (c) New contribution to the overall probability due to emptying of the screen after tweeting: ∆tx[G(a−∆t,x)]k
- (d) Probability of outcome (d): 1−(zi∆t+∆t)=1−z∆t

**Differential Equation for G(k)(a,x):**
- Partially derived equation (S45) from the modified rule
- Similar to Eq. (S7) in the original model but with z−1 instead of z

**Equation for G(a,x):**
- Derived equation (S46) from the differential equation for G(k)(a,x)
- Reveals critical behavior: mean popularity grows linearly with age, old-age asymptotics are similar to µ=0 cases determined in Sec. S3.


---

Thank you to arXiv for use of its open access interoperability.