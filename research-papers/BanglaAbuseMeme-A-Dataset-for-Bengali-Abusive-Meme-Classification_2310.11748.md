# BanglaAbuseMeme: A Dataset for Bengali Abusive Meme Classification

[BanglaAbuseMeme: A Dataset for Bengali Abusive Meme Classification](https://arxiv.org/html/2310.11748) arxiv.org


**Bengali Meme Dataset for Abusive Memes Detection**
- **Background:**
  - Dramatic increase in use of social media platforms for information sharing
  - Steep growth in online abuse, including abusive memes (images with text)
  - Need to develop efficient models to detect and flag abusive memes
- **Challenges:**
  - Absence of benchmark datasets for low-resource settings like Bengali memes
- **Contributions:**
  - Building a Bengali meme dataset (BanglaAbuseMeme) with 4,043 instances: 1,515 abusive, rest non-abusive
  - Annotations include vulgarity, sarcasm, sentiment (positive/negative/neutral), and targeted community
- **Importance:**
  - Overcoming limitations of previous studies on English language abusive memes detection
  - Bengali is the seventh most spoken language with over 210 million speakers
  - Important due to online incidents of slandering, anti-religious propaganda, and cyber harassment in Bangladesh and India.

**Abusive Meme Dataset Creation (2021)**
- Researchers created a dataset of 743 memes labeled as offensive or not-offensive
- Memes related to the 2016 US presidential election were used

**Hateful Memes Challenge (2020)**
- Facebook AI introduced a dataset of over 10,000+ posts labeled as hateful and non-hateful
- The Hateful Memes Challenge also includes a dataset of 3.5K memes related to COVID-19

**Bengali Meme Detection**
- Two previous works on Bengali meme detection: Karim et al. (2020) and Hossain et al. (2022)
- Both studies extended existing datasets by labeling 4,500 and 4,158 memes with Bengali captions
- Data collection and annotation process not detailed in both studies

**Dataset Creation: Offensive Memes Dataset**
- Researchers built a lexicon of 69 offensive Bengali terms
- Performed keyword-based web searches on various platforms to extract memes containing these terms
- Applied data sampling techniques before annotation
- Annotated by 5 undergraduate students supervised by a Ph.D. student
- Memes labeled based on abusiveness, target communities (if any), vulgarity, sarcasm, and sentiment

**Annotation Codebook and Procedure**
- Developed a comprehensive annotation codebook to ensure consistent labeling
- Conducted multiple training sessions for annotators using the codebook
- Evaluated trial annotations by consulting with annotators regarding incorrect labels
- Main annotation task using Label Studio tool on Heroku instance.

**Data Annotation Process**
- Three independent annotators labeled memes based on guidelines
- Majority voting determined final labels
- Initial batch: 100 memes, expanded to 500
- Discussed errors for agreement preservation
- Provided breaks and weekly meetings for annotators' mental health
- Dataset: 4,043 Bengali memes; 1,515 abusive, 2,528 non-abusive
- Further labeling: sarcastic (1,664), vulgar (1,171)
- Sentiment analysis: positive (592), neutral (1,414), negative (2,037)
- Inter-annotator agreement: 0.799, 0.801, 0.67, 0.72 using Fleiss’ kappa score

**Meme Text Analysis**
- Distribution of word length: Figure 3 (histogram of meme texts' average number of words)
  * Both abusive and non-abusive follow similar distribution
  * Most memes have lengths between 10 and 15 words
- Top 10 most frequent words per class before removing stop words using BNLP library
  * Abusive: Ghoti, Bangal, Hindu, etc.
    + Hateful words like 'Malaun', 'Kangladeshi'
  * Non-abusive: Negative emotion (negemo), giving, achievement, fun
- Empath analysis using Empath to identify important lexical categories
  * Abusive memes scored high in hate, crime, suffering, fight, war and weapon categories
  * Non-abusive memes scored higher on negative emotion, giving, achievement and fun

**Text Analysis Tools Used:** BNLP library, Empath.


---

Thank you to arXiv for use of its open access interoperability.