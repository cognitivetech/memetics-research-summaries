# Towards Explainable Harmful Meme Detection through Multimodal Debate between Large Language Models

[Towards Explainable Harmful Meme Detection through Multimodal Debate between Large Language Models](https://arxiv.org/html/2401.13298) arxiv.org


**Comparison of Harmful Meme Detection Systems**

**Baselines:**
- Text BERT (Devlin et al., 2019)
- Image Region (Ren et al., 2016; He et al., 2016)
- Late Fusion (Pramanick et al., 2021a)
- MMBT (Kiela et al., 2019)
- VisualBERT COCO (Li et al., 2019; Lin et al., 2014)
- ViLBERT CC (Lu et al., 2019)
- MOMENTA (Pramanick et al., 2021b)
- MaskPrompt (Cao et al., 2022)
- Pro-Cap (Cao et al., 2023)

**Evaluation Metrics:** Accuracy and macro-averaged F1 score

**Datasets:**
- Harm-C: COVID-19 related memes
- Harm-P: US politics related memes
- FHM: Labeled by Facebook for harmful or harmless classification

**Improvements with ExplainHM:** 3.24%, 2.46%, and 3.71% in terms of Macro-F1 score on Harm-C, Harm-P, and FHM datasets, respectively.

**Observations:**
1. Performance improvements on Harm-P are subdued compared to other datasets due to its small volume and politics focus.
2. Performance improvements increase as scale and difficulty of the dataset increase for ExplainHM.
3. Baselines in first group perform lower due to unimodal features, while remaining baselines effectively leverage multimodal features from both text and image parts of memes.
4. Early-fusion models with multimodal pre-training outperform simple fusion with unimodal pre-training on Harm-C and Harm-P datasets.
5. MOMENTA performs better by considering global and local information in the second group, especially on Harm-P dataset.
6. MaskPrompt incorporates additional extracted entities and demographic information into masked language models, leading to best performance among baselines on FHM.
7. LLaVA and ChatGPT struggle when directly deployed for this task due to their lack of specific design for harmful meme detection.
8. Multimodal Debate CoT reasoning enhances LLMs' detection performance, especially with the LLM judge in the 'w/ MDCoT' setting.
9. ExplainHM further improves model performance by fine-tuning Small LM judge to avoid impractical fine-tuning of LLM judge while considering prior preference given by LLM judge.
10. Performance degradation occurs when proposing components like Multimodal Debate and multimodal fusion with small LM are missing, as demonstrated in ablative studies.

**Performance Comparison of ExplainHM with Different Settings**

**Impact of LLM Judge (LLMJ)**:
- The 'w/o LLMJ' setting achieves worse performance than ExplainHM, suggesting that the prior preference of the LLM judge on the rationales from different positions plays an important role in identifying harm-indicative elements.

**Importance of Small LM Judge (SLMJ)**:
- The decrease in performance for 'w/o SLMJ' is significant, underscoring the importance of the Small LM judge fine-tuned specifically for this task.

**Role of Multimodal Debate Mechanism**:
- ExplainHM makes improvements over 'w/o HlD' and 'w/o HfD', implying the promoting role of the multimodal debate mechanism that incorporates rationales from the harmless and harmful arguments into the language model.
- The 'w/o HlD' setting leads to a larger performance drop than 'w/o HfD', because there are more harmless meme samples in the training data compared to harmful ones.

**Importance of Cross-attention Fusion Mechanism**:
- Compared with ExplainHM, the performance of 'w/o MF' significantly decreases, highlighting the importance of the cross-attention fusion mechanism to mitigate potential misalignments between the LLMs and the rationales.

**Impact of Removing Unpreferred Rationale (UR)**:
- In the 'w/o UR' setting, removing the rationale not preferred by the LLM judge in the input text of the Small LM judge results in performance degradation, reaffirming the usefulness of the conflicting rationales appended in the input text.

**Ablative Studies on ExplainHM Variants**:
1. **w/o Multimodal Debate (MD)**: Fine-tune the Small LM judge without the multimodal debate stage between LLMs.
2. **w/o LLM Judge (LLMJ)**: Concatenate the harmfulness rationales into the input text in a fixed order.
3. **w/o Small LM Judge (SLMJ)**: Use the output of the LLM judge as the final prediction.
4. **w/o Harmless Debater (HlD)**: Concatenate only the rationale from the harmful argument with the meme text as the input text.
5. **w/o Harmful Debater (HfD)**: Concatenate only the rationale from the harmless argument with the meme text as the input text.
6. **w/o Multimodal Fusion (MF)**: Instead of the fusion mechanism on multimodal features, append linguistic features from image captioning.
7. **w/o Unpreferred Rationale (UR)**: Concatenate only the rationale preferred by the LLM judge and the meme text as the input text.

**Evaluation of Explanations from LLMs**

**Automatic Evaluation Limitations**:
- Cannot realistically measure quality of chosen explanations generated by multimodal debate between LLMs

**Human Subjects Study**:
- 50 harmful samples randomly selected from FHM test set
- 10 professional linguistic annotators evaluate explanations:
  - From LLaVA (Liu et al., 2023a) and ChatGPT (Ouyang et al., 2022)
  - Written by Human (Hee et al., 2023)
- Metrics of human evaluation are the same as automatic evaluation
