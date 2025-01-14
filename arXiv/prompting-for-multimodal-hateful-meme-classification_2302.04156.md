# Prompting for Multimodal Hateful Meme Classification

[Prompting for Multimodal Hateful Meme Classification](https://arxiv.org/abs/2302.04156)

## Table of Contents
- [Abstract](#abstract)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 Preliminaries](#3-preliminaries)
- [4 Methodology](#4-methodology)
- [5 Experiments](#5-experiments)
- [6 Conclusion](#6-conclusion)
- [7 Limitations](#7-limitations)
- [APPENDIX](#appendix)
## Abstract

**Hateful Meme Classification: Prompt-based Model**

**Introduction:**
- Hateful meme classification is a challenging multimodal task
- Requires complex reasoning and contextual background knowledge
- Ideally, an external knowledge base could supplement information
- No known explicit external knowledge base for hate speech context
- Proposed solution: PromptHate - prompt-based model for hateful meme classification

**PromptHate:**
- Construct simple prompts
- Provide few in-context examples
- Exploit implicit knowledge in pre-trained RoBERTa language model
- Extensive experiments on two public hateful and offensive meme datasets

**Results:**
- Achieved high **AUC of 90.96**
- Outperforms state-of-the-art baselines on hateful meme classification

**Disclaimer:**
- This paper contains discriminatory content that may be disturbing to some readers.


## 1 Introduction

**Introduction:**
- Internet memes have become popular forms of communication on social media
- Memes can be presented as images with accompanying text, intended to be funny or satirical
- Malicious users generate and share hateful memes under the guise of humor
- Hateful memes can attack people based on race, ethnicity, religion, etc.

**Challenges in Hateful Meme Classification:**
- Comprehension of both visual and textual modalities required for effective classification
- Contextual background knowledge necessary to understand the meaning behind some memes
- Existing approaches have limitations in understanding implicit knowledge and context

**Proposed Approach: Prompt-Based Hateful Meme Classification with Pre-Trained Language Models (PLMs)**
- Convert images into textual descriptions for PLM understanding
- Design specific prompts to adapt and leverage the implicit knowledge in PLMs
- Given a meme and a prompt, the prompt-tuned PLM generates a textual output indicating the predicted label of the input meme
- Intuition: PLMs will tap into implicit and unstructured knowledge from their large pre-training data to generate the continuation of the prompt (e.g., "this is _" to "this is hateful.")

**Contributions:**
1. Proposed a multimodal prompt-based framework called PromptHate for hateful meme classification
2. Conducted extensive experiments on two publicly available datasets, showing that PromptHate outperforms state-of-the-art methods for the hateful meme classification task
3. Performed fine-grained analyses and case studies to examine the effectiveness of prompts in classifying hateful memes
4. First paper to explore prompting PLMs for hateful meme classification.


## 2 Related Work

**Related Work**

**Hateful Meme Detection**:
- Hateful meme classification is an emerging multimodal task
- Made popular by the availability of several recent hateful memes datasets
- Existing studies have adopted multimodal approaches to perform hateful meme classification
- Classic two-stream models combining text and visual features using attention-based mechanisms and other fusion methods
- Fine-tuning large scale pre-trained multimodal models
- Data augmentation and ensemble methods used to enhance performance
- DisMultiHate model proposed to disentangle hateful targets in memes

**Language Model Prompting**:
- Popularity of large-scale PLMs like GPT (Radford et al., 2019), BERT (Devlin et al., 2019), and RoBERTa (Liu et al., 2019)
- Prompt-based learning using PLMs as implicit and unstructured knowledge bases
- Recent studies prompting PLMs for NLP tasks like natural language inference and sentiment classification, yielding good performance in few-shot settings
- Prompting visual-language models for computer vision tasks
- Fewer works on prompting PLMs for multimodal tasks
- Yang et al. explored prompting GPT-3 model for the visual question & answering task, but has limitations due to cost and input length constraints

**Proposed Approach**:
- Prompts RoBERTa for the multimodal hateful meme classification task
- Aims to fill the research gap by leveraging the PLM's unstructured implicit knowledge for hateful meme classification.


## 3 Preliminaries

**Preliminaries**

**Problem Definition**:
- Multimodal hateful memes classification: Given an image (I) and text (O), a model predicts the label of the multimodal meme (hateful or non-hateful)
- Traditional binary classification: Model outputs probability vector y=[y0, y1], where y0 is the probability of non-hateful and y1 is the probability of hateful
- If y1 > y0, the meme is predicted as hateful; otherwise, non-hateful
- Transformation into Masked Language Modelling (MLM) problem: PLM prompted to fill [MASK] token with label (hateful or non-hateful)

**Image Captioning**:
- Convert image into textual input for PLMs
- Extract text from memes using EasyOCR and in-painting with MMEditing
- Apply pre-trained image captioning model, ClipCap, to generate captions describing dominant objects/events in the image
- Use generated captions as inputs into PromptHate model
- Extract entities and demographic information using Google Vision Web Entity Detection API and FairFace classifier
- Combine image captions and supplementary information (entities, demographics) as input to PLMs

**Note**:
- While the extracted supplementary information may capture key details, the contextual background knowledge is still absent in the image caption and supplementary information. For example, identifying a pig in the meme and extracting "Muslim" from text does not imply the knowledge that Muslims do not eat pork.


## 4 Methodology

**PromptHate Model Architecture**
- **Figure 2**: Illustrates the PromptHate model framework
- **Construction of a prompt**:
  - Consists of:
    - Positive demonstration (normal meme)
    - Negative demonstration (hateful meme)
    - Inference instance (meme to be predicted)
- **Preprocessing steps**:
  - Convert memes into text and image descriptions

**Prompt Creation**
- Templates: natural sentences with label words for inference instance
- Positive demonstration template: "the meme is good"
- Negative demonstration template: "the meme is bad"

**Demonstrations and Inference Instance**
- Concatenated with the inference instance to form the prompt S
- Demonstrations provide guidance for PLM on label word completion

**Template and Label Words**
- **Labels**: good (positive class) and bad (negative class)
  - Other label words compared in Section 5.2
- **Templates**: manually defined functions that map label words to sentences

**Model Training and Prediction**
- Feed the prompt S into the PLM (RoBERTa) for probability calculations:
  - y0 = P([MASK] = Wpos)
  - y1 = P([MASK] = Wneg)
- Loss calculated using cross-entropy loss with ground truth label ^y
- No additional parameters beyond PLMs, preserves pre-training objectives

**Multi-Query Ensemble**
- Demonstrations provide additional cues for understanding the target of hateful meme
- Multi-query ensemble strategy: predict inference instance using M pairs of demonstrations
- Final prediction is the average of all predicted scores.


## 5 Experiments

**Experiments: Datasets & Evaluation**

1. Introduction
   - Description of datasets
   - Evaluation setting

2. Hateful Meme Classification
   - Performance evaluation of PromptHate
   - Experimental setup and results

3. Prompt Settings
   - Studies on effects of different prompt settings
   - Results and discussion

4. Error Case Studies
   - Limitations of the model
   - Analysis of misclassified examples


# 5.1 Evaluation Settings

**Evaluation Settings**

**Datasets:**
- **Facebook Hateful Meme dataset (FHM)**
  * 3,050 hateful memes
  * 5,450 non-hateful memes
  * Limited availability of public datasets
  * Used for evaluation of dev-seen split
- **Harmful Meme dataset (HarM)**
  * Real COVID-19-related memes collected from Twitter
  * Labeled with three classes: very harmful, partially harmful, and harmless
  * Combined very harmful and partially harmful memes into hateful memes
  * Harmless memes regarded as non-hateful memes

**Evaluation Metrics:**
- **Area Under the Receiver Operating Characteristic curve (AUROC)**
- **Accuracy (Acc)**
- Measured for reliability with ten random seeds
- All models use same set of random seeds

**Baselines:**
- **Uni-modal baselines:**
  * Text-only model: fine-tuned BERT on meme text
  * Image-only model: processed meme image using Faster R-CNN with ResNet-152 and fed into a classifier
- **Multimodal baselines:**
  * Late Fusion
  * Concat BERT
  * MMBT-Region
  * ViLBERT CC
  * Visual BERT COCO
  * CLIP BERT
  * MOMETA
  * DisMultiHate
  * FT-RoBERTa

**Experimental Results:**

**Facebook Hateful Meme dataset (FHM):**
- Text BERT: AUC = 66.10%, Acc = 57.12%
- Image-Region: AUC = 56.69%, Acc = 52.34%
- Late Fusion: AUC = 66.34%, Acc = 59.14%
- Concat BERT: AUC = 66.53%, Acc = 60.80%
- MMBT-Region: AUC = 72.86%, Acc = 65.06%
- Visual BERT COCO: AUC = 68.71%, Acc = 61.48%
- ViLBERT CC: AUC = 84.11%, Acc = 78.70%
- CLIP BERT: AUC = 82.63%, Acc = 76.66%
- MOMETA: AUC = 86.32%, Acc = 80.48%
- DisMultiHate: AUC = 86.39%, Acc = 81.24%
- FT-RoBERTa: AUC = 89.26%, Acc = 82.32%
- PromptHate: AUC = 90.96%, Acc = 84.47%

**Harmful Meme dataset (HarM):**
- Text BERT: AUC = 81.39%, Acc = 75.68%
- Image-Region: AUC = 76.46%, Acc = 73.05%
- Late Fusion: AUC = 83.17%, Acc = 77.57%
- Concat BERT: AUC = 83.21%, Acc = 77.82%
- MMBT-Region: AUC = 85.48%, Acc = 79.83%
- Visual BERT COCO: AUC = 80.46%, Acc = 75.31%
- ViLBERT CC: AUC = 84.11%, Acc = 78.70%
- CLIP BERT: AUC = 82.63%, Acc = 76.66%
- MOMETA: AUC = 86.32%, Acc = 80.48%
- DisMultiHate: AUC = 86.39%, Acc = 81.24%
- FT-RoBERTa: AUC = 89.26%, Acc = 82.32%
- PromptHate: AUC = 90.96%, Acc = 84.47%


# 5.2 Experiment Results

**Experimental Results on FHM and HarM Datasets**

**Table 2 (FHM)**:
- Standard deviations of ten runs reported
- PromptHate outperforms state-of-the-art baselines: DisMultiHate, DisMultiHate-BL, DisMultiHate-RL, and FT-RoBERTa
- Significant improvement over the best baseline (p-value < 0.05)
- Multimodal approaches outperform unimodal baselines
- PromptHate demonstrates strength of prompting approach for hateful meme classification task

**Table 3 (HarM)**:
- Similar results as FHM
- PromptHate performs better on HarM, likely due to generalization difficulties in the dataset
- High standard deviation in FT-RoBERTa's performance on FHM, suggesting instability

**Additional Experiments**:
- Replacing RoBERTa-large with RoBERTa-base (PromptHate-RB): Outperforms DisMultiHate on HarM, slightly worse than DisMultiHate on FHM but with higher stability
- Replacing BERT-base in baseline models with RoBERTa-large (-RL) or BERT-large (-BL): Larger models do not necessarily outperform PromptHate
- Model size plays a critical role in PromptHate's performance

**Conclusion**:
- The experimental results demonstrate the effectiveness of the proposed prompting approach over state-of-the-art baselines.


# 5.3 Ablation Study

**Ablation Study of PromptHate:**

* Table 6: Performance decrease without MLM objective.
* MLM objective aligns with PLMs' training objectives.
* Enables better usage of embedding knowledge for hate speech classification.
* Can perform well without demonstrations.
* Demonstrations' effects in prompt-based models: ongoing research. (Min et al., 2022)


# 5.4 Prompt Engineering

**Prompt Engineering for PromptHate Model**

**Importance of Good Prompts**:
- Essential for prompt-based models like PromptHate
- Discussing effects of varying prompts on hateful meme classification performance

**Label Words**:
- Individual words representing labels used in prompt generation
- Investigating impact of replacing prompts with different label words

**Table 7: Effects of Label Words**:
- Replacing label words in positive and negative demonstrations
- Shows substantial differences in performances for full training and few-shot setting
- Label words aligned to semantic classes perform better than reverse mapping
- More significant differences observed in few-shot setting
- PromptHate relies more on label word semantics in few-shot setting

**Prompt with Hateful Target Information**:
- Explicit inclusion of target information can help improve hateful meme classification
- Changing prompt template to "It was [LABEL_MASK] targeting at [TARGET_MASK] ."
- Modeling loss from prediction of [LABEL_MASK] in inference instance
- Marginal differences observed after modeling target information in prompts
- Possible reason: Adds auxiliary burden to the model for better utilization, a more sophisticated strategy may be needed

**Table 8: PromptHate with and without Target**:
- Shows marginal differences in performance when target information is included

**Visualizing Predictions**:
- PromptHate with target information correctly predicts targets even in incorrect classifications
- Helps improve interpretability but also highlights difficulties of hateful meme classification


# 5.5 Error Analysis

**Analysis of PromptHate's Performance:**
* Examined incorrect predictions made by PromptHate (Table 10)
* Three examples given for reference
* Reasons for incorrect predictions:
	+ Lack of adequate context
	+ Biases learned by the model
	+ Advanced reasoning required to understand hateful context.

**Inadequate Context:**
* Images descriptions do not include all essential attributes for hateful meme detection
* Missing information supplemented with augmented image tags
* Example: "Jesus" missing from the captions of a meme about Jesus being used as an object to scare away birds.

**Biases Learned by the Model:**
* PromptHate makes incorrect predictions due to biases learned during training
* Example: Predicts right-most meme is hateful because of rainbow flag, which may be used in memes attacking LGBT community.

**Advanced Reasoning Required:**
* Some hateful memes require deeper multi-modal reasoning for understanding context
* PromptHate unable to detect the hatefulness in certain memes that imply hateful meanings without sufficient context.


## 6 Conclusion

**Conclusion: PromptHate**

1. **Proposed a multimodal framework**: PromptHate for hateful meme classification using pre-trained language models.
2. **Evaluations on public datasets**: Outperformed state-of-the-art baselines.
3. **Analyzed prompt settings and effectiveness**.
4. **Error analysis and discussion of limitations**.
5. **Future work**: Explore better demonstration selection and add reasoning modules.


## 7 Limitations

**Limitations of PromptHate**

**PromptHate Limitations:**
- In some instances, unable to tap into implicit Meme Target Distributions
- Incorrect predictions:
  * Hateful (race), Hateful (sex), Hateful (religion) when Ground Truth is Non-hateful
  * Non-hateful predicted as Hateful for certain memes
- Questionable Ground Truth for some memes
- Lacks advanced reasoning on contextual information
- May learn biases from training data
- Debiasing techniques needed to improve performance.

**Examples of Incorrect Predictions:**
* Meme: "the original scarecrow when you date an Asian boy and you trynna get his family to accept you"
  * Ground Truth: Questionable (Non-hateful or Hateful)
  * Prediction: Non-hateful
* Memes with rainbow flags, bisexuality, or transgender flags predicted as Hateful when they are Non-hateful.

**Demographics:**
* None: Black female, Latino Hispanic Male
  * Demographic information not considered in PromptHate's predictions.


## APPENDIX

**Experiment Settings**
- **Hardware**: Pytorch on NVIDIA Tesla V100 GPU with 32 GB dedicated memory, CUDA-10.2
- **Models**: Pre-trained models (BERT, RoBERTa, VisualBERT) from Transformers package by Huggingface
- **Parameter Counts**: Table 11 lists the number of parameters for all VQA models

**Methodology**
- **Learning Rates**: Set empirically, same as Lee et al. (2021) for BERT-based models, tested learning rates of 1 0 5 to 1:510 5 for RoBERTa-large based models
- **Optimizer**: AdamW is used for all models
- **Mini-batch Size**: Set at 16 during training
- **Ensemble Strategy**: Multi-query ensemble strategy with 4 querying times
- **Training Time**: One GPU takes six minutes to train and validate PromptHate per epoch, uses 10 training epochs for both PromptHate and baselines

**Image Captions Analysis**
- **Importance of Quality Image Captions**: Converts image into textual captions as input for PLMs, affects prompting and ultimately the hateful meme classification performance
- **Experiment with Different Image Captions**: Table 12 shows PromptHate's performance with ClipCap+COCO and ClipCap+CC (UC) generated captions. ClipCap+CC performs better due to its similarity to meme images in the CC dataset
- **Implications of Good Quality Captions**: The difference in performance between ClipCap+CC (UC) and other models highlights the importance of good quality captions in applying prompt-based models for hateful meme classification.

