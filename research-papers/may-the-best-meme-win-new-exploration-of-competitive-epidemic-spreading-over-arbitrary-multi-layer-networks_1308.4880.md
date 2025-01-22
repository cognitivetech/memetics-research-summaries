# May the Best Meme Win!: New Exploration of Competitive Epidemic Spreading over Arbitrary Multi-Layer Networks

[May the Best Meme Win!: New Exploration of Competitive Epidemic Spreading over Arbitrary Multi-Layer Networks](https://arxiv.org/abs/1308.4880)

## Table of Contents

- [May the Best Meme Win!: New Exploration of Competitive Epidemic Spreading over Arbitrary Multi-Layer Networks](#may-the-best-meme-win-new-exploration-of-competitive-epidemic-spreading-over-arbitrary-multi-layer-networks)
- [arXiv:1308.4880v2](#arxiv13084880v2)
- [I. INTRODUCTION](#i-introduction)
- [II. COMPETITIVE EPIDEMICS IN MULTI-LAYER NETWORKS](#ii-competitive-epidemics-in-multi-layer-networks)
- [III. MAIN RESULTS](#iii-main-results)
- [A. Threshold Equations](#a-threshold-equations)
- [B. Characterization of Threshold Curves](#b-characterization-of-threshold-curves)
- [C. Standardized Threshold Diagram and a Global Approximate Formula](#c-standardized-threshold-diagram-and-a-global-approximate-formula)
- [D. Multi-layer Network Metric for Competitive Spreading](#d-multi-layer-network-metric-for-competitive-spreading)
- [E. Numerical Simulations](#e-numerical-simulations)
- [IV. DISCUSSION AND CONCLUSION](#iv-discussion-and-conclusion)
- [Appendix: Selected Proofs](#appendix-selected-proofs)- [arXiv:1308.4880v2](#arxiv-1308-4880v2)
- [I. INTRODUCTION](#i-introduction)
- [II. COMPETITIVE EPIDEMICS IN MULTI-LAYER NETWORKS](#ii-competitive-epidemics-in-multi-layer-networks)
- [III. MAIN RESULTS](#iii-main-results)
  - [A. Threshold Equations](#a-threshold-equations)
  - [B. Characterization of Threshold Curves](#b-characterization-of-threshold-curves)
  - [C. Standardized Threshold Diagram and a Global Approximate Formula](#c-standardized-threshold-diagram-and-a-global-approximate-formula)
  - [D. Multi-layer Network Metric for Competitive Spreading](#d-multi-layer-network-metric-for-competitive-spreading)
  - [E. Numerical Simulations](#e-numerical-simulations)
- [IV. DISCUSSION AND CONCLUSION](#iv-discussion-and-conclusion)
- [Appendix: Selected Proofs](#appendix-selected-proofs)

## arXiv:1308.4880v2

**Study Overview:**
- Title: "May the Best Meme Win! New Exploration of Competitive Epide mic Spreading over Arbitrary Multi-Layer Networks" (arXiv:1308.4880v2 [physics.soc-ph])
- Authors: Faryad Darabi Sahneh and Caterina Scoglio
- Department: Electrical and Computer Engineering, Kansas State University

**Background:**
- Extension of Single Virus Propagation model (SIS epidemic model) to Competitive Virus Propagation over a two-layer network with distinct transmission routes.

**Key Findings:**
1. **SI 1SI2S Epidemic Model**: Two exclusive, competitive viruses spreading through different layers in a network.
2. **Survival Threshold and Winning Threshold**: Analytical results determining extinction, mutual exclusion, and coexistence of the viruses.
3. **Coexistence**: Rigorously proven region of coexistence and quantitated via interrelation of central nodes across network layers.
4. **Importance**: Great potential for application to broader classes of multi-pathogen spreading over multilayer and interconnected networks.

**Keywords:** Competitive epidemic spreading, multilayer networks, mutual exclusion, coexistence, SI1SI2S, survival threshold, winning threshold.

**Network Layers**:
- Represent distinct transmission routes of the viruses.
- Central nodes have little to no overlapping for coexistence.
- Coexistence is impossible if network layers are identical but possible if they have distinct dominant eigenvectors and node degree vectors.

**Impact:**
- Positive correlation of network layers makes it difficult for a virus to survive (difficult for one virus to "win") in a network with positively correlated layers.
- Negatively correlated layers make survival easier but total removal of the other virus more difficult.


## I. INTRODUCTION

**Introduction:**
- Multiple virus spreading within a single population involves rich dynamics [1]
- Applications extend beyond physiological viruses to products, memes, pathogens [5–7]
- Mathematical challenge due to distinct networks and multiple interaction possibilities among viruses
- Current knowledge limited on how network topology influences pathogen fate
- Systems often mathematically intractable, hindering conclusive results on spreading of multiple viruses on multi-layer networks

**Previous Research:**
- Newman [10] studied spread of two SIR viruses through a single contact network using bond percolation
  - Coexistence threshold above classical epidemic threshold
- Karrer and Newman [1] extended work to more general case where both viruses spread simultaneously
- Wang et al. [12] studied competitive SIS viruses in scale-free networks, proved exclusive
- Funk and Jansen [2] investigated effects of layer overlapping on two competitive viruses in a two-layer network
- Granell et al. [9] studied disease and information co-propagation in a two-layer network
  - Meta-critical point for epidemic onset leading to disease suppression
- Wei et al. [13] studied SIS spreading of two competitive viruses on an arbitrary two-layer network
  - Introduced Eigenpredict tool to predict viral dominance

**Current Study:**
- Addresses problem of two competing viruses propagating in a host population with distinct contact networks
- Focuses on SI1SI2S model as simplest extension from SIS model for single virus propagation
- Challenges argument that "the meme whose first eigenvalue is larger tends to prevail eventually" [4]
  - Eigenvalues do not directly indicate higher final fraction of infected nodes when comparing distinct network layers
  - Largest eigenvalue does not discuss joint influence of network topology unless symmetry or homogeneity is assumed
- Derives formulae describing effect of individual network layers and their interrelations
- Quantitates interrelations in terms of spectral properties of a set of matrices
- Analytical results determine extinction, mutual exclusion, and coexistence of the viruses
- Shows possibility of coexistence in SIS-type competitive spreading over multilayer networks
- Employs novel multilayer network generation framework to obtain networks with identical graph properties but varying interrelation


## II. COMPETITIVE EPIDEMICS IN MULTI-LAYER NETWORKS

**Competitive Epidemics in Multi-Layer Networks**

**Network Topology**:
- Population of size N with two viruses propagating on a two-layer network
- Represents the network as G(V,EA,EB), where:
  - V is the set of vertices (nodes)
  - EA and EB are sets of edges (links)
  - Aij = 1 if node j can transmit virus 1 to node i, otherwise 0
  - Bij = 1 if node j can transmit virus 2 to node i, otherwise 0
- Assumes the network layers are symmetric: aij = ajj and bij = bji

**SI1SI2S Model**:
- Extends the continuous-time SIS spreading model of a single virus on a simple graph
- Models competitive viruses propagating through two distinct transmission routes
- Each node is either "Susceptible," "I1-Infected," or "I2-Infected"
  - Virus 1 spreads exclusively via EA edges
  - Virus 2 spreads only through EB edges
- Infection and curing processes for viruses are characterized by (β1,δ1) and (β2,δ2), respectively
- **Effective infection rate**: Ratio of infection rate to curing rate, measures the expected number of attempts to infect neighbors
- Model is a coupled Markov process, mathematically intractable due to the exponential explosion of its state space
- A first-order mean-field approximation provides differential equations for the evolution of virus probability

**No-Spreading Threshold**:
- Linearization of the SI1SI2S model at the healthy equilibrium (p1,i = p2,i = 0) demonstrates the exponential extinction condition
- If τ1 < 1/λ1(A) and τ2 < 1/λ1(B), any initial infections exponentially die out
- This critical value is referred to as the **no-spreading threshold**

**Problem Statement**:
- Wei et al. detailed the no-spreading condition:
  - If τ1 < 1/λ1(A), virus 1 does not spread, exponentially dying out
  - Exponential extinction of both viruses occurs only if τ1 < 1/λ1(A) and τ2 < 1/λ1(B)
- This paper addresses the following questions:
  1. Will both viruses survive (coexistence) or will one virus completely remove the other (mutual exclusion)?
  2. Which characteristics of multi-layer network structure allow for coexistence?
- These questions pertain to the long-term behavior of competitive spreading dynamics


## III. MAIN RESULTS

**Competitive Virus Spreading on Multi-layer Networks: Bifurcation Analysis of SI1SI2S Model**

**Background:**
- Objective: study long-term behavior of a system with two competing viruses (SI1SI2S model) on a network
- Use bifurcation analysis to determine critical values for steady-state behavior

**Bifurcation Analysis of SIS Model:**
- Determines threshold at which non-healthy equilibrium emerges [14]
- No-spreading and survival thresholds coincide
- Distinct from SI1SI2S model due to competition between viruses

**Competitive Virus Spreading:**
- Survival threshold larger than no-spreading threshold
- Increases with aggressiveness of other competitive virus
- Aggressive virus can completely remove competing virus
- Two additional thresholds: winning threshold for each virus

**Determining Thresholds:**
- Four quantities involved: survival threshold (Virus 1), multilayer network topology, and aggressiveness of competing virus
- Winning thresholds can be deduced from survival thresholds
- Only focus on survival threshold of Virus 1 due to expression duality

**Complex Interdependency:**
- Understanding the system hindered by complex interdependency of factors
- Impossible to obtain complete analytical solution, but characterize possible solutions with explicit analytical expressions.

**Unique Contribution:**
- Provides unique insights into competitive spreading over multi-layer networks
- Significant implications for role of multilayer network topology in understanding the behavior of competing viruses.


### A. Threshold Equations

**Threshold Equations for SI1SI2 Model**
- Bifurcation analysis of equilibrium equations (3-4) identifies critical values for effective infection rates τ1 and τ2
- Survival threshold value τ1c: smallest effective infection rate that virus 1 steady state infection probability is positive for τ1 > τ1c
- For a given τ2, survival threshold curve Φ1(τ2) is the monotonically increasing function of τ2 that yields the critical value τ1c

**Defining Survival Threshold**
- Given virus 2 effective infection rate (τ2), the survival threshold value for virus 1 (τ1c) is found by:
  - Finding non-trivial solution for wi > 0 in equation (6)
  - Equilibrium equations (3) and (4) define yi as the solution
  - Eigenvalue problem with eigenvector wi = dp∗1,i / τ1 yields the survival threshold

**Finding Survival Threshold Curve**
- By finding yi for all possible values of τ2 and then τ1c from equation (8), we obtain the survival threshold curve Φ1(τ2) for virus 1
- This curve divides the (τ1,τ2) plane into regions where both viruses extinct, only virus 1 survives, only virus 2 survives, and both survive and coexist.

**Winning Threshold**
- Winning threshold: value of τ1 such that for τ1 > τ†1, only virus 1 can survive, while virus 2 is completely suppressed
- The winning threshold of virus 1 is the inverse function of the survival threshold curve Φ2(τ1), denoted as Ψ1(τ2) according to equation (9).


### B. Characterization of Threshold Curves

**Characterization of Threshold Curves**

**Conditions for Viral Coexistence**:
- Explicit analytical solutions not feasible, but interrelations of contact layers are quantitated
- Conditions given for mutual exclusion and coexistence of viruses
- Approach finds solutions to (6) and (7) for values of τ2 close to 1 /λ1(B) and large values of τ2
- Eigenvalue perturbation technique used to find explicit solutions

**Threshold Curve Behavior**:
- Results for τ2 close to 1 /λ1(B) apply where competitive viruses are non-aggressive
- Results for τ2 very large correspond to aggressive competition
- Behavior of the competitive spreading process is an interpolation of the extreme scenarios

**Virus 1 Survival Threshold (τ1c)**:
- Depends on eﬀective infection rate of virus 2 (τ2), spectral radius ratio of each network layer in isolation, and the influence of interrelations between the layers
- If the spectral central nodes of GA are insignificant in GB, the virus 1 survival threshold is not influenced by virus 2's infection rate
- If the spectral central nodes of GA have high spectral centrality in GB, the dependency of τ1c on τ2 is significant

**Virus 2 Survival Threshold (τ2c)**:
- The inverse of the spectral radius of D−1\nBA for large values of τ2
- Indicates the influence of interrelations between the layers
- If λ1(D−1\nBA) is large, virus 1's survival threshold does not increase significantly by virus 2's infection rate

**Coexistence Region**:
- Coexistence is possible when the two network layers are not identical (GA ≠ GB):
  - Non-aggressive competitive viruses can coexist if the dominant eigenvectors of GA and GB do not completely overlap
  - Aggressive competitive viruses can coexist if the node-degree vectors of GA and GB are not parallel


### C. Standardized Threshold Diagram and a Global Approximate Formula

**Standardized Threshold Diagram and Global Approximate Formula**

**Exploring efficient characterization of threshold curves using extreme scenarios**:
- Proposed standardized threshold diagram
- Threshold curves plotted in a [0,1]×[0,1] plane for (x,y) = (1λ1(B)τ2, 1λ1(A)τ1), axes scaled by layer spectral radius and inverted
- Curves start from origin to point (1,1)

**Slope of survival curve**:
- m0 = λ1(B)/λ1(A)/λ1(D−1)BA
- m1 = summation[text]{v2}{A,ivB,i} / summation[text]{v3}{B,i}
- Respectively, the slopes of the survival curve of virus 1 at (0,0) and (1,1)

**Parametric approximation for survival threshold curve**:
- Bezier curve equation:
  - x(σ) = 2σ(1−σ) / na + σ² / (1∕1)
  - y(σ) = nb / ma + m0(1−m1)
- Connecting (x,y) = (0,0) to (x,y) = (1,1) for σ ∈ [0,1]
- Satisfying the slope constraints (m0) and (m1) if a and b are chosen as:
  - a = 1−m1
  - b = m0(1−m1)
  - m0(1−m1)

**Approximate standardized threshold diagram**:
- Bezier curve (18) approximates the standardized threshold diagram for the full range of τ1 > 1/λ1(A) and τ2 > 1/λ1(B) using only spectral information of a set of matrices.


### D. Multi-layer Network Metric for Competitive Spreading

**Multi-layer Network Metric for Competitive Spreading: Coexistence**

**Definition of Coexistence Topological Index (Γs(G)): **
- Measures possibility of coexistence in a multi-layer network G = (V, EA, EB) for non-aggressive spreading
- Formula: Γs(G) = 1 - ΣvB, iv2\nA,i / ΣvA, iv2\nB,i * Σv3, i / Σv3, A,i
- Values range from 0 to 1:
  - 0 implies vA = vB (coexistence is rare and one virus is the absolute winner)
  - Close to 1 indicates coexistence is very possible on G
- Used to discuss coexistence of non-aggressive competitive viruses

**Definition of Coexistence Topological Index (Γl(G)): **
- Measures possibility of coexistence in a multi-layer network G = (V, EA, EB) for aggressive competitive spreading
- Formula: Γl(G) = 1 / [λ1(D−1\nBA).λ1(D−1\nAB)]
- Values range from 0 to 1:
  - 0 implies dA = dcB (coexistence is rare and one virus is the absolute winner)
  - Close to 1 indicates coexistence is very possible on G
- Used to discuss coexistence of aggressive competitive viruses


### E. Numerical Simulations

**Two-Layer Network Generation for Numerical Simulations**

**Objective**:
- Test analytical formulae
- Investigate effect of interrelation on competitive epidemics

**Network Generation**:
- Contact network GA: Random geometric graph with N=1000 nodes, r<3log(N)/π to ensure connectivity
- Contact network GB: Scale-free network generated by Barabasi–Albert model, then associated with GA to achieve certain degree correlation (ρ)
  - Negatively correlated: ρ=-0.47
  - Neutrally correlated: ρ=0
  - Positively correlated: ρ=0.48

**Steady-State Infection Fraction**:
- For single virus, steady-state infection fraction (p̄ss) illustrates threshold behavior based on effective infection rates
- For two competing viruses (SI1SI2S model), p̄ss of virus 1 exhibits threshold at τ1=τ1c for given τ2

**Competitive Spreading Model**:
- Effective infection rate of virus 2 fixed at τ2=61λ1(B)
- Normalized horizontal axis to τ1λ1(A)
- Three graphs shown in FIG. 4 for visualization convenience with N=100 nodes instead of actual N=1000
  - Negatively correlated: GB has high degree nodes that also have high degree in GA, lower right
  - Uncorrelated: GB shows no clear association, lower left
  - Positively correlated: GB has high degree nodes that also have high degree in GA, upper left

**Threshold Behavior**:
- Survival threshold (τ1c) and winning threshold (τ†1) identified in FIG. 5
  - For τ1≤τ1c, p̄ss1=0: extinction region for virus 1
  - For τ1>τ†1, p̄ss1=0: extinction of virus 2, marking winning range for virus 1
- Coexistence region: For τ1∈(τ1c,τ†1), both viruses persist in the population

**Dependence on Network Layer Interrelation**:
- Positively correlated GB makes it more difficult for virus 1 to survive, larger survival threshold τ1c
- Negatively correlated GB impedes virus 1 from completely suppressing virus 2, larger winning threshold τ†1

**Analytical Approximation**:
- FIG. 8 shows standardized threshold diagram with predictions from analytical approximation formula (18) for negatively and positively correlated GB
  - Accurately separates survival regions: mutual extinction region I, where only virus 1 survives; mutual extinction region II, where only virus 2 survives; coexistence region III.


## IV. DISCUSSION AND CONCLUSION

**Competitive Multi-Virus Propagation:**
* Rich behaviors beyond single virus propagation
* Suitable for co-propagation of exclusive entities: opinions, diseases, marketing products
* Challenging problem with numerous unknowns
* Focus on long-term behaviors and multilayer network topology

**Contributions:**
1. Identification and quantification of extinction, coexistence, and mutual exclusion via defining survival thresholds and winning thresholds
2. Proving a region of coexistence and quantitating it through overlapping layers central nodes
3. Developing an explicit approximation formula to globally find threshold values
4. Proposing a novel multilayer network generation scheme to capture influence of layers interrelation

**Findings:**
* Extinction: condition where one entity is driven out of the population
* Coexistence: both entities exist in the population over time
* Mutual exclusion: neither entity can coexist with the other

**Methodology:**
* Focus on simple extension of SIS model to competitive spreading over two-layer network
* Believed to have great potentials for application to broader classes of multi-pathogen spreading over multi-layer and interconnected networks

**Acknowledgement:**
* Work partially supported by National Science Foundation under Award DMS-1201427.


## Appendix: Selected Proofs

**Derivation of Eigenvalue Perturbation Formulae**
- **Equation (7)**: Steady state equation for infection probabilities in NIMFA model
- **Equations (A.1) and (A.2)**: Differentiating with respect to effective infection rate τ2, yielding expressions for dw/dτ2 in terms of A and B matrices
- **Equation (A.5)**: Collective form of the equations, where Hadamard product ◦ acts entry-wise
- **Equation (A.6)**: Obtaining equation (10) by multiplying both sides of equation (A.5) by vA from left

**Coexistence Proofs**
- **Coexistent region for non-aggressive viruses (equation 14)**: Proven using Holder's inequality and the properties of Kronecker product
- **Coexistent region for aggressive competitive viruses (equation 12)**: Derived from equation (A.13)

**Lemma 1**: If H = π(DC)−1C, where π(DC) is a diagonal permutation of degree diagonal matrix of symmetric matrix C, then λ1(H) ≥ 1. Equality holds only if π(DC) = Dc.

**Recursive Law (A.15) and (A.16), (A.17)**: Numerically solving equations to find equilibrium values xi, yi, zi for infection probabilities p∗, 1 and 2


---

Thank you to arXiv for use of its open access interoperability.