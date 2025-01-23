# Memetics Reserach Summaries

\***Note**:
- Filename with Title Case have a flat structure
- Lower case filenames have a clickable ToC and were summarized by section.

These are two different generation methods based on the input type. I am interested in feedback on how people like the different styles.

## Contents
- [Papers](#papers)
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

## Papers
### Generation and Creation
- (2019-08) [MemeFaceGenerator: Adversarial Synthesis of Chinese Meme-face from Natural Sentences](papers/memefacegenerator-adversarial-synthesis-of-chinese-meme-face-from-natural-sentences_1908.05138.md)
- (2019-10) [Memeify: A Large-Scale Meme Generation System](papers/memeify-a-large-scale-meme-generation-system_1910.12279.md)
- (2023-11) [A Template Is All You Meme](papers/a-template-is-all-you-meme_2311.06649.md)
- (2024-03) [MemeCraft: Contextual and Stance-Driven Multimodal Meme Generation](papers/MemeCraft-Contextual-and-Stance-Driven-Multimodal-Meme-Generation_2403.14652.md)
- (2024-07) [XMeCap: Meme Caption Generation with Sub-Image Adaptability](papers/XMeCap-Meme-Caption-Generation-with-Sub-Image-Adaptability_2407.17152.md)

### Applications and Special Uses
- (2010-12) [Toward Emerging Topic Detection for Business Intelligence: Predictive Analysis of Meme Dynamics](papers/toward-emerging-topic-detection-for-business-intelligence-predictive-analysis-of-meme-dynamics_1012.5994.md)
- (2012-07) [Meme as Building Block for Evolutionary Optimization of Problem Instances](papers/meme-as-building-block-for-evolutionary-optimization-of-problem-instances_1207.0702.md)
- (2022-11) [Variance of entropy for testing time-varying regimes with an application to meme stocks](papers/variance-of-entropy-for-testing-time-varying-regimes-with-an-application-to-meme-stocks_2211.05415.md)

### Safety and Robustness
- (2024-01) [GOAT-Bench: Safety Insights to Large Multimodal Models through Meme-Based Social Abuse](papers/GOAT-Bench-Safety-Insights-to-Large-Multimodal-Models-through-Meme-Based-Social-Abuse_2401.01523.md)
- (2024-06) [MemeGuard: An LLM and VLM-based Framework for Advancing Content Moderation via Meme Intervention](papers/MemeGuard-An-LLM-and-VLM-based-Framework-for-Advancing-Content-Moderation-via-Meme-Intervention_2406.05344.md)

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
- (2021-04) [UVCE-IIITT@DravidianLangTech-EACL2021: Tamil Troll Meme Classification: You need to Pay more Attention](papers/uvce-iiittdravidianlangtech-eacl2021-tamil-troll-meme-classification-you-need-to-pay-more-attention_2104.09081.md)
- (2022-05) [MemeTector: Enforcing deep focus for meme detection](papers/memetector-enforcing-deep-focus-for-meme-detection_2205.13268.md)
- (2023-04) [MemeFier: Dual-stage Modality Fusion for Image Meme Classification](papers/memefier-dual-stage-modality-fusion-for-image-meme-classification_2304.02906.md)
- (2024-09) [A CLIP-based siamese approach for meme classification](papers/A-CLIP-based-siamese-approach-for-meme-classification_2409.05772.md)
- (2024-09) [MemeCLIP: Leveraging CLIP Representations for Multimodal Meme Classification](papers/MemeCLIP-Leveraging-CLIP-Representations-for-Multimodal-Meme-Classification_2409.14703.md)

#### Emotion and Sentiment Analysis
- (2020-08) [DSC IIT-ISM at SemEval-2020 Task 8: Bi-Fusion Techniques for Deep Meme Emotion Analysis](papers/dsc-iit-ism-at-semeval-2020-task-8-bi-fusion-techniques-for-deep-meme-emotion-analysis_2008.00825.md)
- (2020-11) [NUAA-QMUL at SemEval-2020 Task 8: Utilizing BERT and DenseNet for Internet Meme Emotion Analysis](papers/nuaa-qmul-at-semeval-2020-task-8-utilizing-bert-and-densenet-for-internet-meme-emotion-analysis_2011.02788.md)
- (2021-03) [Exercise? I thought you said 'Extra Fries': Leveraging Sentence Demarcations and Multi-hop Attention for Meme Affect Analysis](papers/exercise-i-thought-you-said-extra-fries-leveraging-sentence-demarcations-and-multi-hop-attention-for-meme-affect-analysis_2103.12377.md)
- (2022-09) [Domain-aware Self-supervised Pre-training for Label-Efficient Meme Analysis](papers/domain-aware-self-supervised-pre-training-for-label-efficient-meme-analysis_2209.14667.md)
- (2023-02) [NUAA-QMUL-AIIT at Memotion 3: Multi-modal Fusion with Squeeze-and-Excitation for Internet Meme Emotion Analysis](papers/nuaa-qmul-aiit-at-memotion-3-multi-modal-fusion-with-squeeze-and-excitation-for-internet-meme-emotion-analysis_2302.08326.md)
- (2023-02) [NYCU-TWO at Memotion 3: Good Foundation, Good Teacher, then you have Good Meme Analysis](papers/nycu-two-at-memotion-3-good-foundation-good-teacher-then-you-have-good-meme-analysis_2302.06078.md)
- (2023-03) [Meme Sentiment Analysis Enhanced with Multimodal Spatial Encoding and Facial Embedding](papers/meme-sentiment-analysis-enhanced-with-multimodal-spatial-encoding-and-facial-embedding_2303.01781.md)
- (2023-08) [Unimodal Intermediate Training for Multimodal Meme Sentiment Classification](papers/unimodal-intermediate-training-for-multimodal-meme-sentiment-classification_2308.00528.md)
- (2024-03) [Emotion-Aware Multimodal Fusion for Meme Emotion Detection](papers/Emotion-Aware-Multimodal-Fusion-for-Meme-Emotion-Detection_2403.10279.md)

#### Hate and Toxicity Detection
- (2021-05) [Enhance Multimodal Model Performance with Data Augmentation: Facebook Hateful Meme Challenge Solution](papers/enhance-multimodal-model-performance-with-data-augmentation-facebook-hateful-meme-challenge-solution_2105.13132.md)
- (2021-06) [AOMD: An Analogy-aware Approach to Offensive Meme Detection](papers/aomd-an-analogy-aware-approach-to-offensive-meme-detection-on-social-media_2106.11229.md)
- (2021-08) [An Interpretable Approach to Hateful Meme Detection](papers/an-interpretable-approach-to-hateful-meme-detection_2108.10069.md)
- (2022-02) [Feels Bad Man: Dissecting Automated Hateful Meme Detection Through the Lens of Facebook's Challenge](papers/feels-bad-man-dissecting-automated-hateful-meme-detection-through-the-lens-of-facebooks-challenge_2202.08492.md)
- (2022-10) [Hate-CLIPper: Multimodal Hateful Meme Classification based on Cross-modal Interaction of CLIP Features](papers/hate-clipper-multimodal-hateful-meme-classification-based-on-cross-modal-interaction-of-clip-features_2210.05916.md)
- (2023-02) [HateProof: Are Hateful Meme Detection Systems really Robust?](papers/hateproof-are-hateful-meme-detection-systems-really-robust_2302.05703.md)
- (2023-08) [Pro-Cap: Leveraging a Frozen Vision-Language Model for Hateful Meme Detection](papers/pro-cap-leveraging-a-frozen-vision-language-model-for-hateful-meme-detection_2308.08088.md)
- (2023-10) [Mapping Memes to Words for Multimodal Hateful Meme Classification](papers/mapping-memes-to-words-for-multimodal-hateful-meme-classification_2310.08368.md)
- (2023-11) [Improving Hateful Meme Detection through Retrieval-Guided Contrastive Learning](papers/Improving-Hateful-Meme-Detection-through-Retrieval-Guided-Contrastive-Learning_2311.08110.md)
- (2024-02) [Zero shot VLMs for hate meme detection: Are we there yet?](papers/Zero-shot-VLMs-for-hate-meme-detection-Are-we-there-yet_2402.12198.md)
- (2024-06) [Toxic Memes: A Survey of Computational Perspectives on the Detection and Explanation of Meme Toxicities](papers/Toxic-Memes-A-Survey-of-Computational-Perspectives-on-the-Detection-and-Explanation-of-Meme-Toxicities_2406.07353.md)
- (2024-07) [OSPC: Artificial VLM Features for Hateful Meme Detection](papers/OSPC-Artificial-VLM-Features-for-Hateful-Meme-Detection_2407.12836.md)

##### Misogyny Identification
- (2022-03) [Misogynistic Meme Detection using Early Fusion Model with Graph Network](papers/misogynistic-meme-detection-using-early-fusion-model-with-graph-network_2203.16781.md)
- (2022-06) [Codec at SemEval-2022 Task 5: Multi-Modal Multi-Transformer Misogynous Meme Classification Framework](papers/codec-at-semeval-2022-task-5-multi-modal-multi-transformer-misogynous-meme-classification-framework_2206.07190.md)
- (2024-10) [M3Hop-CoT: Misogynous Meme Identification with Multimodal Multi-hop Chain-of-Thought](papers/M3Hop-CoT-Misogynous-Meme-Identification-with-Multimodal-Multi-hop-Chain-of-Thought_2410.09220.md)

### Analysis and Understanding
#### Virality and Evolution Studies
- (2013-04) [Competition and Success in the Meme Pool: a Case Study on Quickmeme.com](papers/competition-and-success-in-the-meme-pool-a-case-study-on-quickmemecom_1304.1712.md)
- (2013-05) [Competition-induced criticality in a model of meme popularity](papers/competition-induced-criticality-in-a-model-of-meme-popularity_1305.4328.md)
- (2013-08) [May the Best Meme Win!: New Exploration of Competitive Epidemic Spreading over Arbitrary Multi-Layer Networks](papers/may-the-best-meme-win-new-exploration-of-competitive-epidemic-spreading-over-arbitrary-multi-layer-networks_1308.4880.md)
- (2013-09) [Meme and Variations: A Computer Model of Cultural Evolution](papers/meme-and-variations-a-computer-model-of-cultural-evolution_1309.7524.md)
- (2014-06) [Meme creation and sharing processes: individuals shaping the masses](papers/meme-creation-and-sharing-processes-individuals-shaping-the-masses_1406.7579.md)
- (2016-04) [Sleeping Beauties in Meme Diffusion](papers/sleeping-beauties-in-meme-diffusion_1604.07532.md)
- (2019-02) [A model for meme popularity growth in social networking systems based on biological principle and human interest dynamics](papers/a-model-for-meme-popularity-growth-in-social-networking-systems-based-on-biological-principle-and-human-interest-dynamics_1902.00533.md)
- (2021-01) [Dissecting the Meme Magic: Understanding Indicators of Virality in Image Memes](papers/dissecting-the-meme-magic-understanding-indicators-of-virality-in-image-memes_2101.06535.md)
- (2021-02) [Competition Dynamics in the Meme Ecosystem](papers/competition-dynamics-in-the-meme-ecosystem_2102.03952.md)
- (2022-06) [Diffusion approximation of a network model of meme popularity](papers/diffusion-approximation-of-a-network-model-of-meme-popularity_2206.10960.md)

#### Linguistic and Content Analysis
- (2020-01) [Automatic Discovery of Political Meme Genres with Diverse Appearances](papers/automatic-discovery-of-political-meme-genres-with-diverse-appearances_2001.06122.md)
- (2023-11) [Social Meme-ing: Measuring Linguistic Variation in Memes](papers/social-meme-ing-measuring-linguistic-variation-in-memes_2311.09130.md)
- (2024-07) [Analyzing Persuasive Strategies in Meme Texts: A Fusion of Language Models with Paraphrase Enrichment](papers/Analyzing-Persuasive-Strategies-in-Meme-Texts-A-Fusion-of-Language-Models-with-Paraphrase-Enrichment_2407.01784.md)
- (2024-07) [What Makes a Meme a Meme? Identifying Memes for Memetics-Aware Dataset Creation](papers/What-Makes-a-Meme-a-Meme-Identifying-Memes-for-Memetics-Aware-Dataset-Creation_2407.11861.md)

#### Financial Impact
- (2021-06) [On the "mementum" of Meme Stocks](papers/on-the-mementum-of-meme-stocks_2106.03691.md)
- (2021-10) [Exploring the Endogenous Nature of Meme Stocks Using the Log-Periodic Power Law Model and Confidence Indicator](papers/exploring-the-endogenous-nature-of-meme-stocks-using-the-log-periodic-power-law-model-and-confidence-indicator_2110.06190.md)
- (2022-03) [The echo chamber effect resounds on financial markets: a social media alert system for meme stocks](papers/the-echo-chamber-effect-resounds-on-financial-markets-a-social-media-alert-system-for-meme-stocks_2203.13790.md)

#### Datasets and Tools
- (2022-05) [DisinfoMeme: A Multimodal Dataset for Detecting Meme Intentionally Spreading Out Disinformation](papers/disinfomeme-a-multimodal-dataset-for-detecting-meme-intentionally-spreading-out-disinformation_2205.12617.md)
- (2023-10) [BanglaAbuseMeme: A Dataset for Bengali Abusive Meme Classification](papers/BanglaAbuseMeme-A-Dataset-for-Bengali-Abusive-Meme-Classification_2310.11748.md)
- (2023-12) [MATK: The Meme Analytical Tool Kit](papers/MATK-The-Meme-Analytical-Tool-Kit_2312.06094.md)

## Books 
- (1989) [Professor René Girard Professor Yvonne Freccero The Scapegoat](books/The-Scapegoat_René-Girard-Professor-Yvonne-Freccero_1989.md)
- (1996) [Rene Girard The Girard Reader](books/Rene-Girard_The-Girard-Reader-1996.md)
- (1998) [Darwinizing Culture: The Status of Memetics as a Science, by Robert Aunger](books/Darwinizing-Culture_The-Status-of-Memetics-as-a-Science_Robert-Aunger_1998.md)
- (2002) [The Electric Meme A New Theory Of How We Think Robert Aunger](books/The-Electric-Meme_A-New-Theory-of-How-We-Think_Robert-Aunger_2002.md)
- (2008) [Mimesis And Theory Essays On Literature And Criticism Rene Girard](books/Mimesis-and-Theory_Essays-on-Literature-and-Criticism_Rene-Girard_2008.md)
- (2011) [The Art Of Memetics Edward Wilson Wes Unruh](books/The-Art-of-Memetics_Edward-Wilson-Wes-Unruh_2011.md)
- (2013) [Memes In Digital Culture Limor Shifman](books/Memes-in-Digital-Culture_Limor-Shifman_2013.md)
- (2013) [René Girard's Mimetic Theory (Studies in Violence, Mimesis, and Culture)](books/Studies-in-Violence-Mimesis-and-Culture-Borrud-Gabriel_Girard-René_2013.md)
- (2015) [René Girard And Secular Modernity Christ Culture And Scott Cowdell](books/René-Girard-and-Secular-Modernity_Christ-Culture-and_Scott-Cowdell_2015.md)
- (2016) [Mimetic Contagion Art And Artifice In Terences Eunuch Robert Germany](books/Mimetic-Contagion-Art-and-Artifice-in-Terences-Eunuch-Robert-Germany_2018.md)
- (2016) [Occult Memetics Reality Manipulation Warwick Tarl](books/Occult-Memetics-Reality-Manipulation-Warwick-Tarl_2016.md)
- (2016) [Studies In Violence Mimesis And Culture William A Johnsen The Mimetic Brain](books/Studies-in-violence-mimesis-and-culture-William-A-Johnsen_The-mimetic-brain_2016.md)
- (2016) [The World Made Meme Ryan M Milner](books/The-World-Made-Meme_Ryan-M_Milner_2016.md)
- (2016) [Vicos New Science Of The Intersubjective](books/Vicos-New-Science-of-the-Intersubjective_2016.md)
- (2018) [Evolution of Desire: A life of Rene Girard. Project Muse](books/Evolution-of-Desire-A-Life-of-Rene-Girard_Project-Muse_Girard-RenéHaven-Cynthia-L_2018.md)
- (2018) [René Girard And The Nonviolent God Scott Cowdell](books/René-Girard-and-the-Nonviolent-God-Scott-Cowdell_2018.md)
- (2018) [Spiral Dynamics In Action Practical Application Of Spiral Don Edward Beck](books/Spiral-Dynamics-in-Action_Practical-Application-of-Spiral_Don-Edward-Beck_2018.md)
- (2020) [Robot Memetics A Space Exploration Perspective Walt Truszkowsk](books/Robot-Memetics_A-Space-Exploration-Perspective_Walt-Truszkowsk_2020.md)
- (2020) [Theology Beyond Metaphysics Transformative Semiotics Of René Girard Anthony Bartlett](books/Theology-Beyond-Metaphysics-Transformative-Semiotics-of-René-Girard-Anthony-Bartlett_2020.md)
- (2021) [Luke Burgis Wanting The Power Of Mimetic Desire In Everyday Life](books/Wanting-The-Power-of-Mimetic-Desire-in-Everyday-Life_Luke-Burgis_2021.md)
- (2021) [Philosophys Violent Sacred Heidegger And Nietzsche Through Duane Armitage](books/Philosophys-Violent-Sacred_Heidegger-and-Nietzsche-through_Duane-Armitage_2021.md)
- (2021) [René Girard Theology And Pop Culture Theology Religion Ryan G Duns T Derrick Witherington](books/René-Girard-Theology-and-Pop-Culture-Theology-Religion_Ryan-G_Duns-T_Derrick-Witherington_2021.md)

## Defender's Corner: Culture Science
- [A Beginner's Guide to Culture Science](Defenders-Corner-Substack.md#a-beginners-guide-to-culture-science)
- [Why are we putting up with clickbait?](Defenders-Corner-Substack.md#why-are-we-putting-up-with-clickbait)
- [Blue tribe is starting to win by adopting the best of conservative values](Defenders-Corner-Substack.md#blue-tribe-is-starting-to-win-by-adopting-the-best-of-conservative-values)
- [Can we use Twitter Radar to empirically study \& predict culture?](Defenders-Corner-Substack.md#can-we-use-twitter-radar-to-empirically-study--predict-culture)
- [How to build culture tech](Defenders-Corner-Substack.md#how-to-build-culture-tech)
- [Destigmatize being dumb](Defenders-Corner-Substack.md#destigmatize-being-dumb)
- [Narrative Spears](Defenders-Corner-Substack.md#narrative-spears-)
- ["We've been wrong about math for 2300 years \& I'm here to fix it"](Defenders-Corner-Substack.md#weve-been-wrong-about-math-for-2300-years--im-here-to-fix-it)
- [Feynman's Razor](Defenders-Corner-Substack.md#feynmans-razor-)

