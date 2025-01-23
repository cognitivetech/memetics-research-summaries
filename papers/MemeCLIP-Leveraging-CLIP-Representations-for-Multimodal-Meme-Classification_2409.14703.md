# MemeCLIP: Leveraging CLIP Representations for Multimodal Meme Classification

[MemeCLIP: Leveraging CLIP Representations for Multimodal Meme Classification](https://arxiv.org/html/2409.14703) arxiv.org


**Study on Multimodal Understanding of Text-Embedded Images**

**Complexity of Text-Embedded Images**:
- Present a formidable challenge in machine learning due to the need for multimodal understanding
- Involves understanding multiple aspects of expression conveyed by text and images

**Previous Research Limitations**:
- Previous research on multimodal analysis primarily focused on singular aspects like hate speech

**Expanding Focus**:
- This study expands the focus to encompass multiple aspects:
  - Hate
  - Targets of hate
  - Stance (positive or negative)
  - Humor

**PrideMM Dataset**:
- **PrideMM**: A novel dataset comprising 5,063 text-embedded images associated with the LGBTQ+ Pride movement
- Addresses a serious gap in existing resources

**Experimentation and Baselines**:
- Conducted extensive experimentation on PrideMM using unimodal and multimodal baseline methods
- Established benchmarks for each task

**MemeCLIP Framework**:
- Proposed a novel framework MemeCLIP for efficient downstream learning while preserving the knowledge of the pre-trained CLIP model
- Achieves superior performance compared to previously proposed frameworks on two real-world datasets
- Discusses shortcomings and misclassified samples

**MemeCLIP Framework Architecture**:
- Leverages the knowledge of the Contrastive Language-Image Pre-Training (CLIP) model
- Uses linear layers to effectively disentangle image and text representations in CLIP's multimodal embedding space
- Implements a cosine classifier alongside Semantic-Aware initialization to make it more robust to class imbalances

**Importance of Understanding Memes**:
- Memes serve as vehicles of both solidarity and resistance, reflecting the multifaceted dynamics of attitudes and perceptions within the LGBTQ+ community and beyond
- Understanding the nuances of hate speech, opinions, and intended humor within memes is paramount for fostering an inclusive digital environment and combating online discrimination

**MemeCLIP Framework:**
* Leverages knowledge from CLIP's encoders to process multimodal information in images
* Uses Feature Adapters and residual connections for preventing overfitting
* Cosine classifier used for robustness against imbalanced data classes
* Multi-aspect datasets help encompass human emotions expressed on social media
* Ours aims to address gap by presenting a multimodal dataset with three aspects: hate, topical stance, and humor

**Comparison of Multimodal Datasets:**
* Differences in focus and annotations for hate speech detection
* Hateful Meme Challenge (HMC), Harm-C, Harm-P, MultiOFF datasets
* Tanaka et al. (2022) created a humor detection dataset
* Qu et al. (2022) introduced DisinfoMeme dataset for disinformative memes

**Inter-Annotator Agreement:**
* Fleiss’ Kappa (κ 𝜅 {kappa} italicκ) used to assess agreement across tasks
* Higher κ 𝜅 {kappa} italicκ from dry run phase to final phase indicates effective annotation schema.

**PrideMM Dataset:**
* Hate detection: balanced distribution of binary labels
* Target classification: heavily imbalanced distribution
* Stance classification: well-balanced across three labels
* Majority of images annotated for humor due to comedic or satirical purposes. 

**Task Descriptions:**
* Humor: identify images showcasing humor, sarcasm, or satire related to LGBTQ+ Pride movement
* Stance: annotate images into three categories based on their stance towards the LGBTQ+ movement.

**Neutral Labeling Guidelines:**
- **Neutral label**: given to contextually relevant images without support or opposition towards a movement

**Hate Target Classification:**
- **Undirected**: abstract topics, societal themes, ambiguous targets like ‘you’ not directed at specific individuals, entities, or groups
- **Individual**: hate targeted towards specific people including political leaders, celebrities, activists (e.g., "Joe Biden," "J.K. Rowling")
- **Community**: broader social, ethnic, or cultural groups (e.g., "LGBT," "trans")
- **Organization**: corporate entities, institutions, organizations (e.g., "Chick-fil-A," "government")

**Hate Speech Identification:**
- Primary focus: identifying images with intentional hateful sentiments
- Distinguish strong disagreement vs. hate speech
- Ensure accurate labeling of genuinely hateful content

**Annotation Process:**
1. Dry run to evaluate understanding of guidelines among annotators
2. Revision phase based on results and new instructions
3. Consolidation phase for final annotations and guideline consensus
4. Data collection from three popular social media platforms: Facebook, Twitter, Reddit
5. Filtering criteria to ensure relevance and quality
6. Deduplication of images using tools like dupeGuru and difPy
7. Text extraction using Google Cloud Vision API
8. Cleaning text data by removing non-alphanumeric elements for data quality

**Dataset Description:**
- Comprises 5,063 text-embedded images from 2020-2024 related to LGBTQ+ movement and memes
- Includes memes, posters, infographics relevant to the LGBTQ+ movement.

**MemeCLIP Framework:**
1. Utilizes pre-trained vision-language model CLIP for rich embeddings
2. Adds lightweight modules on top of CLIP for disentanglement, prevention of overfitting, and robustness to imbalanced data.

**Image and Text Representations**
- **Contrastive visual and linguistic content**: memes often involve contrastive visual and linguistic content to evoke a sense of irony
- **Linear Projection Layers**:
  - Promotes disentanglement of image and text representations in shared embedding space
  - Maps unimodal projections **F I p** and **FT p** to dimensions of CLIP's last hidden state, **D C L I P**
- **Feature Adapters**:
  - Retains CLIP's prior knowledge while learning features of new data
  - Balances knowledge of fine-tuned adapter and disentangled image and text projections using a residual ratio **α**
- **Final unimodal representations**: obtained by combining adapter outputs with original projections weighted by **α**

**Image and Text Projection Layers**
- **LI p r o j** (image) and **LT p r o j** (text) represent image and text projection layers respectively

**Overfitting Mitigation**
- **Feature Adapters**: adopted to mitigate overfitting when applying CLIP to smaller datasets
- **Residual connections**: used to integrate prior projections with adapter outputs, allowing model to balance knowledge from both modules.

**Fusing Image and Text Representations (Multimodal Representation)**
- **Fusion of Image and Text**: Obtained by using an element-wise multiplication operation (**∘ circ ∘**) between the image representation F\_I and text representation F\_T
- **Single Multimodal Representation**: F\_MM = F\_I **circ** F\_T

**Classification**
- **Cosine Classifier**: Robust to biases in prediction under class imbalances
- **Semantic-Aware Initialization (SAI)**: Exploits semantic knowledge held within the text encoder of CLIP
- **Text Encoding**: "A photo of {LABEL}" into F\_class
- **Initializing Classifier Weights**: W\_class using F\_class, where n is the number of classes
- **Predicted Logit**: Calculated as Z\_x = **σ × W\_x × F\_MM / (||W\_x||² ||F\_MM||²)**
  - Static scaling factor: **σ**

**Links:**
- https://github.com/SiddhantBikram/MemeCLIP

---

Thank you to arXiv for use of its open access interoperability.