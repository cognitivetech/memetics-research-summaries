# Emotion-Aware Multimodal Fusion for Meme Emotion Detection

[Emotion-Aware Multimodal Fusion for Meme Emotion Detection](https://arxiv.org/html/2403.10279) arxiv.org


**Emotion Detection from Memes**

**Contributions**:
- Introduce MOOD (Meme emOtiOns Dataset) dataset for emotion detection
- Present ALFRED (emotion-Aware muLtimodal Fusion foR Emotion Detection), a multimodal neural framework
- Establish ALFRED's superiority over existing baselines by 4.94% F1 and competitive performance on Memotion task
- Demonstrate ALFRED's domain-agnostic generalizability to two other datasets (HarMeme, Dank Memes)
- Discuss interpretability using attention maps and limitations of current approaches

**ALFRED**:
- Explicitly models emotion-enriched visual cues
- Employs efficient cross-modal fusion via a gating mechanism

**MOOD Dataset**:
- Large-scale multimodal dataset with real memes expressing emotions mapped to six fundamental Ekman emotions
- Benchmarked against unimodal and multimodal systems, reporting class-wise and macro-averaged performances

**Challenges in Meme Emotion Detection**:
- Complex interplay of disparate modality-specific cues
- Implicit background context abstracted by memetic visuals
- Visual-linguistic dissociation and cross-modal noise
- Reasoning complexity induced by implicit contextual cues

**Subjective Perception Problem**:
- Ambiguous data labeling due to subjective perception in social media content analysis
- Efforts needed towards fine-grained analysis of user behavior, decisions, and perceptions encompassing a broader spectrum of emotions.

**Memes: An Emerging Digital Artifact Genre**

**Introduction:**
- Increase in multimodal content on the web sparks innovation
- Fewer studies focus on analyzing memes, their inherent complexity
- Memes contain text and images, require joint interpretation for meaning
- Existing approaches perform better on conventional tasks but struggle with memes

**Memes on Social Media:**
- Ubiquitous digital artifact genre
- Express information sarcastically or humorously
- Potential to understand or sway sentiment and opinion of communities

**Related Work: Multimodal Emotion Detection**
- Well-studied area focusing on various modalities (text, speech, audio)
- Significant emphasis on multimodal emotion detection
- Initial efforts: multi-kernel learning, pooling-based fusion mechanism
- Recent approaches: Transformer-based inter-modality attention, self-supervision

**Related Work: Meme Analysis**
- Addressing challenges from computational and critical discourse perspectives
- Datasets curated for offensiveness, hatefulness, harmfulness
- Variety of tasks addressed: detecting sexism, racism, harmful propaganda
- Community initiatives: Facebook Hateful Meme Challenge, shared-task on detecting hero, villain and victim from memes
- Approaches attempted: ensembling large language models, utilizing meta information, attentive interactions, adaptive loss
- Utility of commonsense knowledge, web entities, racial aspects for detecting offense, harm, hate speech in memes

**Current Study:**
- Address the fundamental aspect of detecting basic emotions of memes.
