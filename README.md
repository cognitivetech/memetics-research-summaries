# Memetics Reserach Summaries

\***Note**:
- Filename with Title Case have a flat structure
- Lower case filenames have a clickable ToC and were summarized by section.

These are two different generation methods based on the input type. I am interested in feedback on how people like the different styles.

## Contents
- [arXiv](#arxiv)
  - [Generation and Creation](#generation-and-creation)
  - [Applications and Special Uses](#applications-and-special-uses)
  - [Safety and Robustness](#safety-and-robustness)
  - [Detection and Classification](#detection-and-classification)
    - [Emotion and Sentiment Analysis](#emotion-and-sentiment-analysis)
    - [Hate and Toxicity Detection](#hate-and-toxicity-detection)
  - [Analysis and Understanding](#analysis-and-understanding)
    - [Virality and Evolution Studies](#virality-and-evolution-studies)
    - [Linguistic and Content Analysis](#linguistic-and-content-analysis)
    - [Financial Impact](#financial-impact)
    - [Datasets and Tools](#datasets-and-tools)
- [Defender's Corner: Culture Science](#defenders-corner-culture-science)

## arXiv
### Generation and Creation
- [XMeCap: Meme Caption Generation with Sub-Image Adaptability](research-papers/XMeCap-Meme-Caption-Generation-with-Sub-Image-Adaptability_2407.17152.md) (2024-07)
- [MemeCraft: Contextual and Stance-Driven Multimodal Meme Generation](research-papers/MemeCraft-Contextual-and-Stance-Driven-Multimodal-Meme-Generation_2403.14652.md) (2024-03)
- [A Template Is All You Meme](research-papers/a-template-is-all-you-meme_2311.06649.md) (2023-11)
- [Memeify: A Large-Scale Meme Generation System](research-papers/memeify-a-large-scale-meme-generation-system_1910.12279.md) (2019-10)
- [MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences](research-papers/memefacegenerator-adversarial-synthesis-of-chinese-meme-face-from-natural-sentences_1908.05138.md) (2019-08)

### Applications and Special Uses
- [Variance of entropy for testing time-varying regimes with an application to meme stocks](research-papers/variance-of-entropy-for-testing-time-varying-regimes-with-an-application-to-meme-stocks_2211.05415.md) (2022-11)
- [Meme as Building Block for Evolutionary Optimization of Problem Instances](research-papers/meme-as-building-block-for-evolutionary-optimization-of-problem-instances_1207.0702.md) (2012-07)
- [Toward Emerging Topic Detection for Business Intelligence: Predictive Analysis of Meme Dynamics](research-papers/toward-emerging-topic-detection-for-business-intelligence-predictive-analysis-of-meme-dynamics_1012.5994.md) (2010-12)

### Safety and Robustness
- [MemeGuard: An LLM and VLM-based Framework for Advancing Content Moderation via Meme Intervention](research-papers/MemeGuard-An-LLM-and-VLM-based-Framework-for-Advancing-Content-Moderation-via-Meme-Intervention_2406.05344.md) (2024-06)
- [GOAT-Bench: Safety Insights to Large Multimodal Models through Meme-Based Social Abuse](research-papers/GOAT-Bench-Safety-Insights-to-Large-Multimodal-Models-through-Meme-Based-Social-Abuse_2401.01523.md) (2024-01)

### Detection and Classification
**Evolution of meme classification approaches**:\
*From building custom classifiers to leveraging pre-trained models.*
1. Pre-Embedding Era:
   - Custom architectures (MemeFier, MemeTector)
   - Task-specific models
   - Heavy feature engineering
2. Modern [CLIP](https://github.com/cognitivetech/llm-research-summaries/blob/main/document-processing/Learning-Transferable-Visual-Models-From-Natural-Language-Supervision_2103.00020.md)/Embedding Era:
   - Leveraging pre-trained models
   - Focus on adapting large-scale embeddings
   - Multiple CLIP-based approaches
3. Specialized approaches remain relevant for:
   - Limited resources
   - Domain-specific needs
   - Interpretability
   - Specific performance requirements

---
- [A CLIP-based siamese approach for meme classification](research-papers/A-CLIP-based-siamese-approach-for-meme-classification_2409.05772.md) (2024-09)
- [MemeCLIP: Leveraging CLIP Representations for Multimodal Meme Classification](research-papers/MemeCLIP-Leveraging-CLIP-Representations-for-Multimodal-Meme-Classification_2409.14703.md) (2024-09)
- [MemeFier: Dual-stage Modality Fusion for Image Meme Classification](research-papers/memefier-dual-stage-modality-fusion-for-image-meme-classification_2304.02906.md) (2023-04)
- [MemeTector: Enforcing deep focus for meme detection](research-papers/memetector-enforcing-deep-focus-for-meme-detection_2205.13268.md) (2022-05)
- [UVCE-IIITT@DravidianLangTech-EACL2021: Tamil Troll Meme Classification: You need to Pay more Attention](research-papers/uvce-iiittdravidianlangtech-eacl2021-tamil-troll-meme-classification-you-need-to-pay-more-attention_2104.09081.md) (2021-04)

#### Emotion and Sentiment Analysis
- [Emotion-Aware Multimodal Fusion for Meme Emotion Detection](research-papers/Emotion-Aware-Multimodal-Fusion-for-Meme-Emotion-Detection_2403.10279.md) (2024-03)
- [Unimodal Intermediate Training for Multimodal Meme Sentiment Classification](research-papers/unimodal-intermediate-training-for-multimodal-meme-sentiment-classification_2308.00528.md) (2023-08)
- [Meme Sentiment Analysis Enhanced with Multimodal Spatial Encoding and Facial Embedding](research-papers/meme-sentiment-analysis-enhanced-with-multimodal-spatial-encoding-and-facial-embedding_2303.01781.md) (2023-03)
- [NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis](research-papers/nuaa-qmul-aiit-at-memotion-3-multi-modal-fusion-with-squeeze-and-excitation-for-internet-meme-emotion-analysis_2302.08326.md) (2023-02)
- [NYCU-TWO at Memotion 3: Good Foundation, Good Teacher, then you have Good Meme Analysis](research-papers/nycu-two-at-memotion-3-good-foundation-good-teacher-then-you-have-good-meme-analysis_2302.06078.md) (2023-02)
- [Domain-aware Self-supervised Pre-training for Label-Efficient Meme Analysis](research-papers/domain-aware-self-supervised-pre-training-for-label-efficient-meme-analysis_2209.14667.md) (2022-09)
- [Exercise? I thought you said 'Extra Fries': Leveraging Sentence Demarcations and Multi-hop Attention for Meme Affect Analysis](research-papers/exercise-i-thought-you-said-extra-fries-leveraging-sentence-demarcations-and-multi-hop-attention-for-meme-affect-analysis_2103.12377.md) (2021-03)
- [NUAA-QMUL at SemEval-2020 Task 8: Utilizing BERT and DenseNet for Internet Meme Emotion Analysis](research-papers/nuaa-qmul-at-semeval-2020-task-8-utilizing-bert-and-densenet-for-internet-meme-emotion-analysis_2011.02788.md) (2020-11)
- [DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis](research-papers/dsc-iit-ism-at-semeval-2020-task-8-bi-fusion-techniques-for-deep-meme-emotion-analysis_2008.00825.md) (2020-08)

#### Hate and Toxicity Detection
- [OSPC: Artificial VLM Features for Hateful Meme Detection](research-papers/OSPC-Artificial-VLM-Features-for-Hateful-Meme-Detection_2407.12836.md) (2024-07)
- [Toxic Memes: A Survey of Computational Perspectives on the Detection and Explanation of Meme Toxicities](research-papers/Toxic-Memes-A-Survey-of-Computational-Perspectives-on-the-Detection-and-Explanation-of-Meme-Toxicities_2406.07353.md) (2024-06)
- [Zero shot VLMs for hate meme detection: Are we there yet?](research-papers/Zero-shot-VLMs-for-hate-meme-detection-Are-we-there-yet_2402.12198.md) (2024-02)
- [Improving Hateful Meme Detection through Retrieval-Guided Contrastive Learning](research-papers/Improving-Hateful-Meme-Detection-through-Retrieval-Guided-Contrastive-Learning_2311.08110.md) (2023-11)
- [Mapping Memes to Words for Multimodal Hateful Meme Classification](research-papers/mapping-memes-to-words-for-multimodal-hateful-meme-classification_2310.08368.md) (2023-10)
- [Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection](research-papers/pro-cap-leveraging-a-frozen-vision-language-model-for-hateful-meme-detection_2308.08088.md) (2023-08)
- [HateProof: Are Hateful Meme Detection Systems really Robust?](research-papers/hateproof-are-hateful-meme-detection-systems-really-robust_2302.05703.md) (2023-02)
- [Hate-CLIPper: Multimodal Hateful Meme Classification based on Cross-modal Interaction of CLIP Features](research-papers/hate-clipper-multimodal-hateful-meme-classification-based-on-cross-modal-interaction-of-clip-features_2210.05916.md) (2022-10)
- [Feels Bad Man: Dissecting Automated Hateful Meme Detection Through the Lens of Facebook's Challenge](research-papers/feels-bad-man-dissecting-automated-hateful-meme-detection-through-the-lens-of-facebooks-challenge_2202.08492.md) (2022-02)
- [An Interpretable Approach to Hateful Meme Detection](research-papers/an-interpretable-approach-to-hateful-meme-detection_2108.10069.md) (2021-08)
- [AOMD: An Analogy-aware Approach to Offensive Meme Detection](research-papers/aomd-an-analogy-aware-approach-to-offensive-meme-detection-on-social-media_2106.11229.md) (2021-06)
- [Enhance Multimodal Model Performance with Data Augmentation: Facebook Hateful Meme Challenge Solution](research-papers/enhance-multimodal-model-performance-with-data-augmentation-facebook-hateful-meme-challenge-solution_2105.13132.md) (2021-05)

##### Misogyny Identification
- [M3Hop-CoT: Misogynous Meme Identification with Multimodal Multi-hop Chain-of-Thought](research-papers/M3Hop-CoT-Misogynous-Meme-Identification-with-Multimodal-Multi-hop-Chain-of-Thought_2410.09220.md) (2024-10)
- [Codec at SemEval-2022 Task 5: Multi-Modal Multi-Transformer Misogynous Meme Classification Framework](research-papers/codec-at-semeval-2022-task-5-multi-modal-multi-transformer-misogynous-meme-classification-framework_2206.07190.md) (2022-06)
- [Misogynistic Meme Detection using Early Fusion Model with Graph Network](research-papers/misogynistic-meme-detection-using-early-fusion-model-with-graph-network_2203.16781.md) (2022-03)

### Analysis and Understanding
#### Virality and Evolution Studies
- [Diffusion approximation of a network model of meme popularity](research-papers/diffusion-approximation-of-a-network-model-of-meme-popularity_2206.10960.md) (2022-06)
- [Competition Dynamics in the Meme Ecosystem](research-papers/competition-dynamics-in-the-meme-ecosystem_2102.03952.md) (2021-02)
- [Dissecting the Meme Magic: Understanding Indicators of Virality in Image Memes](research-papers/dissecting-the-meme-magic-understanding-indicators-of-virality-in-image-memes_2101.06535.md) (2021-01)
- [A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics](research-papers/a-model-for-meme-popularity-growth-in-social-networking-systems-based-on-biological-principle-and-human-interest-dynamics_1902.00533.md) (2019-02)
- [Sleeping Beauties in Meme Diffusion](research-papers/sleeping-beauties-in-meme-diffusion_1604.07532.md) (2016-04)
- [Meme creation and sharing processes: individuals shaping the masses](research-papers/meme-creation-and-sharing-processes-individuals-shaping-the-masses_1406.7579.md) (2014-06)
- [Meme and Variations: A Computer Model of Cultural Evolution](research-papers/meme-and-variations-a-computer-model-of-cultural-evolution_1309.7524.md) (2013-09)
- [May the Best Meme Win!: New Exploration of Competitive Epidemic Spreading over Arbitrary Multi-Layer Networks](research-papers/may-the-best-meme-win-new-exploration-of-competitive-epidemic-spreading-over-arbitrary-multi-layer-networks_1308.4880.md) (2013-08)
- [Competition-induced criticality in a model of meme popularity](research-papers/competition-induced-criticality-in-a-model-of-meme-popularity_1305.4328.md) (2013-05)
- [Competition and Success in the Meme Pool: a Case Study on Quickmeme.com](research-papers/competition-and-success-in-the-meme-pool-a-case-study-on-quickmemecom_1304.1712.md) (2013-04)

#### Linguistic and Content Analysis
- [Analyzing Persuasive Strategies in Meme Texts: A Fusion of Language Models with Paraphrase Enrichment](research-papers/Analyzing-Persuasive-Strategies-in-Meme-Texts-A-Fusion-of-Language-Models-with-Paraphrase-Enrichment_2407.01784.md) (2024-07)
- [What Makes a Meme a Meme? Identifying Memes for Memetics-Aware Dataset Creation](research-papers/What-Makes-a-Meme-a-Meme-Identifying-Memes-for-Memetics-Aware-Dataset-Creation_2407.11861.md) (2024-07)
- [Social Meme-ing: Measuring Linguistic Variation in Memes](research-papers/social-meme-ing-measuring-linguistic-variation-in-memes_2311.09130.md) (2023-11)
- [Automatic Discovery of Political Meme Genres with Diverse Appearances](research-papers/automatic-discovery-of-political-meme-genres-with-diverse-appearances_2001.06122.md) (2020-01)

#### Financial Impact
- [The echo chamber effect resounds on financial markets: a social media alert system for meme stocks](research-papers/the-echo-chamber-effect-resounds-on-financial-markets-a-social-media-alert-system-for-meme-stocks_2203.13790.md) (2022-03)
- [Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator](research-papers/exploring-the-endogenous-nature-of-meme-stocks-using-the-log-periodic-power-law-model-and-confidence-indicator_2110.06190.md) (2021-10)
- [On the "mementum" of Meme Stocks](research-papers/on-the-mementum-of-meme-stocks_2106.03691.md) (2021-06)

#### Datasets and Tools
- [MATK: The Meme Analytical Tool Kit](research-papers/MATK-The-Meme-Analytical-Tool-Kit_2312.06094.md) (2023-12)
- [BanglaAbuseMeme: A Dataset for Bengali Abusive Meme Classification](research-papers/BanglaAbuseMeme-A-Dataset-for-Bengali-Abusive-Meme-Classification_2310.11748.md) (2023-10)
- [DisinfoMeme: A Multimodal Dataset for Detecting Meme Intentionally Spreading Out Disinformation](research-papers/disinfomeme-a-multimodal-dataset-for-detecting-meme-intentionally-spreading-out-disinformation_2205.12617.md) (2022-05)

## Defender's Corner: Culture Science
- [A Beginner's Guide to Culture Science](Defenders-Corner-Substack.md#a-beginners-guide-to-culture-science)
- [Why are we putting up with clickbait?](Defenders-Corner-Substack.md#why-are-we-putting-up-with-clickbait)
- [Blue tribe is starting to win by adopting the best of conservative values](Defenders-Corner-Substack.md#blue-tribe-is-starting-to-win-by-adopting-the-best-of-conservative-values)
- [Can we use Twitter Radar to empirically study \& predict culture?](Defenders-Corner-Substack.md#can-we-use-twitter-radar-to-empirically-study--predict-culture)
- [How to build culture tech](Defenders-Corner-Substack.md#how-to-build-culture-tech)
- [Destigmatize being dumb](Defenders-Corner-Substack.md#destigmatize-being-dumb)
- [Narrative Spears ](Defenders-Corner-Substack.md#narrative-spears-)
- ["We've been wrong about math for 2300 years \& I'm here to fix it"](Defenders-Corner-Substack.md#weve-been-wrong-about-math-for-2300-years--im-here-to-fix-it)
- [Feynman's Razor](Defenders-Corner-Substack.md#feynmans-razor-)

