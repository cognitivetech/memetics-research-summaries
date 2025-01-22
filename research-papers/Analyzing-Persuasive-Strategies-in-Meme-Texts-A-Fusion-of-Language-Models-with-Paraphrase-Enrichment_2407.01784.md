# Analyzing Persuasive Strategies in Meme Texts: A Fusion of Language Models with Paraphrase Enrichment

[Analyzing Persuasive Strategies in Meme Texts: A Fusion of Language Models with Paraphrase Enrichment](https://arxiv.org/html/2407.01784) arxiv.org


**Subtask 1 of SemEval-2024 Shared Task 4:**
* Detection of persuasion techniques in memes' textual content
* Fine-tuning three language models: BERT, XLM-RoBERTa, mBERT
* Ensemble modeling using mean aggregation
* Data augmentation through paraphrasing
* Adjusted classification thresholds based on class-wise metrics
* Zero-shot approach for languages other than English during testing
* Results showed good performance advantages over baseline in most languages except Arabic.

**Approach:**
* Inspired by successful approaches in multi-label text classification [2, 3]
* Three language models: fine-tuning and ensemble modeling
* Data augmentation through paraphrasing and adjusted thresholds
* Zero-shot approach for surprise languages during testing

**Evaluation:**
* Official results demonstrated good performance advantages over baseline in most languages except Arabic
* Paraphrasing techniques enhance model performance but using a balanced training set is more beneficial
* Analysis highlights potential downside of indiscriminately incorporating paraphrases from diverse distributions as it can introduce noise into the system.

**Section 2:** Review of previous work in multi-label classification.

**Section 3:** Overview of task and data utilized for Subtask 1.

**Section 4:** Classification pipeline, techniques used for data augmentation during fine-tuning.

**Section 5:** Experimental details including training datasets, evaluation metrics, and languages tested.

**Section 6:** Analysis of model results, discussion on performance advantages and challenges.

**Section 7:** Conclusions and future work.

---

Thank you to arXiv for use of its open access interoperability.