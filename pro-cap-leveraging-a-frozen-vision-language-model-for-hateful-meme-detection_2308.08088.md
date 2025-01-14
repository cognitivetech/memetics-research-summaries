# Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection

[Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection](https://arxiv.org/abs/2308.08088)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Preliminary](#3-preliminary)
- [4 Proposed Method](#4-proposed-method)
	- [4.3 BERT-based Detection Model](#43-bert-based-detection-model)
	- [4.4 PromptHate for Hateful Meme Detection](#44-prompthate-for-hateful-meme-detection)
	- [4.5 Model Training and Prediction](#45-model-training-and-prediction)
- [5 Experiment](#5-experiment)
	- [5.1 Experiment Settings](#51-experiment-settings)
	- [5.2 Baselines](#52-baselines)
	- [5.4 Ablation Study](#54-ablation-study)
	- [5.5 Case Study](#55-case-study)
- [6 Conclusion](#6-conclusion)
- [APPENDIX](#appendix)
	- [A Details for Implementation](#a-details-for-implementation)
	- [B Full Ablation Study Results](#b-full-ablation-study-results)
	- [C Visualization Cases](#c-visualization-cases)
	- [D Results with Pro-Cap about One Target](#d-results-with-pro-cap-about-one-target)

## Abstract

**Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection**

**Overview**:
- Proposed approach to leverage pre-trained vision-language models (PVLMs) in hateful meme detection
- Uses probing-based captioning to generate critical captions for PVLMs

**Challenges in Hateful Meme Detection**:
- Multimodal task requiring understanding of both vision and language
- Importance of efficiently leveraging powerful PVLMs

**Previous Approaches**:
- Converting meme images into textual captions for language model predictions
- Suffers from non-informative image captions

**Proposed Approach: Pro-Cap**
- Prompt frozen PVLM with hateful content-related questions
- Use answers as image captions (Pro-Cap)
- Leverages PVLMs in zero-shot visual question answering manner

**Evaluation**:
- Effectiveness and generalization of the proposed method validated on three benchmarks

**Key Contributions**:
- Proposed probe-captioning approach to leverage PVLMs for hateful meme detection
- Demonstration of improved performance compared to previous approaches

**References**:
- Rui Cao, Ming Shan Hee, Adriel Kuek, Wen-Haw Chong, Roy Ka-Wei Lee, and Jing Jiang. 2023. Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection. In Proceedings of the 31st ACM International Conference on Multimedia (MM ’23), October 29-November 3, 2023, Ottawa, ON, Canada. https://doi.org/10.1145/3581783.3612498

**Disclaimer**:
- This paper contains violence and discriminatory content that may be disturbing to some readers.


## 1 Introduction

**Memes and Hateful Content**
- Memes are a popular form of communication on social media
- Often used to express humor or satire, but can also spread hateful content
- **Hateful memes**: attack individuals or communities based on race, gender, religion, etc.
- Propagation of hateful memes can lead to discord online and potentially result in hate crimes

**Challenges in Hateful Meme Detection**
- Multimodal nature of memes: involves understanding both images and texts
- Previous work used cross-modal interactions from scratch, but may be difficult to learn complicated multimodal interactions
- Development of **Pretrained Vision-Language Models (PVLMs)**: facilitated hateful meme detection by fine-tuning on task-specific data
- Difficulty in fine-tuning larger models like BLIP-2 and Flamingo due to billions of trainable parameters
- **PromptHate**: a recently proposed model that converts multimodal meme detection into a unimodal masked language modeling task
- Effectively uses rich background knowledge in the language model, but is significantly affected by quality of image captions

**Limitations of Existing Approaches**
- Dependence on costly APIs for entity and demographic information
- Inability to effectively utilize frozen PVLMs without adaptation or fine-tuning

**Proposed Methodology**
- Leverage the power of a frozen PVLM to complement the unimodal approach of PromptHate
- Use **probing questions** to query the PVLM for information related to common vulnerable targets in hateful content
- Obtain **Pro-Cap**: image captions generated from probing questions, used as input to a trainable hateful meme detection model
- **Probing-based captioning**: step of using probing questions to generate the Pro-Cap captions

**Contributions and Validation**
- Leverage PVLM without adaptation or fine-tuning, reducing computational cost
- Utilize frozen PVLM to generate captions containing information useful for hateful meme detection
- First work to leverage PVLMs in a zero-shot manner through question answering to assist in the hateful meme detection task
- Experimental results show that Pro-Cap PromptHate significantly surpasses original PromptHate and achieves comparable results with PromptHate with additional image tags
- Pro-Cap BERT surpasses multimodal BERT-based models, proving the generalization of the probing-based captioning method.


## 2 Related Work

**Memes as Hateful Content**
* Memes increasingly used for hateful content
* Challenging task of online hateful meme detection [5,12,27]

**Approaches to Hateful Meme Detection**
* Multimodal classification approach [20,26,34,37]
	+ Pre-trained vision-language models (PVLMs) fine-tuned on meme detection data
	+ Model ensembling for improved performance
* Combining pre-trained models with task-specific architectures and end-to-end tuning [13,14,28]
* Converting all meme information into text and prompting language models [2]
	+ State-of-the-art results on two hateful meme detection benchmarks
	+ Generic method for describing images through image captioning
	+ Ignores important factors necessary for hateful meme detection

**Proposed Approach: Probe-based Captioning**
* Seeks to address issue with generic method for describing images
* Prompting pre-trained vision-language models with hateful content-centric questions in zero-shot VQA manner.


## 3 Preliminary

**Defining the Task and Pre-trained Vision-Language Models (PVLMs)**

**Predefined task**: Predict whether a given meme image and accompanying text are hateful or not by generating scores for each label:
- **Non-hateful**: score 𝑠0
- **Hateful**: score 𝑠1

**Zero-shot Visual Question Answering (VQA)** with PVLMs:
- Assumes a pre-trained model capable of processing image and text prompt in format "Question: [QUESTION] Answer:"
- Generates an answer sequence of tokens as the response to the question, e.g., Asian for "What is the race of the person in the image?"

**Pretrained Vision-Language Model (PVLM) used**: BLIP-2 model [15]:
- Consists of a frozen pre-trained image encoder, frozen pre-trained language model, and a lightweight Querying Transformer to bridge modality gap.
- Demonstrated good performance in zero-shot VQA.
- Can be replaced with any other PVLM capable of zero-shot VQA.


## 4 Proposed Method

**Overview:**
- Key idea: elicit critical image details for hateful content detection using VQA
- Use zero-shot VQA due to lack of training data and promising performance
- Prompt PVLM with probing questions, regard answers as Pro-Cap
- Combine original text and Pro-Cap for input to hateful meme detection models

**Design of VQA Questions:**
- Obtain generic image description with first probing question
- Elicit critical details for hateful meme detection with additional questions
  - Religion, Race, Gender, Nationality, Disability
  - Example: "what is the race of persons in the image?"
- Prevent hallucinations by validating existence of persons and animals
- Use C to represent concatenated answers included in Pro-Cap
- Combine original text and C as input to hateful meme classification model.


### 4.3 BERT-based Detection Model

**Alternative Hateful Meme Classification Models**
* Based on BERT model: [T, C] concatenated for vector r generation
* Concatenation of meme text T and Pro-Cap C: r = BERT([T, C])
* Feed r into linear layer for hateful meme classification
* Sigmoid activation function: s = Sigmoid(WTr + b)

**Table 2 Details:**
* Questions prompting PVLMs
	+ Content of the image: What is shown?
	+ Vulnerable targets: Race, Gender, Religion, Nationality, Disability (Is there a person or animal?)
* Focus Questions: Content, Race, Gender, Religion, Nationality, Disability (Validating existence)

**Pro-Cap and Hateful Example:**
* RoBERTaTest Example Text: good = 0.05, bad = 0.9
* Pro-Cap Template: It was [MASK]. Captioning
	+ PVLMQ1: What content...?
	+ Q2: What is the religion...?
	+ ...
* Pro-Cap A1: A group of people with their hands up in the air
* Pro-Cap A2: The person is a Muslim.

**Non-hateful Example:**
* Hateful Example not provided.


### 4.4 PromptHate for Hateful Meme Detection

**Hateful Meme Classification Model: PromptHate [2]**

**Overview:**
- Second hateful meme classification model
- Employs prompt-based method for classification
- Leverages contextual background knowledge

**Approach:**
1. Obtain generic image captions using an image captioning model (ClipCap [25] in original study)
2. Concatenate meme text, image captions, and prompt template into S: "It was [MASK]."
3. Prompt language model (LM) to predict whether the meme is hateful based on context
4. Compare probability of LM predicting [MASK] as positive word vs negative word
5. Include one positive and one negative example in context, replace [MASK] with their respective label words

**Components:**
- Memes represented as O: [Text (T), Caption (C), Prompt (S)]
- Language models (LMs) such as RoBERTa [21] generate confidence scores for masked word over vocabulary space V
  - Score for positive label words: p0 = LM(Otest, Onon-hate, Ohate)
  - Score for negative label words: p1 = LM(Otest, Onon-hate, Ohate)

**Details:**
- PromptHate was developed to better leverage contextual background knowledge [2]
- Utilizes ClipCap [25] for image captioning in original study, replaced by Pro-Cap C in this work.


### 4.5 Model Training and Prediction

**Binary Cross-Entropy Loss for Hate Speech Detection in Meme Classification:**

* **Ground Truth Label (ŷ)**: A binary vector with components ŷ[0] = 1 and ŷ[1] = 0 for non-hateful memes, or [0,1] otherwise.
* **Binary Cross-Entropy Loss**:
$$ L = -(ŷ\_0 \cdot \text{log}(p\_0) + ŷ\_1 \cdot \text{log}(p\_1)) $$

* **Model Prediction**: If p\_0 > p\_1, the meme is classified as non-hateful; otherwise, it's considered hateful.


## 5 Experiment

**Evaluation**: Introduce datasets, metrics, implementation details.

    1. Evaluation Datasets
    2. Metrics for assessment
    3. Implementation specifics

**Baselines**: Present comparison methods.

**Analysis**:

    1. Qualitative: Case studies
    2. Error analysis
    3. Advantages and limitations of our method.


### 5.1 Experiment Settings

**Evaluation Datasets:**
- **Facebook Hateful Meme dataset (FHM)** [12]:
  * Constructed by Facebook
  * Contains synthetic memes with confounders
  * Deep multimodal reasoning required for detection
  * Categories: Religion, Race, Gender, Nationality, Disability
  * Evaluated on dev-seen split due to unavailable test labels

- **Multimedia Automatic Misogyny Identification (MAMI)** dataset:
  * Focuses on hateful memes targeting women
  * Reflects capability of hateful meme detection methods for female victims

- **HarM**:
  * Harmful memes related to COVID-19
  * Categories: harmless, partially harmful, very harmful
  * Tested for generalization from hateful meme detection to harmful meme detection

**Evaluation Metrics:**
- **Detection accuracy**
- **Area Under the Receiver Operating Characteristics curve (AUCROC)**
- Ten random seeds used with average performance and standard deviation reported
- All models use same set of random seeds

**Implementation Details:**
- Meme text detection using Easy-OCR tool
- Generate image captions for text-based hateful meme detection models
- Use BERT-based model with dropout rate and optimized AdamW for training
  - Learning rate: 2𝑒−5
  - Batch size: 64
- Train PromptHate model with batch size of 16 and learning rate set empirically
  - FHM: 1.3𝑒−5, other datasets: 1𝑒−5
  - Optimized using AdamW in PyTorch

**Additional Details:**
- Computation costs and model sizes provided in Appendix A.


### 5.2 Baselines

**Comparison of Pro-Cap BERT with Unimodal and Multimodal Models:**
* **Baselines**: Comparison between Pro-Cap BERT and various models using different modalities (unimodal or multimodal) to demonstrate effectiveness.
* **Unimodal Models**: Text-only model (Text-BERT) and image-only model (Image-Region).
	+ Text-BERT: Fine-tuned pre-trained BERT model on meme text only for classification.
	+ Image-Only Model: Extract object-level features from images using Faster-RCNN, perform average pooling, and feed the resulting vector into a classification layer.
* **Multimodal Models**: Categorized into two groups: generic multimodal models and models specifically designed for hateful meme detection.
	+ Generic Multimodal Models: MMBT-Region, VisualBERT (COCO), ViLBERT (CC), ALBEF, BLIP.
		- MMBT-Region: A multimodal baseline in hateful meme detection which has not been pre-trained with multimodal data.
		- VisualBERT (COCO) and ViLBERT (CC): Pre-trained on MS-COCO and Conceptual Captions respectively.
		- ALBEF and BLIP: Recently released powerful pre-trained models.
	+ Models Designed for Hateful Meme Detection: CLIP-BERT, MOMENTA, DisMultiHate, PromptHate.
		- CLIP-BERT: Leverages the CLIP model to handle noisy meme images and pre-trained BERT for representing meme text; fuses them with concatenation.
		- MOMENTA: Designed both local and global multimodal fusion mechanisms to exploit interactions for hateful meme detection.
		- DisMultiHate: Disentangles target information from memes as essential for identifying hateful content.
		- PromptHate: What we discussed in Section 4.4.

**Experiment Results:**
* Two settings for comparison: without any augmented image tags and with augmented image tags.
* Without augmented image tags: Pro-Cap BERT outperforms unimodal and multimodal models using BERT as text encoder, suggesting visual signals are vital for hateful meme detection and image captions obtained from probing questions are informative.
* With augmented image tags: Pro-Cap BERT still surpasses most powerful multimodal pre-trained BERT-base models despite having fewer model parameters, showcasing the importance of proper visual signal conversion through probe-based captioning.
* Pro-Cap PromptHate demonstrates significant advantages over recent state-of-the-art models like ALBEF and BLIP with a similar model size, especially on noisy real-world datasets like HarM.

**Ablation Study:**
* Impact of the length of VQA answers (Ans. Length) on Pro-Cap performance in FHM, MAMI, and HarM benchmarks.
* No Centric: Ablation without any centric prompts.
* Penalty = 1 to 3: Increasing penalty for longer answers.

**Table Comparison:**
* Tables comparing Pro-Cap PromptHate with basic PromptHate, highlighting differences in performance due to probe-based captioning.


### 5.4 Ablation Study

**Ablation Study**

**Impact of Asking Hateful-Content Centric Questions**:
- Ablation study on Pro-Cap method's impact of prompting PVLMs with questions facilitating hateful meme detection
- First question asks about image content, vs. second block with target-specific questions
- Removing captions from target-specific questions and only using generic image content caption
  - Improved performance on FHM (over 2%) and HarM (over 3%), but minor improvement on MAMI
    - MAMI memes are related to women, so generic captions may already cover the gender
- Including target-specific probing questions is more helpful for hateful meme detection

**Length of Answers to Probing Questions**:
- Using BLIP-2 as a zero-shot VQA model
- Experimented with answers of different lengths by setting length penalty in text decoder
- Results show robust performance and stability of the Pro-Cap method, with slight dataset preferences for answer length


### 5.5 Case Study

**Case Study: Comparing Pro-Cap PromptHate and PromptHate**

**Observations:**
- Generic captions about image content do not provide key information for hateful meme detection
- Asking questions about common vulnerable targets (race, country, religion) helps in identifying crucial facts
- Basic captions in original PromptHate miss these crucial facts

**Example 1:**
- All probe-captions generate sufficient image captions for hateful meme detection
- Model still fails at prediction due to current language models' poor complex reasoning abilities
- Small scale of hateful meme datasets may be inadequate for training a model
- Potential improvement with the development of better zero-shot VQA models

**Example 2:**
- Limitations of hateful content detection models: bias towards certain groups (Muslims) during training
- Debiasing techniques needed to address this issue

**Error Analysis:**
- All probe-captions generate sufficient image captions for hateful meme detection in most cases, but model still fails at prediction
- Minor errors in predicted answers from zero-shot VQA model (incorrect gender predictions)
- Development of better zero-shot VQA models could potentially facilitate improvements.


## 6 Conclusion

**Study Overview:**
- Attempt to leverage pre-trained vision-language models (PVLMs) for hateful meme detection
- Probe PVLMs in zero-shot VQA manner to generate hateful content captions
- Use distilled knowledge from large PVLMs to improve language model performance
- Achieve new state-of-the-art results on three benchmarks with simple BERT model

**Limitations:**
- Heuristically use answers to all probing questions as Pro-Cap, potentially including irrelevant ones
  - Performance of PromptHate with one probing question reported in Appendix D
  - Future direction: Train a model to dynamically select relevant probing questions for meme detection
- Effectiveness of Pro-Cap not thoroughly analyzed
  - Future direction: Use gradient-based interpretation approach to examine influence of different probing questions on final results


## APPENDIX

**Comparison between Pro-Cap Prompt and Basic Prompt on HarM Dataset**

**Meme**
- Ground Truth: Hateful (Trump's COVID-19 statement)
- Hateful (Trump's statement about keeping him safe from COVID-19)

**Basic Prompt**
- Cap-ition: Testing for a virus, cleaning a kitchen sink
- Prediction: Non-hateful

**Pro-Cap Prompt**
- Cap-ition: Trump in suit and tie (race, gender, country, religion), picture of a blender with cleaning products
- Prediction: Hateful (Trump's COVID-19 statement) or Generic (picture of blender)


### A Details for Implementation

**Implementation Details**
- All models implemented under **PyTorch Library** with **CUDA-11.2 version**
- Used **Tesla V 100 GPU** with dedicated memory of 32GB

**Hateful Meme Detection Models**
- Took codes from authors for reimplementation:
  - **CLIP-BERT/MOMENTA**: https://github.com/LCS2-IIITD/MOMENTA
  - **DisMultiHate**: https://gitlab.com/bottle_shop/safe/dismultihate
  - **PromptHate**: https://gitlab.com/bottle_shop/safe/prompthate
- Used packages from Huggingface:
  - **BERT**: Specifically the BERT model [4]
  - **VisualBERT**: [18]
  - **BLIP model**: Took the released code from the authors [23]

**Model Performance Comparison**
- No augmented image tags: Table 12 (AUC, Accuracy)
- Single probing question: Table 13 (AUC, Accuracy)

**Dataset Performance (FHM, MAMI, HarM)**
- **Race**: AUC=83.63±0.26, Accuracy=74.28±1.34
- **Gender**: AUC=83.91±0.97, Accuracy=76.08±1.47
- **Religion**: AUC=84.85±0.87, Accuracy=75.52±1.45
- **Nationality**: AUC=85.78±0.37, Accuracy=75.72±0.96
- **Disability**: AUC=85.26±0.64, Accuracy=75.96±0.82
- **Animal**: AUC=84.93±0.31, Accuracy=75.48±0.72

**Model Performance (Profanity, Cap PromptHate, ALBEF, BLIP-2)**
- Profanity: N/A
- Cap PromptHate: AUC=83.58±0.60, Accuracy=75.10±0.97
- ALBEF [17]: AUC=83.77±0.75, Accuracy=73.63±0.75
- BLIP-2 [15]: AUC=85.03±1.51, Accuracy=82.65±2.01

**Training Details**
- Constrained total length of meme text and generic image caption to be 65 characters
- Limited length of additional questions to be shorter than 20 characters
- Truncated or padded sentences accordingly
- Set number of training epochs to 10 for all models

**Model Parameters Summary**
(Table 11)


### B Full Ablation Study Results

* Results of accuracy presented in ablation studies: Table 6
* Full results with AUC and accuracy: Table 12.


### C Visualization Cases

**Section 5.5: Comparing Pro-Cap PromptHate vs. Basic PromptHate**

- Visualization of additional case studies:
  + HarM dataset: Table 9 (omitted due to space)
  + MAMI dataset: Table 10

(No need to include specific details from the tables as they are not provided in the text.)


### D Results with Pro-Cap about One Target

**Observations on Using Answers from Single Probing Questions**

**Single Probing Question Results**:
- Reported results when models use answers from a single probing question (instead of all probing questions)
- Some models using single probing question answers are **powerful** and can even **surpass** the performance of heuristically asking all probing questions
- Using all probing captions may not be the **optimal solution** and may generate **irrelevant image descriptions**
- For hateful memes targeting certain groups (e.g., black people), it is **meaningless** to ask about irrelevant details like their religion

**MAMI Performance**:
- When using answers to the probing question about **gender**, models reach the best performance on MAMI
- This is because MAMI contains only hateful memes about women

**Promising Directions**:
- Train the model to **dynamically select** essential probing questions for different memes

