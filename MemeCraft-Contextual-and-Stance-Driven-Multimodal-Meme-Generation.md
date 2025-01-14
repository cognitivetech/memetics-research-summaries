# MemeCraft: Contextual and Stance-Driven Multimodal Meme Generation

[MemeCraft: Contextual and Stance-Driven Multimodal Meme Generation](https://arxiv.org/html/2403.14652) arxiv.org


**MemeCraft: An Innovative Meme Generator Using Large Language Models and Visual Language Models**

**Online Memes**:
- Emerged as powerful digital cultural artifacts in the age of social media
- Offer humor, platforms for political discourse, social critique, and information dissemination
- Extensive reach and influence in shaping online communities' sentiments

**Challenges**:
- Gap in systematic evaluation and ability to effectively communicate ideologies in existing meme generation tools

**MemeCraft Overview**:
- Leverages large language models (LLMs) and visual language models (VLMs) to produce memes advocating specific social movements
- End-to-end pipeline that transforms user prompts into compelling multimodal memes without manual intervention
- Intrinsic safety mechanism to curb hateful meme production

**Evaluation**:
- Assessment focuses on two UN Sustainable Development Goals: Climate Action and Gender Equality
- Shows MemeCraft's prowess in creating funny and supportive memes for advocacy goals

**Contributions**:
- Highlights how generative AI can promote social good
- Pioneers the use of LLMs and VLMs in meme generation

**Memes**:
- Typically comprised of images, videos, or text that convey humor, irony, or satire
- Can disseminate rapidly and achieve viral status, shaping collective sentiments
- Can serve as conduits for political discourse, social critique, and information dissemination

**Meme Generation Tools**:
- Semi-automated tools offer text overlay on pre-existing meme templates
- Require extensive training with large datasets
- Existing evaluations primarily assess resemblance to manually crafted memes

**MemeCraft Approach**:
- Leverages LLMs and VLMs effectively with few demonstration memes, reducing training costs
- Generates multimodal memes from specially designed prompts that advocate social causes
- Automatically generates text overlays to convert images into humorous memes

**Safety Mechanism**:
- Ensures MemeCraft does not produce hateful memes, maintaining a platform free from abusive or offensive content

**Study Overview**
- Evaluation of MemeCraft as a social campaigning tool using LLMs or VLMs for meme generation
- Dataset: Two UN Sustainable Development Goals ("Climate Action" and "Gender Equality")
- Human evaluation on four primary factors: authenticity, hilarity, message conveyance, persuasiveness
- Assessment of safety mechanism against hateful content

**Contributions**
1. Introduced MemeCraft: innovative meme generator using LLMs or VLMs for large-scale advocacy memes
2. Conducted extensive human evaluation on generated memes' effectiveness in promoting social movements
3. Results showed that MemeCraft outperformed state-of-the-art meme generators in generating humorous and persuasive memes for social campaigns
4. Demonstrated potential of leveraging generative AI to promote social good

**Related Work**
2.1. **Meme Analysis and Generation**: extensive research on analyzing topics, semantics, emotions conveyed in memes; detection of hateful memes crucial for preventing harmful messages, misinformation, propaganda.
- Dank Learning approach using Inception V3 architecture and attention-driven LSTM for decoding meme captions (Peirson & Tolunay)
- MemeBot and Memeify incorporating text input and transformer-based architectures (Sadasivam et al. & Vyalla & Udandarao)
- Evaluation metrics: differentiability, user satisfaction, humor quotient
5. Large Language Models (LLMs): GPT-3, T5, BLOOM; ability to perform well on novel tasks with zero-shot in-context learning.
6. **Large Vision-Language Models (VLMs)**: robust generative abilities and superior performance in multimodal understanding tasks (Ye et al., Dai et al., Liu et al., Zhu et al., Li et al.).
7. Previous research provided valuable insights into meme generation methodologies; MemeCraft introduces a novel model employing LLMs/VLMs for humorous memes at scale to advocate social causes.

**MemeCraft Framework Overview**

**Components:**
- **Meme Template Image Sampling**:
  - Collecting meme templates using datasets and APIs
  - Retrieving blank image URLs for text overlay
- **Image Description Generation**:
  - Utilizing a state-of-the-art VLM (LLaVA-7B) to generate high-quality image descriptions
  - Ensuring detailed captions align with visual content

**Meme Text Generation:**
- Goal: Create memes that convey campaign messages for specific social causes
- Parameters: Social cause, stance, persuasion technique
- Generating text based on user-defined parameters and randomly selected templates
- Employing a prefix to encourage stronger connections between image and meme text
- Three models used: ChatGPT-3.5, LLaMA-2-13B, LLaVA-7B
  - LLMs use few-shots prompting technique (N = 4 demonstration examples)
  - VLM employs zero-shot prompting method

**MemeCraft: Hateful Memes Detection and Dataset Generation**

**Instructions:**
- Aligns with template in Table 1 (Instruction, Input, Output) but excludes demonstration samples
- "Let's think step-by-step" prefix from output
- Enhanced with safety mechanism for hateful memes detection using MultiModal BiTransformers (MMBT-Grid) model:
  * Utilizes multimodal supervised bitransformer architecture
  * Trained on Hateful Meme Challenge (HMC) Dataset, a benchmark for identifying hateful content
  * High confidence threshold of 0.9 to classify content as hateful and exclude it from final dataset
- Process of generating a dataset focusing on "climate action" and "gender equality":
  * Designed prompts with persuasion techniques (Causes, Consequences, Solutions, Evidence of Absence, Benefits, Rationale) for each social cause
  * Generated memes using three variations of MemeCraft: ChatGPT, LLaMA, and LLaVA
  - Produced a total of 3,000 memes (including Dank Learning and random online memes for comparison)

**Dataset Generation:**
| Social Cause | Model Used   | Memes Generated |
| :----------- | :----------: | :------------: |
| Climate Action | ChatGPT, LLaMA, LLaVA | 100 x each |
| Gender Equality | ChatGPT, LLaMA, LLaVA | 100 x each |
| Total          | -         | 500 x each   |

**Human Evaluation:**
- Recruited a group of 12 undergraduate students familiar with online meme culture as evaluators
- Each meme assessed by at least two evaluators, average rating recorded to represent consensus
- Five evaluation metrics developed: Authencity, Hilarity, Message Conveyance, Persuasiveness, and Hatefulness.

**Authenticity Metric:**
- **Gauges resemblance of generated memes to online content**
- Evaluators determine if a meme looks like those found on the internet, "yes" or "no"
- Score is the percentage of memes rated as authentic (Yes)

**Hilarity Metric:**
- **Evaluates humor in generated memes**
- 5-point scale: Not humorous (1), Humorous (5)
- MemeCraft-ChatGPT outperforms other models and baselines, achieving a median hilarity score of 3 for both social causes.

**Message Conveyance Metric:**
- **Evaluates memes' ability to convey intended message**
- Categorized as "support", "deny", or no clear alignment (NA) with the specified social cause
- Message Conveyance score is percentage of memes that conveyed the social cause and stance correctly.

**Persuasiveness Metric:**
- **Measures persuasive quality of generated memes**
- Evaluators rate memes on a scale from 1 to 5, Not persuasive (1), Persuasive (5)
- Results shown in Table 4.

**Hatefulness Metric:**
- **Assesses effectiveness of safety mechanism in mitigating hateful meme generation**
- Safety mechanism classifies generated memes as hateful or non-hateful and filters out the hateful ones
- Two scores reported: percentage of hateful memes identified by machine (safety mechanism), and percentage identified by evaluators.

**Authenticity Scores:**
- Table 3 shows average authenticity scores for various models, including MemeCraft variations and baselines
- MemeCraft-ChatGPT outperforms smaller models in terms of authenticity score (0.48-0.53)
- Differences between social causes could be due to richness of content available or complexity of topic.

**Hilarity Distribution:**
- Figure 3 shows distribution of hilarity scores across different social causes and meme generation models
- MemeCraft-ChatGPT achieves a median hilarity score of 3, indicating moderate humor in generated memes.

**Message Conveyance Results:**
- Table 4 presents message conveyance scores for memes created using supportive and denied persuasion techniques.
- Notable differences observed among various persuasion strategies when evaluating memes that support social causes.

**Meme Generation and Analysis: Effectiveness of Various Techniques**

**Overview:**
- Study evaluates memes generated using different techniques for two social causes: climate action and gender equality.
- MemeCraft-ChatGPT outperforms other models in both causes, with around 40% of memes receiving a rating of 3 out of 5 persuasiveness score.
- Supportive techniques tend to perform better for the "climate action" social cause.
- Gender equality has less pronounced disparity between support and deny persuasion techniques.

**Technique: Causes**
- Most effective technique, yielding approximately 0.7 supportive memes with MemeCraft-ChatGPT and MemeCraft-LLaMA.
- About 70% of generated memes are evaluated as supporting the social cause.

**Persuasion Strategies: Support vs Deny**
- Supportive strategies registered efficacy scores exceeding 0.6 with MemeCraft-ChatGPT.
- Persuasion strategies designed to deny social causes produced approximately 30% of memes that still advocated for the cause.
- Memes utilizing supportive persuasion techniques rarely adopted an opposing viewpoint, with only approximately 10% doing so.
- The efficacy of various denied persuasion techniques generally yielded a low conversion to contrarian memes.
- A significant outlier was observed with "Evidence of Absence" technique in the context of the "climate action" social cause when applied in MemeCraft-LLaMA, where 76% of generated memes opposed the cause. This anomaly was attributed to the model's replication of patterns from provided demonstration examples during the meme generation process.

**Persuasiveness and Social Causes:**
- Memes demonstrate moderate persuasive impact.
- The persuasiveness scores are notably influenced by social causes and persuasion techniques used.
- Tailoring persuasion techniques to specific social causes is crucial for enhancing the persuasive impact of memes.

**Hatefulness:**
- Our safety mechanism detected a markedly higher proportion of hateful memes in gender equality compared to climate action, highlighting the risk for LLMs to propagate hate speech.
- After applying the safety mechanism, we found that the percentage of hateful memes in both social causes consistently remained below 0.05, which is lower than two baselines.
- Memes generated by various models with their Authenticity (A), Meme Hilarity (M-H), Message Conveyance (M), Persuasiveness (P), and Hatefulness (H) scores are presented in Table 6 for clarity in results. High-quality memes typically demonstrate a seamless integration of text and imagery, which together produce humor and a coherent message.

**Meme Analysis: Understanding Quality vs. Low-Quality Memes**

**Drake's Rejection of Gender Stereotypes as a Prime Example (Meme 2)**
- Satirizes rejection of outdated gender stereotypes
- High-quality meme

**Factors Contributing to Low-Quality Memes**
1. **Lack of Semantic Connection between Text and Image (Memes 5 & 6)**
   - Individual meaning but unclear relationship with visual element
2. **Nonsensical Textual Content (Meme 7)**
   - Fails to convey coherent messages
3. **Sensitive Topics: Risk of Being Labeled Hateful (Meme 8)**
   - Downplaying historical involvement of some groups in sensitive issues
   - Potential for undermining credibility

**Conclusion:**
- **MemeCraft generator**: Noteworthy advancement in automated meme creation
- Capable of producing contextually relevant and offensive-free memes
- Achieved satisfactory metrics in persuasiveness and hilarity
- Room for improvement to achieve humor scores comparable to real online memes
- Future works aim: Refine synergy between textual and visual elements, contributing to progressive evolution of meme generation technology.
