# MemeGuard: An LLM and VLM-based Framework for Advancing Content Moderation via Meme Intervention

[MemeGuard: An LLM and VLM-based Framework for Advancing Content Moderation via Meme Intervention](https://arxiv.org/html/2406.05344) ; Work Does Not Relate To Position At Amazon.; arxiv.org


**MemeGuard: A Framework for Meme Intervention**

**Introduction:**
- Unique challenge of memes in digital world for content moderation
- Current research focuses mostly on text-based detection methods
- Need for proactive solutions like intervention

**Contributions:**
1. **MemeGuard framework**: Leverages Large Language Models (LLMs) and Visual Language Models (VLMs) for meme intervention
2. **VLMeme**: A fine-tuned VLM specifically for meme interpretation
3. **Multimodal Knowledge Selection mechanism (MKS)**: Distills relevant knowledge for intervention generation process
4. **General-purpose LLM**: Employs the refined knowledge to generate contextually appropriate interventions
5. **Intervening Cyberbullying in Multimodal Memes (ICMM) dataset**: A high-quality, labeled dataset featuring toxic memes and their corresponding human-annotated interventions

**Stages of MemeGuard:**
1. Developed a meme-aligned VLM (VLMeme) to understand and interpret memes
2. Identified various facets of the meme, such as underlying toxicity, bias, stereotypes, and claims
3. Utilized MKS to retain only relevant knowledge for intervention generation process
4. Generated appropriate interventions using a general-purpose LLM grounded on refined knowledge
5. Tested efficacy through ICMM dataset, demonstrating proficiency in generating effective responses to toxic memes

**Limitations:**
1. Vanilla LLMs and VLMs lack specific knowledge base for task at hand, leading to generic interventions that may not adequately address the content's complexity
2. Struggles with accurately assimilating and analyzing memes due to their unique contextual nature and reliance on shared understanding of internet subcultures
3. Need to filter irrelevant or noisy information before generating interventions

**Background:**
- LLMs and VLMs shown remarkable capability in content moderation, predominantly for detection purposes
- Text and multimedia content understanding through nuanced language and visual cues
- Application in various tasks within the domain of content moderation, including toxicity detection in text and multimodal formats
- Previous attempts at intervention generation have been restricted to text-based content

**Meme Intervention:**
- Represents a proactive approach to content moderation
- Goes beyond simple detection for preventive action against offensive content
- Aims to mitigate harmful effects and foster positive online discourse.

**Meme Analysis:**
- Fast-developing field analyzing harmful elements in memes using computational methods
- Includes hate speech, offensiveness, cyberbullying, stereotypes
- Datasets: Kiela et al. (2020), Pramanick et al. (2021b), Maity et al. (2022), Mathias et al. (2021)
- Recent research focuses on understanding context of memes, such as hateful reasons (Hee et al., 2023) and identifying explanations for memes (Sharma et al., 2023)
- MultiBully-Ex dataset proposed by Jha et al. (2024) for multimodal rationales of code-mixed cyberbullying memes
- Hwang and Shwartz (2023) released a labeled dataset for meme caption generation

**Intervention and Counterspeech Generation:**
- Counterspeech as preferred remedy to combat hate speech, educates perpetrators and upholds free speech principles
- Social intervention effective on social media platforms like Twitter (Wright et al., 2017) and Facebook (Schieb & Preuss, 2016)
- Early datasets: Mathew et al. (2018), Qian et al. (2019), Chung et al. (2019) for expert annotations of counterspeech interventions
- Annotation process time-consuming and costly, taking 6-8 minutes per sample and additional evaluation time
- Honorarium given to annotators based on India's minimum wage standards
- Intervention annotations have high average scores for fluency (4.98), adequacy (4.87), persuasiveness (4.46), informativeness (4.91) (cf. Appendix 3)
- Evaluators achieved unanimous agreement scores of 94.7% for fluency ratings, 89.1% for adequacy ratings, 90.48% for informativeness ratings, and 82.39% for persuasiveness ratings (cf. Appendix A.5)
- Annotation team consisted of two expert annotators working in content moderation and three novice annotators, all computer science undergraduates proficient in Hindi and English.

**Intervention Process:**
- Ten novice annotators hired through department email list and compensated through honorarium
- Provided with 20 diverse expert-annotated interventions, comprehensive guidelines, and training phases to improve performance
- After each phase of training, expert annotators met with novice annotators to discuss poorly rated intervention annotations and renewed the guidelines.

**Challenges:**
- LLMs might deviate from main query, introducing irrelevant context that can distract and hinder effectiveness (Holtzman et al., 2020)
- Proposed filtering strategy: Multimodal Knowledge Selection to maintain intervention process effectiveness.

**Meme Processing Framework**
- Breakdown of a meme:
    - Set of sentences (s1, s2, …, sm) corresponding to specific text fields in the meme
    - Each sentence (si) further broken down into individual sentences using sentence tokenization
        - Sentence set: ks{i} = {s1, s2, …, sm}
- Retaining relevant sentences:
    - Use a pre-trained multimodal model, ImageBind Girdhar et al. (2023), as an encoder-based multimodal model
        - Maps token sequences (text) and images to feature vectors in unified space
    - Cosine similarity is used to measure relevance of each sentence to the image
        - Retain sentences if their cosine similarity with the image's encoding is above a predefined threshold, Th
- Defining retained knowledge sentences:
    - Output from Multi-Headed Attention layer in Vicuna (ZMHA)
    - Output from image adapter layer (ZIA)
        - Linear feed-forward neural network layers: Linear1, Linear2
    - Subsequent fine-tuning on a meme dataset to improve meme understanding abilities

**Contextual Knowledge Generation**
- Utilize VLMeme to generate contextual information about the meme (M)
    - Set of prompts (p0, p1, …, pn) designed for generating diverse contextual information
        - Meme description
        - Bias inherent in the meme
        - Stereotypes propagated by the meme
        - Toxic elements within the meme
        - Assertions and claims conveyed through the meme
- Prompts yield critical insights into meme content
    - VLMeme is used to generate these prompts: ks{i} = VLMeme(pi), where pi is a prompt

**Challenges for Visual Language Models (VLMs)**
- Difficulties handling meme content due to their inherent complexity and cultural connotations
- Augmenting Vicuna language decoder with an image adapter inspired by recent works on efficient NLP model training Houlsby et al. (2019); Yuan et al. (2023)
    - Improves the model's capacity to decipher visual information
- Fine-tuning the enhanced model on a meme caption dataset
    - Imbues the model with a deeper understanding of memes, enabling it to handle nuances and meanings in memes.

**Automatic Evaluation Metrics:**
- ROUGE Lin (2004)
- BLEU Papineni et al. (2002)
- **BLEUavg**: average of BLEU score
- Hmean: harmonic mean of ROUGE-L and BLEU
- **BERTScore** Zhang et al. (2020)

**Human Evaluation:**
- Aspects: Fluency, Adequacy, Persuasiveness
- Qualified evaluators assess generated interventions based on these aspects

**Meme Examples and Interventions:**
1. **A real man... loads the dishwasher every night!! / Girls be named Naina and then have eyes that don’t work** (OCR Text)
   * No claims being made, just a light-hearted moment between a man and a woman
   * No toxicity or hate perceived by evaluators
2. **The meme is spreading the toxicity and hate that men are not interested in doing household chores and that they think it’s the woman’s responsibility** (OCR Text + MiniGPT4)
   * Perpetuates gender stereotypes but no toxicity or hate detected by evaluators
3. **This meme reinforces harmful stereotypes about men and their roles in the household** (MemeGuard)
   * Address underlying stereotypes and promote shared responsibility and respect
4. **We would like to remind everyone that posting toxic memes that perpetuate harmful gender stereotypes is not only hurtful but also damaging to our society** (OCR Text + VLMeme)
   * Encourage inclusive and equal participation in household chores for healthier relationships
5. **It is important to recognize that memes like this reinforce harmful stereotypes and perpetuate biases** (Memeguard Posting Memes)
   * Challenge stereotypes and promote inclusivity and respect

**Interventions:**
- Address underlying stereotypes and promote shared responsibility and respect in domestic relationships
- Encourage inclusive and equal participation in household chores for healthier and more balanced relationships
- Treat others with kindness and empathy, recognizing the diversity and beauty of all individuals.

**Enhancements from VLMeme over MiniGPT4:**
- **FLAN-T5**, **GPT3.5-Turbo**, and **Dolly**: pronounced enhancements in Hmean and BERTScore due to VLMeme's ability to generate more contextually relevant knowledge about memes than MiniGPT4.
- Suggests: effectiveness of domain-specific fine-tuning for vision-language models.

**Performance Analysis of VLMeme:**
- **MemeGuard framework** utilizing MKS over VLMeme outperforms baselines across all automatic evaluation metrics, enhancing in-context learning for these LLMs.
- Models using MemeGuard: Dolly, LLaMA, RedPajamas, FLAN, and GPT3.5-Turbo.
- Averaged BLEU scores: 9.86 (Dolly), 19.31 (LLaMA), 18.50 (RedPajamas), 24.63 (FLAN), 25.37 (GPT3.5-Turbo).
- BERTScores: 82.27 (Dolly), 80.11 (LLaMA), 83.42 (RedPajamas), 87.21 (FLAN), 89.02 (GPT3.5-Turbo).
- FLAN-T5 and GPT3.5-Turbo outshine other models in ROUGE, BLEU, and BERTScore metrics but only achieve low N-gram matching scores (Hmean: 15.41 for FLAN-T5, 19.03 for GPT3.5-Turbo).
- Despite this, their BERTScores remain fairly high, suggesting generated interventions convey similar meanings as ground truth despite varying word choice.

**Human Evaluation:**
- Outlined in Section A.1.

---

Thank you to arXiv for use of its open access interoperability.