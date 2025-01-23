# What do you MEME? Generating Explanations for Visual Semantic Role Labelling in Memes

[What do you MEME? Generating Explanations for Visual Semantic Role Labelling in Memes](https://arxiv.org/abs/2212.00715)

## Table of Contents
- [Generating Explanations for Visual Semantic Role Labelling in Memes](#generating-explanations-for-visual-semantic-role-labelling-in-memes)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 ExHVV : Dataset Curation and Annotation](#3-exhvv-dataset-curation-and-annotation)
- [4 Methodology](#4-methodology)
- [5 Baselines](#5-baselines)
- [6 Experimental Details](#6-experimental-details)
- [7 Error Analysis](#7-error-analysis)
- [8 Conclusion](#8-conclusion)

## Generating Explanations for Visual Semantic Role Labelling in Memes

**Memes: Generating Explanations for Visual Semantic Role Labeling**

**Introduction:**
- Memes as effective communication tools on social media
- Previous research focuses on affective spectrum and hate speech detection
- Introducing a novel task, EXCLAIM (Explanations for Visual Semantic Role Labeling)

**Dataset:**
- Curated ExHVV dataset: 3,000 memes with natural language explanations of connotative roles for heroes, villains, and victims (4,680 entities)

**Task and Baselines:**
- EXCLAIM: generating explanations for visual semantic role labeling in memes
- Benchmarking ExHVV against unimodal and multimodal baselines

**LUMEN Framework:**
- Jointly learning to predict correct semantic roles and generate natural language explanations
- Outperforms best baseline across 18 standard natural language generation evaluation metrics

**Conclusion:**
- Characteristic multimodal cues helpful for adjudicating semantic roles and generating suitable explanations.


## 1 Introduction

**Meme Analysis: ExCLAIM Task Formulation**

**Introduction:**
- Memes important for communicating complex ideas and discussing societal issues
- Recently used to cause harm (Pramanick et al., 2021a)
- Challenging to detect multimodal narrative framing of social entities in memes
- Goal: Generate natural language explanations that emulate human-like reasoning for given meme, referred entity, and semantic role

**Challenges:**
- Detecting sarcasm, satire, humor, irony in memes
- Contextualization of role labeling
- Abstract reasoning and multimodal contextualization required
- Text plays a significant role towards detection of hateful or harmful memes (Kiela et al., 2020a; Pramanick et al., 2021a,b)
- Image underperforms in detecting meme emotions (Singh et al., 2020; Ruiz et al., 2020)
- Modality influence varies across tasks

**Text–Image Relationship:**
- Text amplifies image, while an image inhibits it (Barthes & Heath, 1978)
- Memes consist of textual and visual components (Osterroth, 2018)

**Proposed Approach:**
- Benchmark ExHVV dataset using unimodal and multimodal baselines
- Propose LUMEN: multimodal encoder-decoder framework with entity-specific role label information and explanation generation capability via multi-task learning

**Contributions:**
1. EXCLAIM: novel task formulation for explanation generation in memes
2. ExHVV: multimodal dataset with natural language explanations accompanying memes, entities, and semantic roles
3. LUMEN: multimodal, multi-task learning framework that facilitates shared feature learning from semantically related tasks
4. Extensive study on explanation generation quality using 18 standard NLG evaluation measures.


## 2 Related Work

**Meme Analysis and Related Work**

**Meme Analysis**:
- Shared tasks on detecting hero, villain, and victim entities in memes
- Hateful meme detection: Kiela et al. (2020) and Zhou et al. (2021)
- Various solutions proposed, including fine-tuning Visual BERT and UNITER representations
- Systematic efforts using Transformers and other models for hateful meme detection
- Other tasks addressed: anti-semitism, propaganda techniques, harmfulness, harmful targeting, and meme detection

**Visual Question Answering (VQA)**:
- Early work by Antol et al. (2015) on open-ended questions and candidate answers
- Joint representation of images and questions
- Examining cross-modal interactions via attention mechanisms
- Incorporating common sense reasoning and external knowledge bases
- General models using non-linear transformations and Transformers for VQA
- Critical language priors constraining VQA performances

**Cross-Modal Association**:
- Increased interest due to multimodal data influx
- Accurate measurement of cross-modal similarity important for cross-modal retrieval and vision-language pre-training
- Traditional techniques: concatenation and self-attention
- Object-centric approaches: multi-grained alignment, capturing relations between visual concepts and text
- Later approaches: cross-modal semantic learning and contrastive loss formulations

**EXCLAIM Task**:
- Attempting to address a novel task in meme analysis.


## 3 ExHVV : Dataset Curation and Annotation

**Dataset Curation and Annotation**

**Datasets**:
- EXCLAIM requires a multimodal dataset with memes, semantic role labels for entities, and natural language explanations
- The dataset used is HVVMemes, which was recently released as part of the CONSTRAINT-2022 shared task
- HVVMemes was annotated considering the connotative labels for meme's entities by associating them with roles: hero, villain, victim or others across COVID-19 and US Politics

**ExHVV Dataset**:
- HVVMemes were augmented with natural language explanations for the connotative labels provided for entities present in memes
- ExHVV considers only hero, villain and victim roles, as other cases would be inherently ambiguous or out-of-scope
- This resulted in an increment of entity-specific sample count: hero - 78, villain - 616, victim - 159
- Annotators were requested to explain why an entity could be a hero, villain, or victim
- This resulted in a total of 4680 labeled samples
- Explanations reasonably varied across annotators in terms of vocabulary and length due to different explanation styles
- The subjectivity of the task is highlighted as memes often lead to several valid interpretations

**Annotation Process**:
- Two annotators were trained especially for obtaining explanations w.r.t. EXCLAIM
- They were prescribed standard annotation guidelines, which were drafted to assist them with the task requirements and ambiguity resolution
- The annotation guidelines emphasized:
  - Considering the meme author's viewpoint as a standardized reference
  - Explanations should be narrated/written using reported speech for opinions and in the simple present form when stating facts
  - Explanations should be lexically diverse
  - Cases labeled as others should be skipped
  - Entity should constitute as the explanation's primary subject
  - Obvious erroneous labels should be rectified
  - Explanations may follow a standardized format: [Entity] [Action/Abstract Word/Phrases] [Description]
  - Each explanation should refer to a single entity
  - Explanations may borrow facts from the OCR text
- The annotators were briefed on the annotation guidelines, and a common set of 20 random memes with 125 entities was used for assessing and streamlining the annotation patterns
- The test set was then annotated, considering the feedback from the consolidator
- The remaining memes were distributed among the annotators, with the consolidator adjudicating ambiguous cases
- The annotation quality was assessed via human evaluation by capturing the semantic validity and diversity of the explanations proposed


## 4 Methodology

**LUMEN: A Multimodal, Multi-Task Learning Framework for EXCLAIM**

**Components of LUMEN:**
1. **Visual Recognition**:
   - Extract meme text using Google's OCR Vision API
   - Perform OCR-based extraction on the meme image
   - Use OFA model for image captioning
   - Encode meme visuals using a ViT-based model and extract visual embedding Vhi2R768
2. **Entity Semantics**:
   - Utilize DeBERTa's last hidden layer output to capture semantics from textual content in memes
   - Fine-tune the setup towards sequence classification objective to obtain a mean-pooled representation for embedding entity-semantics (Thi2R1536)
3. **Explanation Generation**:
   - Formulate encoder input as combination of OCR-extracted text and caption
   - Use T5, a transformer-based encoder-decoder model, for generating natural language explanations conditioned on multimodal cues
   - Obtain the T5-decoder's mean-pooled last hidden layer representation (Ehi2R1024) and a language modeling loss (LEXP)
4. **Role-Label Prediction**:
   - Fuse representations from visual features, entity semantics, and T5-based explanations
   - Non-linearly project individual representations into 512dimensional space before concatenating them
   - Linearly project the fused representation to a 512-sized embedding for multi-class classiﬁcation
   - Use cross-entropy loss (LRP) for semantic role prediction, which is further incorporated into the overall multi-task learning objective
5. **Combining Loss Terms**:
   - Combine loss terms obtained from entity-semantics (LSEQ), explanation generation (LEXP), and role prediction (LRP) modeling objectives using a joint loss formulation: LLUMEN = LSEQ + LEXP + LRP


## 5 Baselines

**Baselines for ExHVV Benchmark:**

1. Text-only Baselines: T5, BERT, GPT2
2. Image-only Baseline: ViT, BEiT
3. Multimodal Baselines: Various combinations of Vision and Text Encoders & Decoders.


## 6 Experimental Details

**Experimental Details**

**Benchmarking Experiments**:
- Conduct multiple benchmarking experiments to compare LUMEN's performance with state-of-the-art systems
- Use exhaustive set of standard evaluation metrics for EXCLAIM task family: BLEU (B-[1,4]), METEOR (M), ROUGE-L (R-L), and CIDEr (C)

**Comparing Baseline Performances**:
- Discuss and compare explanations generated by unimodal (image/text-only), multimodal, and LUMEN systems

**Ablation Study**:
- Establish component-wise relevance by performing ablation study
- Evaluate best-performing models across modality configurations using additional closeness-measuring metrics: BERTScore, BP, chrF, GLEU, LASER, and RIBES, as well as error rate metrics: TER, WER, WER-D, WER-I, and WER-S

**Performance Comparison**:
- Compare LUMEN's performance with second best comparative baseline across the metric-specific variations

**Benchmarking EXHVV**:
- Evaluate EXCLAIM using gen-eval metrics for unimodal, multimodal, and LUMEN systems
- Observations:
  - Unimodal text-only systems exhibit good median scores (0.498, 0.396, 0.313, 0.230, 0.254, 0.468, 0.878) for BLEU-1/2/3/4 and METEOR, ROUGE-L, CIDEr
  - Unimodal text-only T5-based system outperforms BEiT-based vision-only by 0.5% in unigram overlap and 18% in consensus-based CIDEr score
  - Multimodal systems exhibit significant downgrade (4%) in explanation generation quality compared to unimodal text-only
  - LUMEN shows exceptional gen-eval performance, surpassing both unimodal and multimodal systems

**Exploring MTL for Explanation Generation**:
- Primary focus on evaluation of EXCLAIM using MTL for explanation generation
- Validation loss decreases steadily from 0.1345 to 0.1322 with an average decrement rate of 1:5e-4/epoch
- Role label prediction validation accuracies up to 98%

**Analyzing Explanations**:
- Unimodal systems' explanations are adequate, fluent, brief, and frequently accurate, with good median BLEU-1, BLEU-4, ROUGE-L, and CIDEr scores
- LUMEN contributes to the gen-eval suite by generating semantically aligned, complete, and factually relevant explanations

**Ablation Study**:
- Performance details when removing critical components from LUMEN:
  - Replacing simple concatenation-based fusion with self-attention-based fusion leads to an average decline of 2% across gen-eval suite
  - Adafactor optimizer shows better convergence and low memory footprint (1% drop)
  - wtd loss implies performing weighted combination of constituent loss terms, leading to a 0.5% drop in multi-task learning setup
  - Textual captions contribute crucial 2% to gen-eval scores
  - Replacing T5 decoder with GPT2 brings down average gen-eval score from 0.390 to 0.327, reinstating T5's robustness for NLU tasks
  - Removing deBERTa and ViT-based components leads to a reduction of 4% and 3%, respectively, in non-MTL configuration

**Extended Evaluation**:
- Further performed comparison using gen-eval & suite, which measures explanation generated text's closeness with ground-truth
- Observations:
  - Trend observed earlier for gen-eval is reflected again in gen-eval &, with models being in the decreasing order of LUMEN, UM-TXT-T5, followed by UM-IMG-BEiT.GPT2 and MM-ViT.BERT
  - Image-only models show subtle closeness compared to text-only one, suggesting their contributions to explanation generation


## 7 Error Analysis

**Limitations of LUMEN's Explanation Generation**:
* Falls short in exhibiting required inductive biases from ExHVV due to:
  * Inherent complexity of multimodal interactions
  * Resisting accurate prediction or inducing additional noise in the pipeline
* Strong intra/cross-modal grounding results in:
  * LUMEN picking up verbal or visual cues and missing semantic coherence
  * Occasionally observed impact on generated explanations

**Error Rates**:
* LUMEN yields increments of:
  * 3:3% on TER (test for reference sentences)
  * 12%, 26% on WER-I and WER-S, respectively (word error rate)
  * 43% deduction in WER-D score (diversity of explanations)
* Indicates complexity of bridging gap between reference sentences and candidate explanations
* Corroborated by novelty, creativity observed in LUMEN's explanations.


## 8 Conclusion

**Conclusion:**

* Introduced EXCLAIM: task for generating natural language explanations for semantic role labels within memes
* Presented ExHVV dataset and benchmarking setup with unimodal and multimodal baselines
* Proposed LUMEN: efficient, systematic multimodal, multi-task learning framework for EXCLAIM
* Showcased LUMEN's adequacy and fluency while highlighting limitations
* Released resources to foster future research on intra/cross-modal grounding and multimodal noise.


---

Thank you to arXiv for use of its open access interoperability.
