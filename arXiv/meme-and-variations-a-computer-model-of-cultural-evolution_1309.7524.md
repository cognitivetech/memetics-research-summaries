# Meme and Variations: A Computer Model of Cultural Evolution

[Meme and Variations: A Computer Model of Cultural Evolution](https://arxiv.org/abs/1309.7524)

## Table of Contents
- [Meme and Variations: A computer model of cultural evolution](#meme-and-variations-a-computer-model-of-cultural-evolution)
- [1. THE MODEL](#1-the-model)
- [2. PROTOCOL](#2-protocol)
- [3. RESULTS](#3-results)
- [4. COMPARISON WITH OTHER APPROACHES](#4-comparison-with-other-approaches)

## Meme and Variations: A computer model of cultural evolution

**Meme and Variations: A Computer Model of Cultural Evolution**

**Background:**
- Liane Gabora's model inspired by genetic algorithm in Holland's (1975) study
- Investigates effect of parameters on cultural evolution process
- Named after classical music form 'theme and variations', as ideas evolve from old ones

**Key Concepts:**
1. **Knowledge-based operators**: Brains detect regularity, generating novelty strategically based on past experience.
2. **Imitation**: Ideas spread when agents copy what others do, enabling them to share solutions to problems.
3. **Mental simulation**: Agents imagine how successful an idea would be before implementing it, providing rudimentary selection.

**Model Features:**
- Artificial society of neural network-based agents
- Acquire new ideas through innovation or imitation in each iteration
- Variation occurs through mutation of pre-existing ideas
- Selection occurs through choice of which pre-existing idea to mutate and how to mutate it
- Ideas spread through imitation.


## 1. THE MODEL

**The Cultural Algorithm Model**

**Features and Loci**:
- Features or components of an idea are referred to as loci
- Alternative forms of a locus are alleles
- Processes that generate variation are mutation operators
- Forward mutation is mutation away from the original (or "wild type") allele
- Backmutation is mutation from an alternative form back to the original

**The Domain**:
- Earliest culture took the form of physical actions, such as displays of aggression or submission
- Ideas in MAV can be thought of as **mating displays**
- An idea is a pattern consisting of six loci that dictate the degree of movement for six body parts:
  - Left arm, right arm, left leg, right leg, head, and tail
- Each locus has a floating point activation between -0.5 and 0.5
- Loci are treated as having only three possible alleles: **stationary**, up, and down
- This gives a total of 729 possible ideas

**The Neural Network**:
- The neural network is an autoassociator that learns the identity function between input and output patterns
- It has six input/output units numbered 1 through 6, corresponding to the six body parts
- It has six hidden units numbered 7 through 12, corresponding to general concepts like "arms", "legs", "left/right", "movement", and "symmetry"
- Hidden units are linked with positive weights to input/output units that represent positive instances of the concepts they represent, and negative weights to input/output units that represent negative instances
- Hidden units that represent opposite concepts have negative connections between them
- The hidden units enable the network to encode the semantic structure of an idea, and their activations are used to bias the generation of variation

**The Embodiment**:
- The embodiment is a six-digit array specifying the behavior of the six body parts
- An idea cannot be observed and imitated by other agents until it has been copied from the neural network to the embodiment and is implemented as an action

**The Fitness Function**:
- The optimal action is where all body parts except the head are moving, and limb movement is anti-symmetrical
- This fitness function corresponds to a relatively realistic display, but also has properties like:
  - **Overdominance**: The optimal value of the "head stability" locus lies midway between the two extremes
  - **Underdominance**: The optimal values of the "tail" locus lie at either extreme
  - **Epistasis**: The fitness at one locus depends on which allele is present at another locus
- This enables a comparative analysis of diversity under different ratios of creation to imitation

**Using Experience to Bias the Generation of Novelty**:
- Each locus starts with the allele for no movement, and has an equal probability of mutating to either of the other two alleles
- The difference between the currently-implemented action and the fitter action is used to bias the direction of mutation:
  - If the fitter action codes for more movement, increase the probability of forward mutation and decrease the probability of back mutation
  - If the fitter action codes for less movement, do the opposite
- The second rule biases the agent either toward or away from symmetrical limb movement


## 2. PROTOCOL

**Cultural Algorithm for Agents**

**Grid-World Environment**:
- Two-dimensional wrap-around 10x10 grid-cell world
- One agent per cell

**Iteration Process**:
- Acquire new idea for action:
  - Imitate a neighbor
  - Create anew (cultural algorithm applied)
- Update mutation operator
- Implement new action

**Action Creation**:
- Decide to mutate or not (probability specified globally)
- If decide to mutate, direction is stochastically determined
- New idea has higher fitness: learn and implement action

**Imitation**:
- Randomly choose neighbor
- Evaluate neighbor's action fitness
- Copy neighbor's action if own is less fit
- No mental simulation condition: new idea must be implemented for at least one iteration before its fitness can be assessed

**Mutation Operators**:
- Updated following iteration after no mental simulation condition


## 3. RESULTS

**Results of Cultural Evolution Experiments**

**Experiment Setup**:
- Mutation rate: 0.17 per locus
- Creation to imitation ratio: 1:1
- All cultural evolution strategies operative, unless otherwise indicated

**Outline of a Run: Culture Evolves**
- Initially, all agents were immobile (0 actions)
- First idea mutated, coded for movement of a body part (higher fitness)
- Society evolved toward increasingly fit actions through creation and imitation

**Trade-off Between Diversity and Global Optimization**
- Diversity peaked when first maximally fit idea was found, then decreased as society converged on optimal ideas
- Increasing creativity to imitation ratio increased diversity during evolution and stabilization
- Balance struck between diversifying creation and converging imitation effects

**Frequency of Change Must be Intermediate**
- Agents could vary in frequency of invention and amount of change introduced
- Best performance with 0.07 to 0.22 mutations per locus (high for few loci)
- Mutation ensures unfit ideas not implemented, fit actions imitated

**Epistasis Decreases Rate of Fitness Increase**
- Fitness increased more slowly and stabilization took longer for epistatically linked loci than over/underdominant loci
- Epistatic loci never stabilized due to more constraints on what one arm should do based on other arm

**Cultural Drift**
- Presence of drift: random changes in relative frequencies of equally-fit alleles (loci)
- Indicated by high/low mean activation values across society for overdominant and epistatic loci, respectively

**Effect of Knowledge-based Operators, Imitation, and Mental Simulation**
- Each strategy increased optimization rate and peak mean fitness when made inoperative one at a time
- Cumulative results showed all three strategies contributed to improvement

**Fittest Society with Creation to Imitation Ratio of 2:1**
- Highest mean fitness achieved with creation and imitation
- Optimal creativity to imitation ratio likely midway between 1:1 and 3:1 (approximately 2:1)
- Societies with different ratios had varying performance, convergence times


## 4. COMPARISON WITH OTHER APPROACHES

**Comparison of MAV Approach to Other Models**
- **Computational approach**: allows for analysis of cultural evolution patterns in a society of interacting individuals
- First computational model examining culture's impact on biological evolution

**Hutchins and Hazelhurst (1992) Study:**
- Explored relationship between environment, internal representation, and cultural artifacts
- Limited to vertical transmission of knowledge across generations

**MAV vs. Other Models**:
- MAV focuses on cultural evolution within one generation for disentanglement from biological evolution
- Sims (1991), Todd & Latham (1992): studied creativity and cooperation using genetic algorithm, modeling biological evolution
- Axelrod's work inspired more culturally realistic approaches but lacked exploration of cultural phenomena complexity

**MAV Limitations**:
- Fixed and small space for possible ideas
- Static fitness function
- Imitation and innovation less discrete in real life

**Implications of MAV**:
- Demonstrates feasibility of computationally modeling cultural diversity spread through society.

**Summary of MAV Model**:
- Minimal computer model of cultural evolution process
- Artificial society of neural network agents: no genomes, no death or offspring
- Innovate (mutate ideas) or imitate actions from neighbors
- Features observed in biology: drift, epistasis, diversity impact on fitness
- Addresses culture-specific phenomena: mental simulation, strategic variation generation.

**Observed Consequences**:
- Increasing innovation beyond minimum necessary compromises diversity and average fitness
- Optimal innovation-to-imitation ratio approximately 2:1 for society but diverse agents benefit from less imitation.

