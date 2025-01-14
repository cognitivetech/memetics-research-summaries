# Improving Hateful Meme Detection through Retrieval-Guided Contrastive Learning

[Improving Hateful Meme Detection through Retrieval-Guided Contrastive Learning](https://arxiv.org/html/2311.08110) arxiv.org


**Performance of RGCL on HatefulMemes Dataset:**
- Evaluated on HatefulMemes and HarMeme datasets
- State-of-the-art performance: AUC = 87.0% percent, Accuracy = 78.8% percent
- Outperforms previous systems like HateCLIPper (AUC = 85.5% percent), PromptHate (Accuracy = 84.5% percent), and LLaVA (Accuracy = 83.3% percent) on HarMeme dataset

**Comparison with Baseline Models:**
- Comparison with OD-based models: ERNIE-Vil, UNITER, OSCAR; similar AUC scores around 79%
- LMMs: Flamingo (86.6% AUC), Lens (59.4% AUC), Instruct-BLIP (54.1%, 57.5%), and LLaVA (57.9% AUC); RGCL outperforms all baseline systems on HatefulMemes dataset
- CLIP-based systems: PromptHate, HateCLIPper; surpasses original CLIP's performance but falls short of Flamingo-80B

**Transfer to Unseen Domain:**
- Demonstrates effective transfer to the unseen domain of hateful memes without retraining
- Evaluated on HarMeme dataset as retrieval database: AUC = 60.0% percent, Accuracy = 57.2% percent (with LR instead of KNN), surpassing baseline HateCLIPper and best LMMs' zero-shot performance
- Results indicate that fine-tuned LLaVA struggles to generalize effectively to diverse domains of hateful memes.

**RGCL's Performance Compared to Baseline and Zero-Shot LMMs**
* **RGCL's Impact on AUC:**
  * Boosts AUC by 12.2% percent (66.6 vs 54.4%)
  * Outperforms baseline by a large margin
* **RGCL's Accuracy:**
  * Achieves an accuracy of 59.9% percent (out of 100)
  * Surpasses the baseline by 9.6% percent (59.9 vs 50.3%)
* **Additional Information:**
  * RGCL's AUC and accuracy scores exceed zero-shot LMMs as well.
