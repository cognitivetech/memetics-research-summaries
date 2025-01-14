# A CLIP-based siamese approach for meme classification

[A CLIP-based siamese approach for meme classification](https://arxiv.org/html/2409.05772) arxiv.org


**Funding for Research Projects:**
- Partially funded by Horizon 2020 European projects vera.ai (grant agreement no. 101070093) and AI4Media (grant agreement no. 951911)
- CHISTERA IV Cofund 2021 program funded by MCIN/AEI/10.13039/501100011033
- European Union NextGenerationEU/PRTR grants: FightDIS (PID2020-117263GB-100), XAI-Disinfodemics (PLEC2021-007681)
- IBERIFIER Plus project from European Comission (DIGITAL-2023-DEPLOY-04-EDMO-HUBS 101158511)
- Convenio Plurianual with Universidad Politécnica de Madrid and MCIN/AEI/10.13039/501100011033 for Programa de Excelencia para el Profesorado Universitario
- I+D+i project PLEC2021-007681, financed by MCIN/AEI/10.13039/501100011033 and European Union NextGeneration/PRTR
- National Natural Science Foundation of China (No. 62171114)
- Fundamental Research Funds for the Central Universities (Nos. N232400412 and DUT22RC(3)099)

**Warning:**
- Article contains explicit examples of potentially offensive subjects, including misogyny, racism, and calls to violence.

**Proposed Method for Meme Classification:**
- SimCLIP: deep learning-based architecture using CLIP encoder for cross-modal understanding
- Context-aware embeddings produced by pre-trained CLIP encoder
- Siamese fusion technique captures interactions between text and image.

**Experimentation and Results:**
- Extensive experimentation on seven meme classification tasks across six datasets
- New state of the art in Memotion7k with a 7.25% relative F1-score improvement
- Achieved super-human performance on Harm-P with 13.73% F1-Score improvement.

**Meme Classification Approach**

**Potential for Compact Meme Classification Models**:
- Enables accurate and efficient meme monitoring
- Code shared at https://github.com/jahuerta92/meme-classification-simclip

**Interplay between Visual and Textual Cues in Memes**:
- Reflects the core of their nature
- Respective representations lie on a shared vision-language space
- Vector operators can reveal internal associations or contradictions

**Preserving Critical Condition**:
- Using identical projection layers for image and text embeddings preserves this critical condition
- Elimination of this condition could be eliminated by creating semantically different embedding spaces

**Proposed SimCLIP Approach**:
- A Siamese approach utilizing CLIP features to capture cross-modal interactions effectively
- Addresses the challenges of contextual awareness and cross-modal understanding
- Leverages a large pre-trained Transformer with good off-the-shelf vision-language understanding
- Allows for:
  - Cross-modal element-wise operations for interaction-aware representation learning
  - Effective transfer learning to the meme classification domain

**Comparison to Other Approaches**:
- **Information fusion architectures**: Use pre-trained models to extract textual and visual features, but their success is limited due to unimodal understanding
- **CLIP embeddings**: Align the visual and textual modalities, containing information about each modality in both branches

**Challenges in Meme Understanding**:
- Difficulty in handling context and cross-modal interactions
- Inherent multimodality of memes
- Subjectivity of interpretation and annotations

**Importance of Memes in Social Media**:
- Carriers of concepts, ideas, and social values
- Spread cultural narratives through images and text
- Can steer narratives and harm society

**Meme Understanding Approaches:**
- **Concatenation of Text and Entity Detector**: Enriches text with context about potential harassment targets [15]
- **Demographic Information Extraction**: Improves predictions using demographic information from memes [12]
- **Visual Feature Extraction**: Utilizes pre-trained object detectors to extract visual features from regions of interest [27]
- **Fusion of Approaches**: Generates captions and extracts region-based visual features [31]
- **Contextual Information Incorporation**: Uses knowledge graphs for contextual information [11]
- **GAN Techniques**: Proposed for zero-shot hatefulness detection by generating target-aware meme representations [32]

**MOMENTA:**
- Includes named entities and other textual information, achieving outstanding performance in meme understanding [19]

**Multiple Models per Modality:**
- Adds necessary context to the detection task but carries a steep cost in training and inference [23, 9]
- Questionable ability to be trained outside of targeted tasks and datasets due to dataset-specific features

**Meme Classification:**
- A recently introduced task with challenges and workshops appearing in conferences [1, 10, 25]
- Focuses on hate speech detection, misogyny, and meme vs. non-meme classification [23, 9, 13]
- Variety of topics such as politics and COVID-19 [19]
- Detection of disinformation and manipulation through propaganda [5]

**CLIP (Contrastive Language-Image Pretraining) [21]:**
- Processes each modality to generate an embedding
- Trained with a contrastive objective for maximizing similarity between associated text-image pairs and minimizing unrelated pairs
- Offers common embeddings spaces for image and text, allowing joint interpretation with various operators
- Pretrained on extensive data allows encoding essential semantics for meme understanding

**SimCLIP Architecture:**
- Relies on two fundamental points: pretrained CLIP encoders as feature extractors and a common embedding space [21]
- Leverages CLIP's structural compliance with Siamese networks, enabling the use of common techniques like concatenation and Hadamard product [2, 22]
- Reduces trainable parameters by efficiently comparing embeddings and enhances generalization capabilities in small datasets.

**SimCLIP Architecture**
- Input image processed by OCR algorithm to extract text (ETXT)
- Image and text CLIP-encoded, projected using a Siamese feedforward network
  * Projections concatenated with absolute difference and Hadamard product
  * Final processing by a feedforward classification head
- Losses summed across heads in multitask settings
- Binary cross-entropy loss used for multilabel tasks, categorical cross-entropy for multiclass

**Architecture Details:**
1. Two separate CLIP encoders: EIMG and ETXT
2. Shallow network processes outputs of both encoders
3. Projections undergo activation and linear projection, then L2 normalization
4. Four features produced: [E{TXT}, E{IMG}, |E{TXT}-E{IMG}|, E{TXT}⋅E{IMG}]
5. Absolute difference highlights disagreement between image and text encoders
6. Product enhances activations on large positive values for high similarity or disagreement.

**Links:**
- https://github.com/jahuerta92/meme-classification-simclip.
