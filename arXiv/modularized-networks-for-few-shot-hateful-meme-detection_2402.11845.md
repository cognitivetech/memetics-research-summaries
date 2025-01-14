# Modularized Networks for Few-shot Hateful Meme Detection

[Modularized Networks for Few-shot Hateful Meme Detection](https://arxiv.org/abs/2402.11845)

## Table of Contents

- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
	- [2.1 Hateful Meme Detection](#21-hateful-meme-detection)
	- [2.2 Parameter-efficient Tuning](#22-parameter-efficient-tuning)
- [3 Preliminary](#3-preliminary)
	- [3.1 Few-shot Hateful Meme Detection](#31-few-shot-hateful-meme-detection)
- [4 Methodology](#4-methodology)
	- [4.2 LoRA Module Learning](#42-lora-module-learning)
	- [4.4 Modularized Networks](#44-modularized-networks)
- [5 Experiments](#5-experiments)
	- [5.2 Baselines](#52-baselines)
	- [5.4 Ablation Study](#54-ablation-study)
	- [5.5 Qualitative Analysis](#55-qualitative-analysis)
- [6 Conclusion](#6-conclusion)
- [A Details of Implementation](#a-details-of-implementation)
- [B Error Cases](#b-error-cases)
- [C Templates for In-context Learning](#c-templates-for-in-context-learning)
- [E Limitations](#e-limitations)

## Abstract

**Modularized Networks for Few-shot Hateful Meme Detection**

**Authors:**
- Rui Cao (ruicao.2020@phdcs.smu.edu.sg)
- Roy Ka-Wei Lee (roy_lee@sutd.edu.sg)
- Jing Jiang (jingjiang@smu.edu.sg)

**Background:**
- Challenge of detecting hateful memes in low-resource setting with few labeled examples available
- Approach leverages compositionality of Low-rank adaptation (LoRA) for parameter-efficient tuning

**Methodology:**
1. Fine-tune large language models (LLMs) with LoRA on relevant tasks for hateful meme detection
2. Generate suite of LoRA modules capable of essential reasoning skills for hateful meme detection
3. Use few available annotated samples to train module composer, assigning weights based on relevance
4. Modularized network underpinned by LLMs and augmented with LoRA modules exhibits enhanced generalization in context of hateful meme detection
5. Evaluation on three datasets designed for hateful meme detection in few-shot learning context
6. Superior performance to traditional in-context learning, more computationally efficient during inference

**Keywords:** multimodal memes, hateful content, parameter-efficient tuning, few-shot learning

**ACM Reference Format:** Cao, R., Lee, R. K. W., & Jiang, J. (2024). Modularized Networks for Few-shot Hateful Meme Detection. In Proceedings of the ACM Web Conference 2024 (WWW ’24), May 13–17, 2024, Singapore, Singapore. ACM, New York, NY, USA. https://doi.org/10.1145/3589334.3648145

**Disclaimer:** This paper contains violence and discriminatory content that may be disturbing to some readers.


## 1 Introduction

**Online Social Platforms and Hateful Memes:**
* **Impact of online social platforms**: Enhanced information exchange and dissemination across communities
* **Memes**: Entertaining or provocative images with text overlays, can also be hateful and disruptive
* **Hateful memes**: Target individuals or groups based on race, gender, nationality; foster discord, amplified distribution
* **Challenges in addressing hateful memes**:
	+ Existing detection methods rely heavily on extensive supervised learning and large volumes of annotated data
	+ Acquiring and annotating sufficient training examples for novel occurrences is impractical
* **Few-shot hateful meme detection**: A niche area that has not been thoroughly explored in existing literature

**Hateful Meme Detection Methods:**
1. General multimodal classification using pre-trained vision-language models (PT-VLMs)
	* Fine-tune PT-VLMs for hateful meme detection
	* Directly integrating PT-VLMs within specialized architectures for hateful content detection
2. In-context learning potential of PT-VLMs: Harnessing the model's ability to learn from limited annotated examples
3. Large language models (LLMs) for multimodal hateful meme detection: Convert images to captions and feed them into LLMs
	* Low-rank adaptation (LoRA) modules for essential reasoning skills acquisition
	* Develop a suite of LoRA modules for core competencies in hateful meme detection: grasping the concept, decoding messages, elucidating rationales
4. Modular networks with composition of LoRA modules: Transfer learned skills from related tasks and compose them for hateful meme detection
5. Proposed method: Consistently outperforms established in-context learning baselines across all test datasets; more efficient during inference stage compared to traditional methods.


## 2 Related Work

### 2.1 Hateful Meme Detection

**Online Social Media and Memes:**
- Memes have become prevalent mode of communication in online social media
- Rising trend of use in disseminating hate
- Numerous datasets developed for detecting hateful memes [9,19,28,29]

**Challenges in Hateful Meme Detection:**
- Multimodal challenge: Understanding both text and image components of memes
- Current approaches use fine-tuned PT-VLMs [19,25,27,42]
  - Ensemble of PT-VLMs considered [25,27,36]
- Overlook distinctive aspects of the task
- Alternative strategies tailor architectures specifically for hateful meme detection [4,5,20,21,29]
  - Rely on extensive supervised learning
- Rapid annotation of memes is unfeasible and cost-prohibitive [19]

**Proposed Approach: Few-shot Hateful Meme Detection**
- Novel focus in underexplored domain
- LoRA module learning from relevant tasks for essential skills [not clear what "LoRA" stands for]
  - Obtain skills for hateful meme detection
- Module composer with few-shot training data learns importance scores over each LoRA module
- Construction of modularized networks by integrating learned LoRA modules with frozen LLMs

**Proposed Model Architecture:**
- Consists of three steps:
  1. LoRA module learning from relevant tasks
  2. Training a module composer with few-shot data
  3. Construction of modularized networks by integrating learned LoRA modules and frozen LLMs


### 2.2 Parameter-efficient Tuning

**Large Language Models (LLMs)**
- Widespread use due to impressive performance across various tasks [3,7,26,35,39]
- Efficiency challenges when applied to new tasks
  - Multi-billion parameter scale
  - Scarcity of supervised data
- Parameter-efficient tuning (PEFT) techniques introduced to circumvent inefficiencies:
  1. Adding and updating new parameters:
    - Prompt-tuning [40,41]
    - Adapters [15,31]
  2. Selectively updating a sparse set of parameters:
    - [11,32]
  3. Employing decomposition strategy with low-rank matrices:
    - LoRA [16]

**Challenges in Tuning with Few Labeled Instances**
- PEFT methods reduce the number of adjusted parameters but persist challenges in tuning with limited labeled instances

**Inspiration from LoraHub [17]**:
- Investigated composability and transferability of LoRA modules to unseen tasks

**Study Objective**:
- Seeks to harness power of LoRA for hateful meme detection using a few-shot learning framework
  - Train LoRA modules on related domain tasks with limited examples
  - Design module composer assigning importance scores to learned LoRA modules

**Approach**:
- Composes specialized modules for effective tackling of the hateful meme detection task within few-shot learning.


## 3 Preliminary

### 3.1 Few-shot Hateful Meme Detection

**Hateful Meme Detection**

**Meme Classification**:
- Decide if meme is hateful or non-hateful based on image and superimposed text
- Train model with labeled training data `Dtrain=(I,C,^e)` where `^e` is the ground-truth label
- Evaluate models on testing split `Dtest`
- Low-resource setting with limited labeled examples (assuming `𝐾` training examples per class)
- Goal: Optimize models to generalize well on testing data

**LoRA (Low-Rank Adaptation)**:
- Parameter-efficient tuning method [16] that decomposes attention weight updates into low-rank matrices
- Given `Wi ∈ R𝑝×𝑞` attention weight matrix and its accumulated gradient update `ΔWi`, LoRA approximates the update as:
  - **Wi := Wi + ΔWi, (1)**
  - **≈ Wi + AiBi, (2)**
- Where `Ai ∈ R𝑝×𝑟` and `Bi ∈ R𝑟×𝑞` are the decomposed matrices with low rank `r(r≪pos, r≪n)`
- Reduces number of trainable parameters compared to direct fine-tuning
- Allows for composition of LLMs with various LoRA modules tailored to specific tasks.


## 4 Methodology

**Modularized Networks for Hateful Meme Detection (Mod-HATE)**

**Overview**:
- Introduce innovative approach to few-shot hateful meme detection: Mod-HATE
- Core concept: Acquisition of essential reasoning skills through specialized modules
- Modules acquired from tasks closely aligned with hateful meme detection
- Importance scores assigned by a module composer
- Composed module weighted averaging the learned modules
- Integration of composed module with LLMs to create modularized networks for hateful meme detection

**Components**:
1. **LoRA based on LLMs**: Acquisition of reasoning capabilities from related tasks, including image-related tasks using a converter
2. **Converter**: Transforms images into textual descriptions
3. **Module Composer**: Generates importance scores for individual modules
4. **Modularized Networks**: Integration of composed modules with LLMs

**Details**:
1. LoRA modules acquired from related tasks, including hateful meme detection (Section 4.2)
2. Training of module composer (Section 4.3)
3. Construction of modularized networks by integrating composed modules with LLMs (Section 4.4)
4. Application of modularized networks for hateful meme detection:
   - Meme comprehension
   - Hateful meme interpretation tasks (Figure 2)

**Examples**:
- Figure 3: (a) Meme Comprehension, (b) Hateful Meme Interpretation Tasks.


### 4.2 LoRA Module Learning

**LoRA Modules for Hateful Meme Detection**

**Converter**:
- Translates images into textual descriptions to overcome modality limitations of LLMs
- Uses the PT-VLM, BLIP-2, FlanT5 XL as the captioning model
- Generates textual descriptions T from an image I: T = Converter(I)

**Relevant Tasks and Supervised Data**:
- 3 essential skills for hateful meme detection:
    1. Understanding what constitutes hateful content
    2. Deciphering concealed meaning in multimodal memes
    3. Interpreting why a meme is hateful
- 3 distinct tasks to acquire LoRA modules proficient in these reasoning skills:
    - **Hate Speech Detection**: Predict whether a text is hateful or non-hateful
    - **Meme Comprehension**: Decode the meaning of multimodal memes
    - **Hateful Meme Interpretation**: Explain why a meme is hateful

**Training LoRA Modules**:
- Use the widely used cross entropy loss to optimize LLMs for text generation
- Adopt the LLaMA (7B) language model as the decoder-only model
- Use the LoRA parameter-efficient tuning method to tune the LLM parameters
- Obtain a set of LoRA modules {Lₙ}n=1, where n=3

**Module Composer**:
- Learns how to assign importance scores to LoRA modules based on few-shot training examples
- Optimizes the module composer to generate the expected outputs for few-shot examples by composing LoRA modules: Lcomp = ∑ⁱ𝑠ₙLₙ
- Adapts the LLM with the composed module Lcomp and optimizes the module composer


### 4.4 Modularized Networks

**Modularized Networks for Hateful Meme Detection**

**Construction of Modularized Networks:**
- Consists of LLM (Language Model) and LoRA adapter
- LoRA modules comprise relevant tasks: Lcomp
- Attention weight matrices in frozen LLM updated with equation (8): Wₗ ≈ Wₗ + Acomp, Bcomp, 𝑖
- Networks modularized by adjusting importance scores over LoRA modules for new tasks or datasets

**Optimizing Module Composer:**
- Determine final importance scores assigned to LoRA modules using optimized networks

**Model Prediction:**
- Hateful meme detection as binary classification task
- Extract output probabilities corresponding to first predicted token, o|V| (V: vocabulary set)
- Use probability of 'No' to gauge probability of meme being non-hateful
- Probability of 'Yes': meme flagged as hateful
- Obtain classification probability, **a**∈R²: a₀ = oₗ (Vₗ = No), a₁ = oₙ (Vₙ = Yes)


## 5 Experiments

**Evaluation Framework**
* Three benchmark datasets used: Facebook Hateful Meme (FHM), Multimedia Automatic Misogyny Identification (MAMI), Harmful Meme (HarM)
* Evaluation metrics: standard accuracy (Acc.) and Area Under the Receiver Operating Characteristic curve (AUCROC)
* To mitigate evaluation variability, multiple few-shot examples generated with different random seeds for each setting
* Average accuracy and AUCROC scores computed over test sets after training on various few-shot samples

**Implementation Details**
* Use open-source package EasyOCR for meme text detection
* Remove meme texts on the image before captioning to avoid noise
* Optimize module composer using Covariance Matrix Adaptive Evolution Strategies provided by Nevergrad gradient-free optimization platform.

**Evaluation Setting (continued)**
* Facebook Hateful Meme dataset (FHM): diverse range of synthetic memes targeting vulnerable groups, often contains confounders requiring multimodal reasoning for classification
* Multimedia Automatic Misogyny Identification dataset (MAMI): memes derogatory towards women, sourced from social platforms like Twitter and Reddit
* Harmful Meme dataset (HarM): COVID-19 related memes categorized into three levels of harm: harmless, partially harmful, very harmful (combined under label "harmful")

**Evaluation Metrics**
* Accuracy (Acc.) and Area Under the Receiver Operating Characteristic curve (AUCROC) used for evaluation.


### 5.2 Baselines

**Few-Shot Hateful Meme Detection: Baselines using In-Context Learning**

**Baselines for Few-Shot Hateful Meme Detection:**
- Utilize few training examples as demonstrations and prompt pre-trained models with the concatenation of demonstrations and testing example for prediction
- Examine baselines built on PT-VLMs (Partially Trainable Visual Language Models) that integrate multimodal in-context learning: Flamingo, OpenFlamingo, GPT-3, and OPT models.

**Flamingo:**
- Derived from Chinchilla LLM
- Proprietary, limited to reported outcomes for its 3B and 9B parameter models on FHM dataset

**OpenFlamingo:**
- Open-source version of Flamingo using MPT LLM as foundation
- Assessed with both 3B and 9B configurations
- Employed Otter-9B due to absence of multi-GPU support in OpenFlamingo for instructional tasks

**Large Language Models:**
- GPT-3 recognized for in-context learning efficacy
- Employed OPT model (freely available version) for fair comparison

**Experiment Results:**
- Conducted under two few-shot learning scenarios: 4-shot and 8-shot examples
- Proposed model outperforms all in-context learning baselines across all three benchmarks, including Flamingo's 32-shot results reported in a prior study.

**Scaling Up Models:**
- Increasing model size tends to enhance performance of in-context learning methods
- Substituting LLaMA-7B with larger counterparts (13B or 65B) may lead to further advancements.

**Ablation Studies:**
- Table 3 summarizes different modules' impact on AUC and accuracy in the 4-shot setting: hate-speech, hate-interp, meme-comp.

**LoRA Modules Weights:**
- H-S: hate-speech LoRA module
- H-I: hateful interp LoRA module
- M-C: meme comprehension LoRA module
- Table 4 shows the weights of these modules for different datasets and number of shots.

**Number of Shots:**
- Both baseline models and proposed method exhibit a plateau in performance, with some configurations even showing a decline as the number of training examples increases.
- Indicates that hateful meme detection remains challenging within few-shot framework, requiring innovative approaches for effectively leveraging limited examples.

### 5.4 Ablation Study

**Ablation Study Findings:**
* Examining contributions of different modules in a modularized network
* Focus on 4-shot setting due to space constraints
* Integration of all three modules surpasses performance of any two-module combination:
  + Accuracy and AUCROC
* Isolated hate-speech module outperforms on three datasets regarding AUCROC
* Suggests bias in the learned model for hate speech detection
* Necessity of additional modules for complex multimodal understanding

**Observations:**
* Hate-speech module's superior performance on three datasets:
  + All predictions non-hateful
* Importance scores of modules (Table 4):
  + Meme comprehension module registers the lowest importance score but negatively impacts performance if absent.

**Visualization of Predictions:**
* Table 5 shows individual module predictions, compositions of two modules, and from modularized networks.
* Incorrect prediction in red.

**Ground Truth:**
* Hateful (Religion): Mocks Muslims for violent nature; dehumanizes females
* Non-hateful: Conveys that Islam is a religion of peace; men do dishes, women do laundry; women who claim to be virgins are lying

**Modularized Networks:**
* hate-speech module: No (incorrect) prediction in red for all cases
* meme-comp module: Correctly conveys the intentions of memes regarding religion and gender
* hate-interp module: Incorrectly identifies hate speech in some cases
* Modularized networks: Various combinations of modules; results shown in Table 5.


### 5.5 Qualitative Analysis

**Case Studies on Mod-HATE Model**
* **Table 5**: Shows predictions from individual modules, module combinations, and full Mod-HATE model for three example memes
* **Role of Modules**:
  * Dedicated to hateful meme interpretation (hate-interp) and meme comprehension (meme-comp) contribute significantly to accuracy
  * Aid in detection and enhance model's explanatory power
  * When used alone, effectiveness diminishes as they provide descriptive explanations rather than clear-cut classifications
* **Module Integration**: Crucial for optimal functioning
* **Limitations of Individual Modules**:
  * Hate-interp: Tendency to incorrectly interpret content as hateful due to exclusive training on hateful examples (second example)
  * Struggles with generalizing to diverse, visually complex memes encountered in real world scenarios (third example)
  * Limited efficacy when cross-modal reasoning required is not straightforward (first and third example)
* **Benefits of Modules Integration**:
  * Synergistic improvement in detection capabilities
  * Augments model's interpretability, providing a more comprehensive solution to hateful meme detection.


## 6 Conclusion

**Study on Hateful Meme Detection in Few-Shot Setting**

**Background:**
- Research on hateful meme detection in few-shot setting
- Limited labeled training examples available

**Proposed Method:**
1. **Modularized networks**: Train a set of modules for relevant tasks
2. Learn composition of modules using few-shot examples
3. More efficient than standard in-context learning: Few-shot examples not used during inference
4. Outperformed previous methods on three benchmarks

**Funding:**
- Supported by the Ministry of Education, Singapore (Grant No.: T2EP20222-0047)

**Acknowledgement:**
- Any opinions, findings, conclusions or recommendations expressed in this material are those of the authors and do not reflect the views of the Ministry of Education, Singapore.

**Conference:**
- WWW '24, May 13–17, 2024, Singapore, Singapore.


## A Details of Implementation

**LoRA Module Learning Hyperparameters**
- **Learning rate (Lr.)**: 0.0005
- **Batch size (Bz.)**: 16 for hate-speech, 8 for meme-comp and hate-interp
- **Number of epochs**: 1 for hate-speech, 2 for meme-comp and hate-interp

**Implementation Details**
- All models implemented under the **PyTorch Library** (CUDA-11.2 version)
- NVIDIA A40 GPU with dedicated memory of 48GB used
- Implementation of **OpenFlamingo model**: Took code released by authors [2]
- Implementation of **LLAMA model**: Leveraged **HuggingFace Library** (yahma/llama-7b-hf checkpoint) with HuggingFace version 4.33.0
- Implementation of **LoRA parameter-efficient tuning**: Adopted from the PEFT Library (version 0.5.0)
- Training of LoRA modules optimized using **Huggingface trainer**

**Model Parameters and GPU Memory Requirements**
- Table 6 provides hyperparameters for LoRA module learning
- All LoRA modules set to have ranks of 16
- Model parameters in LLaMA converted to binary float take 21GB dedicated GPU memory during inference with Mod-HATE
- Training the module composer takes about 21GB dedicated GPU memory

**Meme Text Constraints and Table of Model Params**
- Each meme image's text length is constrained to be 25 characters
- If text exceeds this limit, it will be truncated
- Number of model parameters summarized in Table 7:
    - **OPT-13B**: 13B
    - **OPT-30B**: 30B
    - **OpenFlamingo-3B**: 3B (OpenFlamingo-9B: 9B)
    - **Flamingo-3B**: 3.2B (Flamingo-9B: 9.3B)
    - **Mod-HATE**: 7B


## B Error Cases

**Error Cases of Mod-HATE**

**Inaccurate Predictions from Modules:**
- **hate-speech**: Dehumanizes individuals based on nationality or gender
- **hate-interp**: Dehumanizes immigrants and women
- **meme-comp**: Conveys that refugees are not people, and women can't cook like their mothers
- **Solution:** Improve individual module performance for better final prediction

**Different Memes Rely on Different Modules:**
- **hate-speech** (Shallow multimodal understanding): Can detect hateful meme correctly
- **Skills from other modules may be redundant in this case**
- **Solution:** Module composer generates instance-dependent importance scores for better prediction.

**Error Cases:**
| Meme | Ground Truth: Hateful (Nationality/Gender) | Predicted as Hateful by Modules |
| --- | --- | --- |
| hate-speech | No | Yes |
| hate-interp | It dehumanizes the immigrants as lesser humans and degrades women | It does not convey hate speech but interprets it as hateful |
| meme-comp | Meme conveys that children are not people and women can't cook like their mothers | Not detected as hateful by any module |
| meme-comp, hate-speech | The meme is hateful because it dehumanizes refugees | Not detected as hateful by any module |
| meme-comp, hate-interp | It is hateful because it degrades women and suggests they are not good cooks | Not detected as hateful by any module.


## C Templates for In-context Learning

**Template for Prompting Pre-trained Models**
* For prompting OpenFlamingo: "It is an image with: [MEME_TEXT] written on it. Is it hateful? GPT: <answer>"
	+ Replace "[MEME_TEXT]" with the real meme text
* For prompting Otter, WWW '24, May 13–17, 2024, Singapore:
	+ "is an image with: [MEME_TEXT] written on it. Is it hateful? Answer:"
* For prompting OPT after converting meme images to textual descriptions (CAP):
	+ "Please decide whether the meme is hateful according to its image caption and meme text. Image Caption: [CAP]; Meme Text: [MEME_TEXT] Prediction:"
* Few-shot examples will be converted into similar format of prompts and positioned at the beginning

**Importance Scores for LoRA Modules**
* Provided in both 4-shot and 8-shot settings with standard deviation (Table 9)
	+ Hate-speech LoRA module: H-S
	+ Hate-exp LoRA module: H-E
	+ Meme-captions module: M-C
* Example rows in the table:
	+ Dataset: FHM, MAMI, HarM
	+ Mean ± SD of weights for each module in different datasets.


## E Limitations

**Hateful Meme Detection: Improving Skills**

**Relevant Tasks for Hateful Meme Detection:**
- Three tasks considered: text analysis, visual processing, metaphor comprehension (optional)
- Broader range of tasks can lead to more versatile detection capabilities

**LoRA Modules and Importance Scores:**
- Same importance scores assigned to LoRA modules regardless of meme type
- Text part may require different emphasis in hateful meme detection
- Hate speech LoRA module essential for some memes
- Reasoning across modalities crucial for others
- Future improvements: instance-dependent module composer for optimal importance scores based on meme attributes.

