# Meme as Building Block for Evolutionary Optimization of Problem Instances

[Meme as Building Block for Evolutionary Optimization of Problem Instances](https://arxiv.org/abs/1207.0702)

## Table of Contents
- [1 Introduction](#1-introduction)
- [2 Related Works](#2-related-works)
- [3 Memetic Evolution](#3-memetic-evolution)
	- [3.1 Cultural Operators](#31-cultural-operators)
	- [3.2 'Intelligent' Evolutionary Optimization via Memetic Evolution](#32-intelligent-evolutionary-optimization-via-memetic-evolution)
- [4 Case Studies on Routing Problems](#4-case-studies-on-routing-problems)
	- [4.1 Capacitated Vehicle Routing Problem](#41-capacitated-vehicle-routing-problem)
	- [4.2 Capacitated Arc Routing Problem](#42-capacitated-arc-routing-problem)
	- [4.3 Present State-of-the-art Evolutionary Optimization Methodologies](#43-present-state-of-the-art-evolutionary-optimization-methodologies)
- [5 Memetic Computational Paradigm for 'Intelligent' Evolutionary Optimization of Routing Problems](#5-memetic-computational-paradigm-for-intelligent-evolutionary-optimization-of-routing-problems)
	- [5.1 Meme Learning Operator in Routing Problem](#51-meme-learning-operator-in-routing-problem)
	- [5.2 Meme Selection Operator in Routing Problem](#52-meme-selection-operator-in-routing-problem)
	- [5.3 Meme Variation Operator in Routing Problem](#53-meme-variation-operator-in-routing-problem)
	- [5.4 Meme Imitation Operator in Routing Problem](#54-meme-imitation-operator-in-routing-problem)
- [6 Experimental Study](#6-experimental-study)
	- [6.1 Capacitated Vehicle Routing Problem](#61-capacitated-vehicle-routing-problem)
		- [6.1.2 Result and Discussion](#612-result-and-discussion)
	- [6.2 Capacitated Arc Routing Problem](#62-capacitated-arc-routing-problem)
		- [6.2.1 Empirical Conﬁguration](#621-empirical-conﬁguration)
		- [6.2.2 Result and Discussion](#622-result-and-discussion)
- [7 Conclusion](#7-conclusion)

## 1 Introduction

**Meme-Based Evolutionary Optimization: Building Blocks for Intelligent Problem Solving**

**Background:**
- Significant gap in literature on evolutionary optimization approaches that learn and transfer knowledge across problems
- Most approaches start from scratch, independent of past problem solutions
- Lack of automated knowledge transfers and reuse

**Motivation:**
- Inspired by human problem solving and cultural evolution
- Memes as building blocks of culture evolution
- Memetic Computational Paradigm for search introduced to enhance future evolutionary optimizations

**Key Concepts:**
1. **Meme**: Instructions for carrying out behavior in humans, replicable and transmissible
2. Memetic selection: Survival of the fittest among competitive ideas
3. Memetic learning: Adaptive improvement procedure or local search operator to enhance problem solving
4. Memetic variation: Introducing innovations into memes
5. Memetic imitation: Process of memes assimilation into new problem solutions

**Proposed Methodology:**
- Models human problem solving using memes as building blocks
- Transfer structured knowledge from past experiences to future problems
- Four culture-inspired operators: Meme Learning, Selection, Variation, and Imitation

**Application:**
- Demonstrated effectiveness on combinatorial optimization problems (vehicle routing, arc routing)
- Enhances existing state-of-the-art optimization methodologies in the domains of CVRP and CARP.

**Structure of the Paper:**
1. Introduction to traditional evolutionary optimization and related works
2. Proposed Memetic Computational Search Paradigm for intelligent problem solving
3. Mathematical formulations of Capacitated Vehicle Routing Problem (CVRP) and Capacitated Arc Routing Problem (CARP)
4. Designs of Meme Learning, Selection, Variation, and Imitation operators for routing problems
5. Experimental results on well-established CVRP and CARP benchmarks
6. Conclusive remarks.


## 2 Related Works

**Evolutionary Algorithms (EAs)**
- Inspired by principles of natural selection and survival of the fittest in biological kingdom
- Effective optimizations achieved through **inductive biases** that fit well with problem structure [5]
- Many specialized EAs developed with manual incorporation of human expert domain knowledge (inductive biases)

**Limitations of Existing Evolutionary Computation:**
- Lack of automated useful knowledge transfers and reuse from past problem solving experiences as appropriate biases to enhance evolutionary search on new problems
- Problems seldom exist in isolation, and previously encountered problems yield useful information for more effective future evolutionary search [33, 17]

**Reusing Useful Traits from Across Problems:**
- Few works have attempted to reuse established high-quality solutions or partial solutions from previous problems to aid evolutionary search via **case-based reasoning**[33]
- Appropriate intermediate solutions drawn from similar problems that have been previously solved are periodically injected into the GA population
- Reusing established high-quality schedules from past problems to bias search on new traveling salesman problems (TSPs)[17]

**Memetic Computational Search Paradigm:**
- Addresses the non-trivial task of learning the generic **building blocks or memes of useful traits** from past problem solving experiences
- Drawing upon them through the cultural evolutionary mechanisms of **meme learning, selection, variation, and imitation**, rather than simple direct copying of past solutions
- Transfer of memes as generic building blocks of useful knowledge can lead to enhanced search on problems of differing dimensions, topological structures, and representations


## 3 Memetic Evolution

**Memetic Computation in "Intelligent" Evolutionary Optimization:**

1. Memetic Computational Paradigm:
   - Based on human problem-solving methods.
   - Capable of adapting to changing problems.
2. Problem-solving behaviors modeled as memes.
3. Meme storage in "brains" (representation).
4. Memes represent past experiences, passed on for future problem solving.
5. Cultural evolution transfers memes between instances.
6. Enhances search through drawing on intelligence from previous problem-solving sessions.


### 3.1 Cultural Operators

**Cultural Operators for Memetic Computational Paradigm**

**Meme Learning Operator**:
- Takes the role of modeling and generalizing the mapping from problem instance p to optimized solution s*
- Learns from past problem instances and solutions, building up a wealth of knowledge in the form of memes
- Contrasts with simple storage or exact memory of specific problem instances and their solutions

**Meme Selection Operator**:
- Serves to identify or select the most successful memes from the "society of memes" for replication
- Different prior knowledge introduces unique biases into the search, making it more efficient for certain classes of problems
- Inappropriately harnessed knowledge may lead to impairments in the search

**Meme Variation Operator**:
- Forms the intrinsic innovation tendency of cultural evolution
- Without variation, maladaptive forms of bias may be introduced in evolutionary searches for new problem instances
- Variation is essential for retaining diversity in the "society of memes" to enable effective and efficient evolutionary search

**Meme Imitation Operator**:
- Memes are copied from person to person via imitation, as described in "The Selfish Gene" by Dawkins
- Memes learned from past problem solving experiences are replicated through imitation and used to enhance future evolutionary search


### 3.2 'Intelligent' Evolutionary Optimization via Memetic Evolution

**Meme Representation of Human Problem Solving in Memetic Computation**

**Identification of Meme Representation**:
- Schemata representation of memes as structured knowledge or latent patterns encoded in the "mystical mind of nature" is identified.
- Human problem solving experiences are captured via **meme learning** and crystallized into the **memepool**, which forms the building blocks of the "society of mind".

**Meme Selection and Variation**:
- When a new problem arises, the **meme selection operator** identifies appropriate memes from the memepool to enhance the evolutionary solver.
- These memes undergo variation to generate innovative memes that improve problem solving effectiveness and efficiency.

**Initial Problem Solving**:
- At time step i=1, the optimization solver OS is faced with the first problem instance p1.
- Since no relevant memes are available, the search proceeds normally, and the **meme selection operator** remains dormant.
- The optimized solution s1∗ obtained by OS on p1 is denoted by (p1, s1∗).
- Through **meme learning**, a new meme M1 is learned from the problem instance and corresponding optimized solution.

**Subsequent Problem Solving**:
- On subsequent unseen problem instances j=2,...,∞, the **meme selection operator** identifies appropriate memes Ms from the memepool SoM.
- Activated memes Ms then undergo variation to generate innovative meme Mt that instructs and guides the intelligent solver in the search process.
- The accumulated memes play the role of positively biasing the search on new problems, evolving the intellectual capability of the evolutionary solver with time.


## 4 Case Studies on Routing Problems

**Memetic Computational Paradigm for "Intelligent" Evolutionary Optimization:**
* **Scenario**: Class of combinatorial optimization problems
	+ Agents and tasks
	+ Costs and profits vary with agent-task assignments
	+ Agents have budgets, total costs cannot exceed it
	+ Maximize total profit while ensuring agents don't exceed their budgets
* **Practical Applications**:
	+ Complex real-world problems like: vehicle routing in urban waste collection or post delivery, plant location, resource scheduling, flexible manufacturing systems, generalized assignment problem (GAP), job scheduling problem (JSP), arc routing problem (ARP), etc.
* **Demonstration**: Memetic Computational Search Paradigm for "Intelligent" Evolutionary Optimization applied to:
	+ Capacitated Vehicle Routing Problem (CVRP)
	+ Capacitated Arc Routing Problem (CARP)

**Capacitated Vehicle Routing Problem (CVRP) and Capacitated Arc Routing Problem (CARP):**
* Widely studied challenging domains in optimization
* Demonstrated using the memetic computational search paradigm for "intelligent" evolutionary optimization.


### 4.1 Capacitated Vehicle Routing Problem

**Capacitated Vehicle Routing Problem (CVRP)**

**Background:**
- Introduced by Dantzig and Ramser [18]
- Design a set of vehicle routes for uniform capacity vehicles to service known customer demands from a common depot at minimum cost.

**Definitions:**
- **Connected undirected graph G=(V,E)**: vertex set V={vi}, i=1...n and edge set E={eij}, i,j=1...n.
  - vi: customer or depot (depot is vd)
  - eij: arc between vertices vi and vj with non-negative weight cij representing travel distance
- Demand set D={d(vi)} for each vi in V where d(vi)>0 implies a task.
- CVRP consists of designing a set of least cost routes R={Ci}, i=1...k such that:
  1. Each route Ci starts and ends at the depot node vd.
  2. Total load of each route is no more than the capacity W of each vehicle.
  3. For all vi in V with d(vi)>0, there exists exactly one route Ci in R that includes vi.
- Objective: Minimize the total distance cost (R) traveled by all vehicles defined as:
  - **k/summation** display i=1 of c(Ci)
  - where c(Ci) is the sum of travel distances in route Ci.


### 4.2 Capacitated Arc Routing Problem

**The Capacitated Arc Routing Problem (CARP)**

**Background**:
- Proposed by Golden and Wong [24] in 1981
- Connected undirected graph G=(V,E) with vertex set V and edge set E

**Constraints**:
1. Each travel circuit Ci must start and end at the depot node vd∈V
2. Total load of each travel circuit cannot exceed the capacity W of each vehicle: ∀ei∈C, d(ei) ≤ W
3. For every edge ei with demand d(ei)>0, there is exactly one circuit Ci∈R that includes it

**Solution Representation**:
- Set of travel circuits R={Ci}, i=1...k

**Cost Calculation**:
- Cost of a travel circuit C: sum of servicing costs on required edges + total travel cost of remaining edges: (2)
  - Service cost vector Cs = {cs(ei)| ei∈E}
  - Travel cost vector Ct = {ct(ei)| ei∈E}
- Objective is to find a valid solution R that minimizes the total cost (3)


### 4.3 Present State-of-the-art Evolutionary Optimization Methodologies

**CVRP and CARP: Solving Methods and Metaheuristics**

**Theoretical Complexity**:
- CVRP and CARP are NP-hard, with explicit enumeration approaches being the only known optimal solutions
- Large-scale problems are computationally intractable due to poor scalability of most enumeration methods

**Solving Approaches**:
- Metaheuristics, heuristics, and evolutionary computation have played important roles in solving CVRP and CARP within reasonable time constraints

**CVRP: Unified Tabu Search Algorithm (UTSA)**:
- Cordeau et al. [16] considered UTSA for solving VRP

**CVRP: Evolutionary Algorithm with Local Search**:
- Prins [41] presented an effective evolutionary algorithm with local search for the CVRP

**CVRP: D-ants Algorithm**:
- Reimann et al. [42] proposed a D-ants algorithm for CVP, which equipped ant colony algorithm with individual learning procedure

**CVRP: Hybrid Metaheuristic Algorithm**:
- Lin et al. [32] took advantage of both simulated annealing and tabu search, and proposed a hybrid meta-heuristic algorithm for solving CVRP

**CVP: Cooperative Memetic Algorithm**:
- Chen et al. [11] proposed a domain-specific cooperative memetic algorithm for solving CVRP, achieving better or competitive results compared to other state-of-the-art memetic algorithms and metaheuristics

**CARP: Memetic Algorithms (MAs)**:
- Lacomme et al. [30] presented the basic components embedded in MAs for solving the extended version of CARP (ECARP)
- LMA outperformed all known heuristics on three benchmark sets
- Mei et al. [35] introduced two new local search methods, improving the solution qualities of LMA
- A memetic algorithm with extended neighborhood search was proposed for CARP [45]
- Liang et al. proposed a formal probabilistic memetic algorithm for solving CARP [23]

**Solving Approach Generalization**:
- Searching for suitable task assignments (vertices or arcs requiring service) and finding the optimal service order of each vehicle

**Evolutionary Search Literature**:
- Task assignment stage realized by simple randomization to more advanced strategies like heuristic search, clustering, etc.
- Optimal service order achieved via evolutionary search operators

**Optimized CVRP/CARP Solutions Example**:
- Figure 2 illustrates an example of optimized CARP and CVP solutions


## 5 Memetic Computational Paradigm for 'Intelligent' Evolutionary Optimization of Routing Problems

**Meme Computational Paradigm for Intelligent Evolutionary Optimization of Routing Problems**

**Meme Selection:**
- Mechanism that selects fit memes (Ms) from the Society of Memes (SoM) to activate, if SoM is not empty
- Activated memes undergo variation to arrive at Mt

**Meme Variation:**
- Inspired by human's ability to generalize from past knowledge
- Operates on activated memories (Ms) to create a generalized version (Mt)

**Meme Imitation:**
- Positively biases search of evolutionary optimization solver OS
- Induced solutions enhance performance on new problem instances Xj\nnew
- Obtained by clustering and pairwise distance sorting (PDS) for tasks assignment and service orders, respectively

**Meme Learning:**
- Updates SoM memepool with newly learned meme Mj\nnew from optimized solutions Xj\nnew, Yj\nnew obtained by OS

**Pseudo Code and Workflow:**
1. For each new problem instance pj\nnew:
    - If SoM is not empty, perform meme selection to identify fit memes Ms
    - Perform meme variation on selected memes to generalize Mt
    - Initialize initial population Ω with cloned population and meme imitation
    - Repeat until stopping criteria met:
        * Evolutionary solver OS search
        * Memetic optimization with Xj\nnew, Mt
        * Insert optimized solutions (Xj\nnew, Yj\nnew) into Ω
2. If SoM is empty, proceed with original population initialization scheme of OS
3. Perform meme learning on pj\nnew and corresponding optimized solutions to derive new meme Mj\nnew
4. Archive the learned meme in SoM for subsequent reuse


### 5.1 Meme Learning Operator in Routing Problem

**Meme Learning: Transforming Task Distributions for Optimized Solutions**

**Background:**
- Meme M transforms original task distributions to desired ones, preserving service orders
- Figures 2 and 4 illustrate example problem instance and optimized solution
- Desired transformation: rearrange tasks closer to each other for common vehicles, further apart for different ones
- Distance metric: M(vi, vj) = ||vi - vj||M

**Meme Decomposition:**
- Positive semidefinite matrix
- Singular value decomposition (SVD): M = LLT
- Scales distances among tasks

**Learning Task:**
- Maximize dependency between X and Y using Hilbert-Schmidt Independence Criterion (HSIC)
- Equation 5: max Ktr(HKHY)
- X, Y represent problem instance and solution, respectively
- Idenitity matrix (I), trace operation (tr())

**Constraints:**
- Distance constraints: Dij > Diq for all (i, j, q) in N
- Reformulated as ast(KTij) > tr(KTiq)
- Introduce slack variables ξijq to measure violations and penalize square loss
- Equation 6: min M, ξ − tr(XHYHXT) + C

**Optimization Problem:**
- Derive minimax optimization problem using Lagrangian theory (Equation 7)
- Set∂Lr∂ξij = 0, resulting in αijq = 0 and ξijq = 1
- Reformulate learning problem as Equation 9: max α min Mtr[(−XHYHXT − summation display αijqXTijXT + summation display αijqXTiqXT)M]−12Cα2ijq

**Notes:**
- Meme learning transforms original task distributions to desired ones based on optimized solutions
- Desired transformations: tasks serviced by same vehicle closer together, tasks serviced by different vehicles further apart
- Distance metric is scaled by meme M
- To learn meme M from a problem instance p = X and optimized solution s∗ = Y with distance constraints N:
  1. Maximize dependency between X and Y using Hilbert-Schmidt Independence Criterion (HSIC) in Equation 5
  2. Introduce slack variables ξijq to measure violations of distance constraints and penalize the corresponding square loss
  3. Solve the minimax optimization problem given by Equation 9.


### 5.2 Meme Selection Operator in Routing Problem

**Meme Selection Operator**
- **Purpose**: Select fit memes that share common characteristics with a new problem to enhance evolutionary search
- **Process**:
  1. Identify weight (µ) of each meme based on:
     - **Hilbert Schmidt Independence Criterion (HSIC)** and **Maximum Mean Discrepancy (MMD)** criteria
  2. Determine coefficient vector µ using Equation (11):
     - Maximize statistical dependence between input X and output label Y for clustering
     - Measure similarity between previous problem instances solved to the given new problem
- **Unknown Variables**: 
   - Memes (µ)
   - Label matrix Y (obtained from task assignment results)
- **Solution**:
  1. Perform clustering on input X directly to obtain label matrix Y
  2. Fix Y and maximize Equation (11) via quadric programming solver to obtain µ
  3. Maintain chosen meme (M) fixed and perform clustering on new X' (transformed by selected M) to obtain label matrix Y


### 5.3 Meme Variation Operator in Routing Problem

**Meme Variation: Generalization in Memetic Algorithms**

    1. Introduce innovations during reuse: Meme variation operator.
    2. Inspired by human generalization from past problem-solving experience.
    3. Form of meme variation: Meme generalization as linear combination of selected memes.
    4. Generalized meme `Mt`: $$ M_t = \sum_{i=1}^{n} \frac{\mu_i}{|\mu|} M_i $$ (where $\mu$ is the set of weights and $|\mu|$ is its size).


### 5.4 Meme Imitation Operator in Routing Problem

**Routing Problems: Two Phases for Optimal Solution**
- Phase 1: Assignment of tasks requiring services to appropriate vehicles
- Phase 2: Determination of optimal service order for each vehicle's assigned tasks

**Meme Induced Solutions**
- Descripton of meme imitation solutions as initial population for intelligent biasing the optimization search
- Transformation of original task distribution X into a meme-induced tasks distribution X′ using singular value decomposition on Mt (Line 10 in Algorithm 1)
- Illustrative example: Figure 6 shows the original and meme-induced tasks distributions

**Phase 1: K-Means Clustering on Meme Induced Tasks Distribution**
- Simple clustering scheme such as K-Means with random initializations used to obtain vehicle assignments from the meme-induced tasks distribution X′
- Derivation of tasks assignments for individual vehicles, denoted by dashed circles in Figure 6(c)

**Phase 2: Obtaining Service Orders via Pairwise Distance Sorting (PDS)**
- Determination of service orders for each vehicle by sorting pairwise distances among tasks in ascending order
- First and last tasks to be serviced are those with the largest distance, with remaining tasks defined by their sorted positions relative to the reference task


## 6 Experimental Study

**Memetic Evolutionary Search Paradigm: Evaluation on Capacitated Vehicle Routing Problems (CVRPs) and Capacitated Arc Routing Problems (CARPs)**
* Two empirical studies presented to evaluate memetic evolutionary search paradigm effectiveness
* Considering CAMA [9] and ILMA [35] as baselines for CVRPs and CARPs, respectively
* Performance measurement criteria:
  + **Number of Fitness Evaluation**: measures algorithm efficiency
  + **CpuTime**: measures algorithm efficiency
  + **Ave.Cost**, **B.Cost**: criteria for solution qualities
  + **Success No.**: criterion for solution qualities


### 6.1 Capacitated Vehicle Routing Problem

**CVRP Benchmark Datasets**
- Three commonly used datasets: "AUGERAT" [1], "CE" [12], and "CHRISTOFIDES" [13]
- Detailed properties summarized in Table 2 and Table 3
    - Number of vertices (V), capacity (Cv), lower bound (LB)

**Data Analysis for CAMA, CAMA-R, and CAMA-M on "AUGERAT"**
- Results presented in Table 4
- Comparison of performance metrics: B.Cost, Average Cost, Standard Deviation, Success Rate

**Data Analysis for CAMA, CAMA-R, and CAMA-M on "CE" CVRP Benchmarks**
- Results presented in Table 5
- Comparison of performance metrics: B.Cost, Average Cost, Standard Deviation, Success Rate

**Data Analysis for CAMA, CAMA-R, and CAMA-M on "CHRISTOFIDES" CVRP Benchmarks**
- Results presented in Table 6
- Comparison of performance metrics: B.Cost, Average Cost, Standard Deviation, Success Rate

**Figures Demonstrating Convergence Graphs for CAMA, CAMA-R, and CAMA-M on Representative CVRP Benchmarks**
- Figure 7: "AUGERAT" benchmarks
- Y-axis: Fitness value, X-axis: Number of Fitness Evaluation or CPU Time in Seconds.
- Figure 8: "CE" benchmarks
- Y-axis: Fitness value, X-axis: Number of Fitness Evaluation or CPU Time in Seconds.

**Initialization Procedures for CAMA-R, CAMA, and CAMA-M**
- Three initialization procedures: random approach (CAMA-R), informed heuristic approach (baseline CAMA), meme induced population initialization (CAMA-M)
- CAMA-M uses the MME of Equation 10 augmented with demand for each task as a feature.


#### 6.1.2 Result and Discussion

**Results and Discussion**

**CAMA-R vs CAMA**:
- CAMA-R achieved improved solution quality over CAMA on most "AUGERAT" and "CE" CVRP instances:
  - Consistently converged to the best solution fitness on instance "A-n54-k7"
  - Attained an improved B.Cost solution over CAMA on instance "B-n63-k10"
- However, CAMA outperformed CAMA-R on "CHRISTOFIDES" benchmarks:
  - Superior performances in terms of Ave.Cost and Success No. on instances "c199" and "c120", "c150"
  - Possible due to the appropriate biases introduced in CAMA's population initialization phase

**CAMA-M**:
- Initially behaves like the baseline CAMA, as it learns no memes on the first CVRP instance
- As more CVRP instances are encountered, CAMA-M learns and generalizes memes to induce positive bias in the evolutionary search of new problems
- CAMA-M converges to similar solutions to CAMA-R and CAMA on the first problem instance, but demonstrates superior performance on subsequent CVRP instances:
  - "AUGERAT" and "CE" benchmarks: 13 out of 19 CVRP instances with improved Ave.Cost and Success No.
  - "CHRISTOFIDES" benchmarks: 4 out of 7 CVRP instances with improved Ave.Cost and Success No.
- CAMA-M converges faster than both CAMA-R and CAMA on most CVRP instances, saving up to thousands of fitness evaluations

**Conclusion**:
- The proposed memetic search paradigm in CAMA-M allows for intelligent generation of initial solutions using the positive biases induced by learned memes from past problem solving experiences
- This leads to superior performance and faster convergence compared to both CAMA-R and CAMA on most CVRP instances.


### 6.2 Capacitated Arc Routing Problem

**Memetic Evolutionary Search for Capacitated Arc Routing Problem:**

1. Evaluate efficiency and effectiveness of the proposed method on the Capacitated Arc Routing Problem domain.


#### 6.2.1 Empirical Conﬁguration

**Car Path Planning Benchmark (CARP)**
* Dataset: Egles' benchmark for CARP
* Originated from data obtained from Winintergritting application in Lancashire [21, 22, 31]
* Commonly used as benchmark dataset in literature for CARP solving [23, 35]
* Consists of two series: "E" and "S" with a total of 24 instances

**Properties of the "E" Series CARP Benchmarks:**
| Dataset | V (number of vertices) | Er (number of edges) | E (total number of tasks) | LB (lower bound) |
|---|---|---|---|---|
| E1A, B, C | 77 | 51, 72, 87 | 3 (3 instances with different task distributions) | 3548, 4498, 5566 |
| E2A, B, C | 77 | 98, 98, 98 | 3 (3 instances with different task distributions) | 5018, 6305, 8243 |
| E3A, B, C | 77 | 87, 87, 87 | 3 (3 instances with different task distributions) | 5898, 7704, 10163 |
| E4A, B, C | 77 | 98, 98, 98 | 3 (3 instances with different task distributions) | 6048, 8884, 11427 |

**Properties of the "S" Series CARP Benchmarks:**
| Dataset | V (number of vertices) | Er (number of edges) | E (total number of tasks) | LB (lower bound) |
|---|---|---|---|---|
| S1A, B, C | 140 | 75, 147, 159 | 3 (3 instances with different task distributions) | 5018, 6384, 9824 |
| S2A, B, C | 140 | 190, 190, 190 | 3 (3 instances with different task distributions) | 12968, 16353, 10143 |
| S3A, B, C | 140 | 8493, 7704, 17100 | 3 (3 instances with different task distributions) | 5898, 7716, 13616 |
| S4A, B, C | 140 | 9824, 8884, 20375 | 3 (3 instances with different task distributions) | 12143, 16093, 20375 |

**ILMA, ILMA-R, and ILMA-M on "E" Series CARP Benchmarks:**
| Dataset | Fitness Value (B.Cost) | Number of Success No. | Average Cost Std.Dev |
|---|---|---|---|
| E1A | 3548, 3548, 3548 | 30 | 3548, 3548, 3548 |
| E1B | 4498, 4517, 4498 | 12 | 4517.63, 9 (.8), 4498.19 |
| E1C | 5595, 5601, 5595 | 7 | 5601.33, 3 (.61), 5595.07 |
| E2A | 5018, 5018, 5018 | 30 | 5018, 5018, 5018 |
| E2B | 6317, 6341, 6344 | 14 | 6317.53, 16 (.15), 6341.9 |
| E2C | 8335, 8359, 8355 | 10 | 8335.87, 6 (.57), 8355.07 |
| E3A | 5898, 5921, 5916 | 30 | 5921.23, 25 (.57), 5898.07 |
| E3B | 7777, 7794, 7792 | 23 | 7794.77, 76 (.95), 7775.33 |
| E3C | 10292, 10318.73, 10342 | 20 | 10342.47 (1.57), 16 (.98), 10269.16 |
| E4A | 6461, 6481.77, 6471 | 15 | 6471.37, 21 (.16), 6461.8 |
| E4B | 8995, 9060.93, 9067 | 41 | 9067.93, 15 (.54), 8988.97 |
| E4C | 11555, 11678.47, 11728 | 20 | 11728.16 (1.35), 10 (.39), 11576.27 |

**ILMA, ILMA-R, and ILMA-M on "S" Series CARP Benchmarks:**
| Dataset | Fitness Value (B.Cost) | Number of Success No. | Average Cost Std.Dev |
|---|---|---|---|
| S1A | 5018, 5023, 5025 | 18 | 5023.67, 27 (.39), 5023 |
| S1B | 6388, 6403, 6392 | 20 | 6392.03, 22 (.38), 6388.93 |
| S1C | 8518, 8581, 8576 | 33 | 8576.33, 11 (.46), 8518.15 |
| S2A | 9920, 10037, 10050 | 54 | 10050.3, 20 (.51), 9896.2 |
| S2B | 13173, 13257, 13245 | 53 | 13245.56, 22 (.94), 13147.97 |
| S2C | 16507, 16605.1, 16626 | 82 | 16626.43, 10 (.9), 16468.16 |
| S3A | 10248, 10342, 10369 | 53 | 10369.4, 18 (.33), 10239.4 |
| S3B | 13764, 13912, 13899 | 76 | 13899.7, 21 (.33), 13749.33 |
| S3C | 17274, 17371, 17355 | 85 | 17355.03, 14 (.48), 17261.27 |
| S4A | 12320, 12489, 12498 | 83 | 12498.43, 19 (.91), 12320.43 |
| S4B | 16378, 16540.93, 16542 | 57 | 16542.13, 20 (.54), 16415.43 |
| S4C | 20564, 20774, 20841 | 86 | 20841.53, 5 (.53), 20589.2 |


#### 6.2.2 Result and Discussion

**Results and Discussion on Solution Quality**
* Tabulated results for "E"-Series and "S"-Series eglCARP datasets: Table 9, 10
* ILMA-R vs ILMA-M performance comparison

**ILMA-R vs ILMA-M Performance (Competitive)**
- On instances "E1-A", "E1-B", "E2-A", "S1-A", "S1-B" and "S2-A": ILMA-R has comparable solution quality with ILMA-M

**ILMA-M vs ILMA (Superior Performance)**
- On 18 out of total 24 eglbenchmarks: ILMA-M demonstrates superior performance over ILMA in terms of Ave.Cost
- On "E" and "S" series eglbenchmarks: ILMA-M achieved 2 and 8 improved solution qualities over ILMA and ILMA-R, respectively

**ILMA vs ILMA-R (Improved Performance)**
- On large scale instances (instances with greater service arcs, travel edges, or number of vertices): ILMA attains improved performance over ILMA-R in terms of solution quality

**ILMA, ILMA-R, and ILMA-M Convergence Speed**
* Depicted convergence traces on several representative instances: Fig. 11 (E & S series)
* ILMA and ILMA-R demonstrate competitive convergence speed on simpler problems
* As problem complexity increases, ILMA consistently converges faster than ILMA-R with improved solution quality
* ILMA-M consistently converges more efficiently than ILMA and ILMA-R on most instances presented

**Efficiency of Proposed Memetic Evolutionary Search Paradigm**
* ILMA-M brings about significant savings in the number of fitness function evaluations (up to 2×10^6) compared to ILMA and ILMA-R on most eglbenchmarks. For instance:
  - On instance "S1-B", ILMA-M used total 1.5×10^6 number of fitness function evaluations to converge at the solution incurred by ILMA and ILMA-R, which otherwise used a significant large number (approx. 6×10^6). This equates to a total savings of 4 times by ILMA-M over ILMA and ILMA-R.


## 7 Conclusion

**Memetic Computational Paradigm for Intelligent Evolutionary Optimization**

**Proposed Memetic Search Algorithm:**
- Enhances future evolutionary searches through transfer of structured knowledge in the form of memes learned from previous problem solving experiences
- Four culture-inspired operators: Meme Learning, Meme Selection, Meme Variation, and Meme Imitation
- Realized based on HSIC, MMD criterion and K-means Clustering for combinatorial routing problems

**Benchmark Studies:**
- Conducted on CVRP and CARP (Capacitated Vehicle Routing Problem and Capacitated Arc Routing Problem)
- Demonstrated efficiency and effectiveness of the proposed paradigm

**Key References:**
- P. Augerat et al., Computational results with a branch-and-cut code for the capacitated vehicle routing problem (1995)
- S. Blackmore, The mememe machine (1999)
- I. Borg and P. J. F. Groenen, Modern Multidimensional Scaling: Theory and Applications (2005)
- K. M. Borgwardt et al., Integrating structured biological data using kernel maximum mean discrepancy (2006)
- P. Bosman and E. de Jong, Adaptation of a success story in gas: Estimation-of-distribution algorithms for tree-based optimization problems (2008)
- J. D. Bransford et al., How People Learn: Brain, Mind, Experience, and School (2000)
- R. Brodie, Virus of the mind: The new science of the meme (1996)
- J. P. Byrnes, Cognitive development and learning in instructional contexts (1996)
- X. Chen and Y. S. Ong, A conceptual modeling of meme complexes in stochastic search (2012)
- X. S. Chen et al., A multi-faced survey on memetic computation (2011)
- X. S. Chen, Y. S. Ong, M. H. Lim, and S. P. Yeo, Cooperating memes for vehicle routing problems (2011)
- N. Christofides and S. Eilon, An algorithm for the vehicle dispatching problem (1969)
- N. Christofides et al., The vehicle routing problem (1979)
- N. Christofides et al., Exact algorithm for the vehicle routing problem based on spanning tree and shortest path relaxations (1981)
- P. C. Chu and J. E. Beasley, A genetic algorithm for the generalized assignment problem (1997)
- J. F. Cordeau et al., A unified tabu search heuristic for vehicle routing problems with time windows (2001)
- P. Cunningham and B. Smyth, Case-based reasoning in scheduling: Reusing solution components (1997)
- G. Dantzig and J. H. Ramser, The truck dispatching problem (1959)
- E. W. Dijkstra, A note on two problems in connection with graphs (1959)
- R. W. Eglese, Routing winter gritting vehicles (1994)
- R. W. Eglese and L. Y. O. Li, A tabu search based heuristic for arc routing with a capacity constraint and time deadline (1996)
- L. Feng et al., Towards probabilistic memetic algorithm: An initial study on capacitated arc routing problem (2010)
- B. Golden and R. Wong, Capacitated arc routing problems (1981)
- B. L. Golden et al., Computational experiments with algorithms for a class of routing problems (1983)
- G. Grant, Memetic lexicon (1990)
- A. Gretton et al., Measuring statistical dependence with Hilbert-Schmidt norms (2005)
- M. T. Jensen, Generating robust and flexible job shop schedules using genetic algorithms (2003)
- J. D. Knowles and D. W. Corne, M-PAES: A memetic algorithm for multi-objective optimization (2000)
- C. Prins et al., Competitive memetic algorithms for arc routing problem (2004)
- L. Y. O. Li and R. W. Eglese, An interactive algorithm for vehicle routing for winter-gritting (1996)
- S. W. Lin et al., Applying hybrid metaheuristics for capacitated vehicle routing problem (2009)
- S. J. Louis and J. McDonnell, Learning with case-injected genetic algorithms (2004)
- A. Lynch, Thought contagion as abstract evolution (1991)
- Y. Mei et al., Improved memetic algorithm for capacitated arc routing problem (2009)
- M. Minsky, The society of mind (1986)
- Q. C. Nguyen, Y. S. Ong, and C. Y. Lee, A probabilistic memetic framework (2009)
- Y. S. Ong and A. J. Keane, Meta-Lamarckian learning in memetic algorithms (2004)
- Y. S. Ong, M. H. Lim, and X. S. Chen, Research frontier: Memetic computation - past, present & future (2010)
- S. J. Pan and Q. Yang, A survey on transfer learning (2010)
- C. Prins, A simple and effective evolutionary algorithm for the vehicle routing problem (2004)
- M. Reimann et al., D-ANTS: Savings based ants divide and conquer the vehicle routing problem (2004)
- M. A. Runco and S. Pritzker, Encyclopedia of Creativity (1999)
- L. Song et al., A dependence maximization view of clustering (2007)
- K. Tang, Y. Mei, and X. Yao, Memetic algorithm with extended neighborhood search for capacitated arc routing problems (2009)
- K. Tang, Y. Mei, and X. Yao, Memetic algorithm with extended neighborhood search for capacitated arc routing problems (2009)
- A. Barkat Ullah et al., A new approach for solving constrained real-valued optimization problems (2009)
- G. Ulusoy, The fleet size and mix problem for capacitated arc routing (1985)
- H. F. Wang, D. W. Wang, and S. X. Yang, A memetic algorithm with adaptive hill climbing strategy for dynamic optimization problems (2009)
- N. Yoshiike and Y. Takefuji, Vehicle routing problem using clustering algorithm by maximum neural networks (1999)
- J. Zhuang et al., A family of simple non-parametric kernel learning algorithms (2011)

