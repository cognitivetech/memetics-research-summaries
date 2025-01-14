# Text or Image? What is More Important in Cross-Domain Generalization Capabilities of Hate Meme Detection Models?

[Text or Image? What is More Important in Cross-Domain Generalization Capabilities of Hate Meme Detection Models?](https://arxiv.org/html/2402.04967) arxiv.org


**Cross-Domain Generalization in Multimodal Hate Meme Detection**
* **Challenge of Cross-Domain Generalization**: Previous studies suggest that multimodal hate meme detection models do not generalize well across different domains.
* **Reasons for Poor Generalization**: Possible causes include:
  * Implicit knowledge captured by multi-modal hate messages (Ma et al., 2022; Gomez et al., 2020; Zhong et al., 2016; Hosseinmardi et al., 2015)
  * Additional annotation noise in multimodal settings (Oriol Sàbat, 2019)
  * More complex network architectures
* **Approach**: Utilize a text-only (unimodal) hate classifier to detect hateful memes, then apply it to transformed meme test data.
* **Findings**:
  * Performance of unimodal classifier is comparable to or even better than late-fusion-based MM models in certain instances.
  * Average F1 increase of 0.05 for the unimodal classifier compared to MM models.
  * Textual modality demonstrates superior generalizability compared to image modality.
* **Explanation of Behavior of MM Models**: Retrain MM models on hateful meme datasets with captions and observe small performance drops (average Δ F1 of 0.02) regardless of the presence of captions in test sets.
* **Contribution Analysis**: Use Shapley values to determine textual contribution to prediction, which decreases when image caption is incorporated during training.
* **Confounder Dataset**: Compose a confounder dataset of memes featuring celebrities or known figures and observe that MM models are sensitive to text confounders but not image ones (average Δ F1 of 0.18 for both Text and Image confounder sets).
* **Limitations**: Previous studies also represent similar hypotheses, but in explicit types of downstream tasks.
