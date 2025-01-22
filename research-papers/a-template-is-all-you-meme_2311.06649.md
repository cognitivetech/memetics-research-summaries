# A Template Is All You Meme

[A Template Is All You Meme](https://arxiv.org/abs/2311.06649)

## Table of Contents

- [A Template Is All You Meme](#a-template-is-all-you-meme)
- [A Template Is All You Meme](#a-template-is-all-you-meme)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 The Know Your Meme Knowledge Base](#3-the-know-your-meme-knowledge-base)
- [4 Template-Meme Analysis](#4-template-meme-analysis)
- [5 Template-Label Counter](#5-template-label-counter)
- [6 Classification Experiments](#6-classification-experiments)
- [6.1 Results and Discussion](#61-results-and-discussion)
- [7 What’s in a Meme?](#7-whats-in-a-meme)
- [8 Conclusion and Future Work](#8-conclusion-and-future-work)
- [9 Limitations](#9-limitations)
- [A.2 Scraping details](#a2-scraping-details)
- [A.3 More template-meme analysis](#a3-more-template-meme-analysis)
- [A.4 Meme “edge cases”](#a4-meme-edge-cases)
- [A.5 Template-Label](#a5-template-label)
- [A.6 Dataset information](#a6-dataset-information)
- [A.7 Additional classification results](#a7-additional-classification-results)- [A Template Is All You Meme](#a-template-is-all-you-meme-1)
- [1 Introduction](#1-introduction)
- [2 Related Work](#2-related-work)
- [3 The Know Your Meme Knowledge Base](#3-the-know-your-meme-knowledge-base)
- [4 Template-Meme Analysis](#4-template-meme-analysis)
- [5 Template-Label Counter](#5-template-label-counter)
- [6 Classification Experiments](#6-classification-experiments)
	- [6.1 Results and Discussion](#61-results-and-discussion)
- [7 What’s in a Meme?](#7-whats-in-a-meme)
- [8 Conclusion and Future Work](#8-conclusion-and-future-work)
- [9 Limitations](#9-limitations)
	- [A.2 Scraping details](#a2-scraping-details)
	- [A.3 More template-meme analysis](#a3-more-template-meme-analysis)
	- [A.4 Meme “edge cases”](#a4-meme-edge-cases)
	- [A.5 Template-Label](#a5-template-label)
	- [A.6 Dataset information](#a6-dataset-information)
	- [A.7 Additional classification results](#a7-additional-classification-results)

## A Template Is All You Meme

**Meme Analysis using Meme Templates**

**Introduction**:
- Memes are a modern form of communication
- Meme templates have a base semantics that can be customized
- Machine learning systems struggle to understand memes due to insufficient context

**Know Your Meme Knowledge Base (KYMKB)**:
- Released to aid understanding of memes
- Includes over 54,000 images from knowyourmeme.com
- Contains popular meme templates, examples, and detailed information

**Hypothesis**:
- Meme templates can be used to inject models with missing context
- **Template-Label Counter (TLC)** classifier developed to test this hypothesis

**Experiments and Results**:
- Thorough classification experiments and data analysis in the context of 5 meme analysis tasks
- TLC found to be more effective or competitive with fine-tuned baselines

**Cautionary Note**:
- Some memes discussed may be offensive, but do not reflect the authors' views.


## 1 Introduction

**Memes: Understanding Templatic Memes**

**Introduction:**
- Memes as modern form of communication
- AI research community treats memes as static images with text
- Disclaimer on ethical use for academic purposes only

**Meme Definitions:**
- Unit of cultural transmission or imitation and replication (Dawkins, 1976)
- Reference to a cultural moment shared by a group of people
- Inherent basis in Internet culture with sociolinguistic traits
- Meaning obfuscated for in-group communication

**Meme Templates:**
- Common patterns or elements used to create novel memes
- Difficult to parse due to various combinations and unique meanings
- Reference to a meme template, commonly reused material (text, images, audio)
- Importance of recognizing both entities in the meme and the template for interpretation

**Know Your Meme (KYM):**
- Internet Meme Database
- Valuable resource for information on templatic memes
- Provides base template image and examples of usage
- Helps users learn how to interpret and use templates

**Memes in Machine Learning:**
- Growing interest due to learning problem and spread of harmful content
- Humor increases persuasiveness, important to prevent harmful memes
- Previous work focuses on fine-tuning large multimodal models on image and text

**Contributions:**
1. Release of Know Your Meme Knowledge Base (KYMKB) with 54,000 meme-related images and information
2. Proposal of Template-Label Counter (TLC), an efficient, majority-based classifier for templatic memes
3. Extensive study on five meme analysis tasks to demonstrate the potential of using templatic memes as contextual grounding for meme understanding.


## 2 Related Work

**Related Work on Analyzing Memes**

**MultiOFF (Suryawanshi et al., 2020)**:
- Dataset of offensive memes related to the 2016 US presidential election

**FigMemes (Liu et al., 2022)**:
- Scraped images from a politically incorrect and infamous board on 4chan, /pol/
- Labeled over five thousand memes with six different types of figurative language used in the meme

**Memotion3 (Mishra et al., 2023)**:
- Composed of memes in Hindi and English, labeled for sentiment, emotion detection (including offensiveness/hatefulness), and emotion intensity

**MEMEX (Sharma et al., 2023)**:
- Created a new dataset and task by creating meme-explanation (a document) pairs
- Used Wikipedia and Quora to assemble explanation documents and create a novel multimodal model
- Uses meme external information (Wikipedia/Quora), but not meme knowledge

**Tommasini et al. (2023)**:
- Developed software for creating a knowledge graph of memes by scraping and querying different sources of information
- Makes no attempt to leverage the graph in a downstream task or provide demonstrations

**Differences from the Above Work**:
- First work to specifically exploit meme templates and distinguish between templatic and non-templatic memes
- KYMKB is much larger (54,000 images) than other datasets
- Provides detailed, general information about templatic memes, not just for a specific task
- Performs inference with a multimodal model (CLIP), but does not rely on graphs to connect or ground memes
- Uses a distance-based lookup to find the most likely template and choose the most frequent label for a novel meme
- Provides meme-specific context, rather than querying potentially unrelated knowledge sources


## 3 The Know Your Meme Knowledge Base

**Know Your Meme (KYM)**
- **Internet Meme Database**: Wiki-like platform for creating and documenting meme entries
- Users create entries with template and information about origin, meaning, usage
- Entries reviewed and approved by community, can be updated as meme evolves
- **Template instances** important for understanding memes
  - Can be altered with text and images to fit specific semantics
- Existing approaches rely on Optical Character Recognition (OCR) to extract text/named entities
  - Not effective when entities are images referencing YouTube videos

**KYM Knowledge Base (KYMKB)**
- Collection of meme templates, examples, and usage details
- Ensures quality by crawling approved KYM entries
  - 5,220 base templates, 49,531 examples (total 54,751 images)
- Organized for easy access to related templates, info, and examples
- All textual data linked to a template in JSON file with local location
- Average of 9.49 examples per template.


## 4 Template-Meme Analysis

**Template-Meme Analysis**

**Hypothesis**:
- Retrieval-based methods should match base template to memes in the wild
- Allows access to information about a novel meme by considering text connected to the base template

**Experiment**:
- Fit nearest neighbor lookup on encoded template images in knowledge base (KYMKB)
- Query it on 5 existing meme classification tasks
- Manually inspect similarities
- Use CLIP as encoder

**Results**:
- **39.2%**: Memes are base templates or distorted/cropped versions
- **15.2%**: Instances of templates tuned by 4chan poster
- **16.8%**: KYMKB matches non-template images
- **7th column**: Anime template "You Get Used To It" matched to an image not believed to be that template
- **28.8%**: Matched templates despite different appearances

**Examples**:
- Pepe the Frog: KYMKB includes various versions, even in alt-right contexts
- SpongeBob and Angry Pepe: Templatic concepts merged into a single meme expressing derision in the "alt-right" domain.


## 5 Template-Label Counter

**Template-Label Counter (TLC) Pipeline**

**Hypothesis**:
- KYM memes are composed of popular template instances from the KYM Knowledge Base (KYMKB)
- Meme datasets are customized versions of these templates
- Labels assigned to memes in a dataset reflect their semantics

**Step 1: Encode Template Knowledge**
- Use CLIP encoding and nearest neighbor indexing for template representation
- Set up a reference (ref=CLIP(XKYMKB))

**Step 2: Learn Dataset Knowledge**
- Encode training data (query train=CLIP(Xtrain))
- Query neighbor index to obtain closest template and record label
- Reduce each template index to its most frequent label

**Step 3: Test Meme and Dataset Knowledge**
- Encode test data (query test=CLIP(Xtest))
- Perform nearest neighbor lookup
- Assign the most frequent label from the training data or the template itself to a novel instance

**Hyperparameters**:
- Ignore meme and match OCR text to about section of templates
- Consider base template, examples, or both for encoding meme knowledge
- Use multiple neighbors and select most common template/label
- Experiment with different CLIP versions and modalities (text, image)
- Combine modalities via concatenation, Hadamard product, or average.


## 6 Classification Experiments

**Classification Experiments**

**Testing TLC against Meme Tasks**:
- Tested TLC against results from 5 meme tasks:
    - **FigMemes**
    - **MultiOff**
    - **MEMEX**
    - **Memotion 3**: Task A and B
- **Table 1**: Summary of datasets and tasks

**Dataset Sizes**:
- Provided same number of data points as reported in relevant work
- Not always used the same data in analysis:
    - **Memotion 3**: Used training and validation splits, not test split (labels not publicly available)
    - **MEMEX**: Only considered training and test splits (validation split not publicly available)

**Baselines and Setup**:
- **Baseline Model**: Majority class from the training split for each task
    - When test split is unavailable, evaluated on validation split instead
- **Evaluation Measures**: Computed using **scikit-learn**


### 6.1 Results and Discussion

**TLC Results and Discussion**
* **Table 2**: Shows TLC's results compared to fine-tuned methods for various tasks
	+ Best performing version of TLC vs embedding text, encoding templates, templates and examples
	+ Previous work results: text only, vision only, vision + text
	+ Majority class performance as baseline
* **TLC Performance Improvements**: Consistently improves with addition of more modalities (OCR text, template images)
* **Multimodal Representation**: Strongest TLC configuration for concatenating image and text modalities
* **Neighbor Search**: Improves performance in cases where templates and examples are considered
	+ Up to five neighbors in the KYMKB for estimating novel meme template
* **Counting Templates**: Ineffective for TLC due to difficulty of determining meaning from a picture, not a meme
* **MEMEX Approach**: Creates new task with meme and explanation pair, but cannot be applied to novel memes without context
* **TLC Limitations**: Overfits to majority class, unable to interpret novel templates or understand meme's nuanced meaning.
* **Goal of the Work**: Not creating a state-of-the-art meme classifier but a resource for furthering meme understanding and adding template knowledge to literature.
* **Template Signal Neglect**: TLC takes advantage of leaked information by exploiting templates in training data, which should be carefully considered when constructing meme datasets.

## 7 What’s in a Meme?

**Understanding Meme Concepts: The KYMKB**

**Memes Beyond Images**:
- Memes are not just images with text
- Examples: Leeroy Jenkins template, audio/video memes
- Longevity of popular templates (Leeroy Jenkins referenced for almost 20 years)

**Expanding the Definition of Meme**:
- Examples include audio and video memes
- Evidence from popular YouTube videos with millions of views

**Limitations of Current Literature**:
- Narrow focus on image-based memes
- TLC relies on the concept of memes as images for classification
- The KYMKB provides a wealth of knowledge to understand and create systems capable of interpreting all types of memes.


## 8 Conclusion and Future Work

**Conclusion and Future Work**
- Introduced **Know Your Meme Knowledge Base (KYMKB)**: composed of over 54,000 images and 5,200 base templates with detailed information about each template
- Demonstrated the power of **templatic memes and their semantics** through detailed exploratory data analysis
- Proposed **Template-Label Counter (TLC)**: an inexpensive, majority-based classifier competitive with more expensive methods
- Asserted that considering **meme templates** is necessary when creating meme datasets to understand the nuances of memes
- Plans to use the KYMKB to explore **categorizations and develop a taxonomy of memes** to aid the development of meme-aware systems
- Believes the **large language models (LLMs)**'s ability to understand memes remains untested, and the KYMKB makes it possible to examine LLM meme understanding in a systematic manner.

**Acknowledgments**:
- Gratitude to Tobin Bates, Max Glockner, Derek Hommel, Timour Igamberdiev for inspiring discussions
- Acknowledges the support of:
  - **German Federal Ministry of Education and Research (BMBF)** under the project "MISRIK"
  - **Hessian Ministry of Science and the Arts (HMWK)** within the projects "hessian.AI" and "National Research Center for Applied Cybersecurity ATHENE"
  - **Pioneer Centre for AI**, DNRF grant number P1.


## 9 Limitations

**KYM and Limitations:**

* KYM: Best resource for meme knowledge but not the only one.
* Not all meme posters agree on interpretation of templates or memes.
* Determining templateness is complex, not all memes are templatic.
* A.1 Non-Templatic Memes:
  * Not all memes follow a template.
  * Determining templateness can be difficult.


### A.2 Scraping details

**Scraping Details**

* Use Wayback Machine (WM) to adhere to KYM's terms of use.
* WM snapshots are incomplete; only 5,220 out of 8,400 confirmed entries scraped.
* Passionate about memes and committed to making the KYM Knowledge Base complete.
* Releasing all scraping code and updating it regularly.

**References:**

* Know Your Meme (KYM)
* Wayback Machine (WM)
* terms-of-service
* youtube.com/watch?v=33O7jg50FjE
* cheezburger.com
* knowyourmeme.com/memes/doggo
* knowyourmeme.com/memes/sites/
* knowyourmeme.com/memes/people/donald-trump


### A.3 More template-meme analysis

**Template-Meme Analysis: Retrieval Method**

**Background**
- KYMKB (know your meme knowledge base) templates matched to FigMemes images for analysis
- Random selection of kpairs, where k is the number of labels in a dataset
- Concerned with FigMemes as it has most labels and is difficult dataset

**Findings**
- Combining embeddings via fusion or normalizing/averaging results in nuanced or non-existent relations between templates and memes
- Keeping modalities separate or concatenating image and text representations produces strongest signal for retrieval
- Matches base template to obvious instances of that template or text/characters related to meme culture

**Examples**
1. **Wojak in I Support the Current Thing meme template**: matches character in social media criticism meme
2. **White Knight template**: matches image deriding White Knight concept
3. **/pol/ template**: matches 4chan board-related meme

**Clustering Analysis**
- Investigate saliency of templatic memes using KMeans clustering on KYMKB and FigMemes datasets
- Encoding all memes using CLIP embeddings
- Manually examine closest meme or template to each centroid

**Results**
- Combining image and text embeddings often results in repeated images
- Concatenating embeddings or only using images representation leaves distinct image files as centroids
- Centroids from KYMKB reflect the nature of FigMemes dataset, expressing toxic rhetoric and conservative beliefs
- Centroids from FigMemes dataset also reflect dataset's nature, expressing derision, sexism, and political beliefs
- One meme centroid is closest to same template in both cases: Is He /Our Guy/? template (4chan celebrity belief confirmation).


### A.4 Meme “edge cases”

**Meme "Edge Cases"**

**Rickroll**:
- Oldest meme template
- Involves posting image of Rick Astley from music video
- More common: bait-and-switch prank to trick others into viewing the music video

**Loss**:
- Template referencing Ctrl+Alt+Del Comic gamming webcomic
- Users mockingly posted references to panel as a joke, bringing it to meme status
- Template includes various character arrangements from comic strip

**Planking**:
- Behavior where a person lies flat on their stomach with arms to sides in unusual place
- Has photo taken and uploaded for amusement of others

**Thinking Face Emoji**:
- Instance could be ironically or sarcastically posting thinking face emoji
- Or using Unicode "U+1F914" or posting picture of emoticon for extra emphasis

**OOF / Roblox Death Sound**:
- Recent meme template without image
- Involves featuring or remixing audio clip in videos or music
- Referenced to suggest empathy for another's misfortune and shared experience, popular among Roblox players.


### A.5 Template-Label

**Template-Label Counter (TLC)**

**Multiple Voting Methods**:
- **Template vote**: Consider multiple templates and take their most common label
- **Label vote**: Keep all labels for a given template and reduce to the most frequent

**Late Fusion Implementation**:
- Combine labels from both the template and its context, find the most common
- If a template is not in the training data, use the most frequent label in the training split

**Performance Observations**:
- Text representations are not as strong as image representations
- Voting independently and then aggregating weakens image performance
- TLC templates is competitive with other multi-modal methods but less expensive

**Comparison to Other Models**:
- **BERT**: Fine-tuning yielded a macro-averaged f1 of 32.62, which TLC templates is competitive with
- Table 3 from the study shows great variation, demonstrating the task's difficulty


### A.6 Dataset information

**Dataset Information**

**MultiOff**:
- Binary classification task: offensive (40%) vs. not offensive (60%)
- Reported Fleiss Kappas before and after feedback:
  - Before feedback: fair agreement (0.2-0.3)
  - After feedback: moderate agreement (0.4-0.5)

**Memotion 3**:
- Composed of two multilabel tasks, A and B
- Task A: sentiment analysis for memes
  - Labels: very positive (5%), positive (26%), neutral (42%), negative (23%), very negative (5%)
  - Inter-annotator agreement scores not reported
  - Settling disagreements via majority vote
- Task B: memes with humorous, sarcastic, offensive, or motivational messages
  - Labels: humorous (39%), sarcastic (37%), offensive (19%), motivational (5%)
  - Inter-annotator agreement scores not reported

**FigMemes**:
- Multilabel task of determining the type of figurative language used in a meme
- Labels: Allusion (17%), Exaggeration (19%), Irony (20%), Anthropomorphism (9%), Metaphor (20%), Contrast (10%), None (30%)
- Reported Fleiss Kappa of 0.42, indicating moderate agreement

**MEMEX**:
- Binary task: baseless (30%) vs. valid (70%)
- First stage of annotation reported Cohen's Kappa of 0.55, moderate agreement
- Second stage of annotation reported Cohen's Kappa of 0.72, substantial agreement
- Validation split not publicly available at time of writing


### A.7 Additional classification results

**Additional Classification Results**

**Modality Combinations**:
- Keeping modalities separate: Table 3
- Concatenating embeddings: Table 4
- Fusing via Hadamard product: Table 5
- Normalizing and averaging: -

**Performance per Encoder**:
- ViT-L/14@336px: Strongest performer, but exceptions (e.g., Memotion 3 (A) and (B))
- ViT-B/32: Best backbone for Memotion 3 (B)
- ViT-B/16: Best backbone for MultiOff

**Neighbor Voting**:
- Improves final prediction only when considering both templates and instances
- Intuitive finding due to similar templates conveying broad semantics and noisy instance combinations

**Evaluation Measures**:
- Computed using scikit-learn, set zero division to avoid undefined f1 scores
- Possible inflated weighted/macro averages if no predictions are made for a label


---

Thank you to arXiv for use of its open access interoperability.