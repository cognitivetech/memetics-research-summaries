# Dissecting the Meme Magic: Understanding Indicators of Virality in Image Memes

[Dissecting the Meme Magic: Understanding Indicators of Virality in Image Memes](https://arxiv.org/abs/2101.06535)

## Table of Contents
- [Table of Contents](#table-of-contents)
- [1 Introduction](#1-introduction)
- [2 Background and Related Work](#2-background-and-related-work)
	- [2.1 Memes](#21-memes)
	- [2.2 Why and How Do People Share Memes?](#22-why-and-how-do-people-share-memes)
	- [2.3 Related Work](#23-related-work)
- [3 Dataset](#3-dataset)
- [4 A Codebook to Characterize Viral Memes](#4-a-codebook-to-characterize-viral-memes)
	- [4.1 RH1: Composition](#41-rh1-composition)
	- [4.2 RH2: Subjects](#42-rh2-subjects)
	- [4.3 RH3: Audience](#43-rh3-audience)
- [5 Annotation](#5-annotation)
	- [5.1 Annotation Platform](#51-annotation-platform)
	- [5.2 Annotation Process](#52-annotation-process)
- [6 Modeling Indicators of Image Virality](#6-modeling-indicators-of-image-virality)
	- [6.1 Classification](#61-classification)
	- [6.2 Feature Importance](#62-feature-importance)
	- [6.3 Evaluation of the Research Hypotheses](#63-evaluation-of-the-research-hypotheses)
- [7 Case Studies](#7-case-studies)
	- [7.1 A Viral Meme: Smug Frog](#71-a-viral-meme-smug-frog)
	- [7.2 Non-viral memes"](#72-non-viral-memes)
	- [7.3 Viral Memes on Twitter and Reddit](#73-viral-memes-on-twitter-and-reddit)
- [8 Discussion \& Conclusion](#8-discussion--conclusion)
	- [8.1 Design Implications](#81-design-implications)
	- [8.2 Limitations and Future Work](#82-limitations-and-future-work)

## 1 Introduction

**Understanding Indicators of Virality in Image Memes**

**Background:**
- Image memes play an increasing role in Internet culture
- Previous research focused on textual content spread, not visual elements
- This study aims to understand the impact of visual elements on image meme virality

**Research Hypotheses:**
1. **Composition (RH1):** A poorly composed image meme is unlikely to be re-shared and become viral
2. **Subject (RH2):** The subject depicted in an image meme affects its likelihood of going viral
3. **Target Audience (RH3):** The target audience's understanding of a meme impacts their choice to re-share it

**Methodology:**
1. Select set of viral and non-viral image memes from 4chan’s Politically Incorrect Board (/pol/)
2. Develop codebook to characterize visual cues that potentially contribute to virality
3. Human annotators label 100 images using the codebook
4. Train classifier to distinguish between viral and non-viral image memes based on the codebook features
5. Evaluate models' ability to predict popular memes on mainstream Web communities (Twitter, Reddit)

**Findings:**
1. Composition, subject, and target audience all play important roles in image meme virality
2. Machine learning models trained on /pol/ data can effectively distinguish between viral and non-viral image memes
3. Models trained on /pol/ data correctly predict 19 out of the 20 most popular image memes shared on Twitter and Reddit
4. Codebook features help explain why certain image memes became popular while others did not

**Implications:**
- Understanding visual elements that affect image meme virality can lead to more effective online information campaigns
- Models can be used to moderate content on social networks by prioritizing potentially viral imagery and discarding unlikely-to-be-shared images.


## 2 Background and Related Work

**Background:**

* Operational definition of image memes provided
* Review of prior work:
  + Not explicitly stated in bullets. Provide specific studies or authors if possible.


### 2.1 Memes

**Memes**
- Term coined by Richard Dawkins in 1976 to designate non-genetic behavior that spreads through population
- Digital version of memes emerged in the late 1990s and early 2000s
- Noted by sociologists as a new genre of "cut and paste" jokes in response to events like 9/11 terrorist attacks
- Consisted of various types of content, including catchphrases, images, and video clips, that were shared and modified
- Can be defined as a piece of culture with sarcastic or amusing undertones that gains influence by being shared online

**Virality**
- Image memes have become a prominent way for social media users to communicate complex concepts
- Viral memes are indicated by the number of times they are shared on social media and appear at high frequency online

**Image Memes**
- Operational definition: An image must be shared by more than one user on social media and present at least one variation to be considered an image meme
- Example: "Nick Young" meme, which presents three variations of the same concept.


### 2.2 Why and How Do People Share Memes?

**Why and How People Share Memes**

**The Uses and Gratification Theory (UGTheory):**
- Users are not a passive audience of media
- Consumers choose content based on needs and gratification
- Memes function as a tool to connect users and their audience
- Used for sharing information and emotions

**Different User Behavior:**
- Passively consume memes without understanding
- Actively get involved in dissemination process by re-sharing or modifying

**Personality Traits and Social Media Use:**
- Narcissism, extraversion, anxiety affect online communication perception and reaction

**Influencers and Viral Content Spreading:**
- High homogeneity within online communities
- Reputation of influencers induces conformity behavior
- Matching attitude, beliefs, and behaviors towards a viral meme leads to sharing and imitation under unconscious conformity

**Visual Information Preference:**
- Individuals prefer images over textual labels for attention
- "Pictorial superiority effect": images more likely to catch user's attention than textual labels.


### 2.3 Related Work

**Previous Research on Viral Content:**
* Studied how textual information goes viral on social media [46, 75, 90]
* Features influencing virality: comments [46], votes [34], user-defined groups [75, 90]
* Supervised learning used to predict virality of text memes [12, 14, 85]
* Success of online content depends on timing, social network structure, randomness, and audience appeal [12, 13]
* Emotions generated (surprise, interest) play a role in virality but may not be the only factor [40, 69]
* Some research argues that virality is a random event [12]

**Image Memes:**
* Recent focus on image memes and user interaction [21, 57, 92]
* Dupuis et al. identified personality traits of users sharing disinformation [21]
* Crovitz and Moran analyzed image memes as vehicles for disinformation [17]
* Small polarized communities effective in pushing hateful content on mainstream social media [92]

**Viral Marketing:**
* Targeting platforms, narrative advertising, and high arousal emotions promote sharing behavior [62]
* Online advertisements triggering high or low arousal emotions more likely to be shared [6, 7, 61]
* Human need for affiliation drives content sharing on social media [5, 22, 25]

**Our Work:**
* First study to investigate the role of visual features in image meme virality.


## 3 Dataset

**Data Collection:**
- Collect image memes from 4chan's Politically Incorrect Board (/pol/)
- Focus on this community due to its influence on Internet culture and creation of viral memes [29, 59, 92]
- Obtain dataset of 160M images from Twitter, Reddit, 4chan, and Gab by Zannettou et al. [92]
- Cluster visually similar images using ground truth data from Know Your Meme [42]
- Extract 38,851 clusters containing image memes posted on /pol/ within a period of 13 months between July 2016 and July 2017.

**Dataset Preparation:**
- Use two datasets for analysis:
  1. Sample of 100 viral and 100 non-viral clusters based on number of posts containing the meme
  2. Sample of 50 viral and 50 non-viral clusters at random from top and bottom 1,000 clusters
- Extract medoid (representative image) for each cluster to work with single images instead of clusters.

**Codebook Development:**
1. Manual analysis of the 100 most viral and 100 least viral image memes by one author
2. Discussions and iterations among authors to develop initial codes for further annotation using thematic coding [9]
3. Evaluation of common agreement on codebook, discussions of disagreements, and finalization
4. Annotate the entire dataset and calculate a final agreement.

**Potential Indicators of Virality:**
- Composition (RH1): elements that contribute to the visual appeal and shareability of an image meme
- Subjects (RH2): themes or topics that resonate with a wide audience and encourage social engagement
- Audience (RH3): demographics or communities that are targeted, creating a sense of belonging and virality.

## 4 A Codebook to Characterize Viral Memes
**Main Phases of Codebook Development**
- **Phase 1**: Single author analysis of 200 memes (100 most viral, 100 least viral)
- **Phase 2**: All six authors' collaborative characterization

**Three-Step Process**
- **Step 1**: Multiple iterations to finalize codebook until stability
- **Step 2**: Multiple annotators rated portion of dataset
- **Step 3**: Full dataset annotation and agreement calculation

**Research Structure**
- **Purpose**: Characterize viral vs non-viral image memes
- **Dataset**: 200 total memes analyzed
- **Features**: Grouped by research hypotheses
  - **RH1**: Composition
  - **RH2**: Subjects
  - **RH3**: Audience

**Methodology Notes**
- Used **thematic coding** approach
- Focused on **virality indicators**
- Required **annotator agreement**
- Included **visual examples** of panel types (single vs multiple)

### 4.1 RH1: Composition

**Composition Factor for Image Meme Virality**

**Hypothesis**: The composition of an image contributes to its meme going viral.

**Visual Arts Definition**: Composition refers to the organization of visual elements in a picture, including color, form, line, shape, space, texture, and value.

**Factors Affecting Virality**:
- **Number of panels**: Single panel vs multiple panels (comic strips)
- **Type of images**: Photo, screenshot, or illustration
- **Scale**: Close up, medium shot, or long shot
- **Movement**: Physical movement, emotional movement, causal movement

**Panel Number**:
- Single panel: Only one image
- Multiple panels: Series of images
- Impact on attention due to longer reading time compared to a single image

**Type of Images**:
- Photo: Picture taken by a camera
- Screenshot: Image of a computer screen (Web page, etc.)
- Illustration: Drawing, painting, or printed work of art

**Scale**:
- Close up: Tightly frames a person or object
- Medium shot: Shows equality between subjects and background
- Long shot: Focuses on the larger scene rather than subject

**Movement**:
- Physical movement: Movement in the image
- Emotional movement: Expressions on faces or bodies
- Causal movement: Sequence of movements that appear to be caused by one component (sender) to another (recipient)


### 4.2 RH2: Subjects

**Research Hypotheses: Subjects in Image Memes**

**Hypothesis 2**:
- The subjects depicted in an image meme affect its virality
- **Subject**: Refers to the main idea or focus of the work, as determined by the person, object, scene, or event represented

**Types of Subjects**:
- Landscapes, still life, animals, portraits of people [71]
- Viewer's attention attracted by faces in pictures [11]
- Memes in dataset: characters, scenes, creatures, objects, other
  - **Object**: Material things that can be seen and touched
  - **Character**: People or anthropomorphized creatures/objects
  - **Scene**: Situation or activity is the main focus
  - **Creature**: Animal not anthropomorphized

**Attributes of the Subject**:
- For character memes: facial expression, posture
- Other attributes: posters, signs, screenshots, scenes, unprocessed photos

**Character's Emotion**:
- Emotion perceived from images causes physiological reactions and speeds up time perception [28, 50]
- Faces exhibiting emotion capture attention [83]
- Memes refined as facial expression or posture in F6: positive, negative, neutral
  - Positive: laughing, smiling, smug, excited
  - Negative: crying, angry/nervous, impatience/boredom/shyness
  - Neutral: typical for character's facial expression or body language

**Contains Words**:
- Caption in image memes can elicit message but may delay recognition [80]
- Study the impact of word count on a meme's virality.


### 4.3 RH3: Audience

**Hypothesis 4.3: Audience and Virality of Image Meme**

**Intended Audience**:
- Memes can be categorized into two types based on their intended audience:
  - **Human common**: Arouses common experiences and emotions, meant to be understood by all social media users regardless of background.
  - **Culture specific**: Require specific background knowledge to be fully understood, only members of the intended community can understand the full meaning.
- Memes that resonate with a general audience (human common) are more likely to go viral on social media due to their wider appeal.

**Categorizing Culture Specific Memes**:
- Culturally specific memes require specific background knowledge for understanding.
- These include **hateful**, **racist**, and **political** memes, which are often shared by polarized communities as part of "attention hacking".


## 5 Annotation

**Annotating Image Meme Dataset:**
* **Methodology**: discussed in this section
* **Human Annotation Required**: due to:
  - Complexity of image memes: mixture of drawings and collages, not well-polished pictures
  - Subjectivity of features: human common vs cultural specific
* **Web Interface Developed**: for annotating image memes
* **Annotators**: six in total, used the developed interface to label the 100 image memes
* **Automation Used**: OCR techniques for extracting words from images (F.8 in Section 4)


### 5.1 Annotation Platform

**Custom Annotation Platform:**

1. Codebook structure encoded as a graph in JSON format stored in a database.
2. Annotation questions linked to nodes in the graph, capturing hierarchical dimensions and providing direct references for annotators.
3. Some features have mutually exclusive labels, allowing multiple choices per feature.
4. 9 features with 35 possible labels for each image (Table 1).


### 5.2 Annotation Process

**Annotator Process**
- 6 annotators used Web application
- Shown images from both viral and non-viral clusters
- Asked to label based on codebook presented in Section 4
- All annotators were male or female, in their 20s and 30s, with graduate degrees
- Extensive experience with memes and hateful content

**Ethical and Privacy Considerations**
- Study approved by Boston University IRB
- No sensitive information collected
- Images with human faces may prompt privacy concerns, but only include public figures (celebrities)
- All other figures in the paper are drawings or large-scale scenes

**Inter-annotator Agreement**
- Measured using Fleiss' Kappa score to understand codebook features and establish labeling reliability
- Kappa score ranges from 0 to 1, with 0 indicating no agreement and 1 perfect agreement
- Agreeement was generally high:
  - 13 labels had almost perfect agreement (score above 0.8)
  - 15 labels had substantial agreement (score between 0.6 and 0.8)
  - 4 labels had moderate agreement (score between 0.4 and 0.6)
  - 3 labels fell below the threshold of moderate agreement: "Emotional Movement," "No Movement," and "Hateful"
- "Emotional Movement" and "No Movement" had low agreement due to subjective perception of emotion
- Hateful label may have low agreement due to different cultural backgrounds in annotators

**Number of Words**
- Not specified in provided text.


## 6 Modeling Indicators of Image Virality

**Feature Label Fleiss**

**F.1 Number of panels**:
- A single panel: 0.958 ***
- Multiple panels: 0.958 ***

**F.2 Image type**:
- Poster: 0.674 **
- Photo: 0.926 ***
- Sign: 0.640 **
- Illustration: 0.947 ***
- Screenshot: 0.933 *** and 0.951 ***

**F.3 Scale**:
- Other: 0.624 **
- Close up: 0.666 **

**F.4 Movement**:
- Neutral: 0.627 **
- Physical Movement: 0.724 **

**F.5 Type of subject**:
- Political: 0.876 ***
- An object/objects: 0.592 *
- A character/characters: 0.768 **
- A scene/scenes: 0.544 *
- A creature/creatures: 0.457 *

**F.6 Attributes of subject**:
- Facial expression: 0.709 **
- Stationary pose/posture: 0.649 **

**F.7 Emotion**:
- Positive: 0.794 **
- Negative: 0.765 **

**F.9 Audience**:
- Human Common: 0.719 **
- Cultural Speciﬁc: 0.729 **

*** indicates almost perfect agreement, ** substantial agreement, and * moderate agreement with the Fleiss score.


### 6.1 Classification

**Feature Selection:**
- Start with features described in Section 4
- Exclusive options become single features (e.g., scale of meme)
- Multiple options split into multiple features (e.g., character and object)
- 30 resulting features: number of images, type of images, etc.

**Classifier Selection:**
- Eight classifiers selected for training: Random Forest, SVM, Logistic Regression, KNN, Ada Boost, Gaussian Bayesian, Decision Tree, Neural Network
- Perform 10-fold cross validation for each classifier on annotated set of 100 image memes
- Calculate Area Under the ROC Curve (AUC) and standard deviation for each classifier

**Classifier Performance:**
- Random Forest achieves best performance with an AUC of **0.866**
- Among non-tree based classifiers, KNN has the best classification performance, achieving an AUC of **0.828**.


### 6.2 Feature Importance

**Feature Importance**

**Understanding Contributing Features**:
- Identifying indicators of virality (or non-virality) through feature analysis of best performing classifier (Random Forest)
- Discussing top 5 features learned by this model and whether images with them are more likely to go viral or not be shared:

**1. Facial Expression**:
- Random Forest classifier identifies facial expression as most important feature for classification
- 84% of viral memes (42 out of 50) have this feature, compared to 38% of non-viral ones (19 out of 50)

**2. Character Emotion**:
- Positive emotions make images more likely to go viral: 39% of viral memes present this feature vs. 15% of non-viral ones
- Negative emotions also contribute to virality: 27% of viral memes have this feature, compared to 17% of non-viral ones

**3. Character Posture**:
- Classifier identifies character posture as third most important feature
- 46% of viral memes present this feature, while only 30% of non-viral ones do

**4. Image Scale**:
- Medium shot scale does not affect virality significantly (58% and 61% for viral and non-viral, respectively)
- Close up scales make images more likely to go viral: 34% of viral memes have this feature, while only 14% of non-viral ones do
- Large shot scales reduce the likelihood of an image being viral: 27% of non-viral memes present this feature, compared to 4.6% of viral ones

**5. Character as Subject**:
- Presence of a character is the strongest indicator among other subjects for predicting virality
- 93% of image memes in viral class are labeled as "character," while only 67% in non-viral class have this feature.


### 6.3 Evaluation of the Research Hypotheses

**Evaluation of Research Hypotheses**
- Re-evaluating three research hypotheses: composition (RH1), subjects (RH2), and audience (RH3) of an image meme on its virality

**Composition (RH1)**
- Classification model shows close up images more likely to go viral, long shots less likely to go viral
- Composition does impact meme virality, confirming RH1

**Subjects (RH2)**
- Character images more likely to go viral; object images less likely
- Facial expressions and posture also influence virality
- Subjects play a significant role in meme virality, conﬁrming RH2

**Audience (RH3)**
- No confirmation of audience influence on virality from classiﬁcation model
- None of the audience-related features found to be important

**Predicting Viral Memes on Twitter and Reddit**
- Collect additional dataset of top 10 memes on Twitter and Reddit
- Repeat annotation process, run models trained on 4chan data on new set
- 19 out of 20 most popular image memes correctly classified as viral
- Indicators of virality generalize to other platforms
- Best performing classifier for this experiment is KNN
- Tree-based classiﬁers provide worse results due to limited training data.


## 7 Case Studies

**Case Studies: Evaluating Virality in Image Memes**

1. **Viral Meme (Smug Frog)**: Discuss features explaining its virality.
2. **Non-viral Memes**: Analyze features impacting their non-virality using codebook.
3. **Top Twitter & Reddit Memes**: Apply identified virality indicators.
4. **Failing Meme**: Reason about reasons for model's failure to predict its virality.


### 7.1 A Viral Meme: Smug Frog

**Pepe the Frog Memes**

**Background**:
- Originally a comic book character created by Matt Furie
- Spawned numerous derivatives and became popular online
- Declared as a hate symbol by the Anti-defamation League

**Smug Frog Meme**:
- One of many incarnations of Pepe, originated on 4chan in 2011
- Viral with many variations posted across social media
- Prominently discussed online:
    - 63,447 threads on 4chan
    - 2,197 tweets
    - 392 posts on Gab
    - 5,968 posts on Reddit

**Characteristics of Viral Meme**:
- Close up scale, tightly framing the character's face
- Positive emotion and posture
- Identified by the model as important features of virality


### 7.2 Non-viral memes"

**Models Identifying Viral Traits in Images:**
* Multiple identified traits help an image go viral (Figure 13)
* Lack of these characteristics indicates low likelihood for virality (Figures 14a-d)
* Characters or clear focus point required for visual cues and fewer words

**Non-Viral Meme Examples:**
* Manning Face, Roll Safe: No characters (Fig. 13a, b)
* That's the Joke, Evil Kermit: Lack of clear focus (Fig. 4c, d)
* Confession Bear, Nut Button: Require reading entire text to understand (Fig. 5a, 6b)
* This is Fine, Smug Frog: Text reliance for meaning (Fig. 7a, 8b)
* Rage Guy, Expanding Brain: Intricate or elaborate texts (Fig. 9c, 10a)
* Make America Great Again, Demotivational Posters: No clear meme concept (Fig. 11a, 12a)
* Fake CCG Cards, Cash Me Ousside/Howbow Dah: Unclear context (Fig. 13e, f)

**Table 3:** Top 10 Viral Memes on Reddit and Twitter (July 2016 - July 2017) [Source: Know Your Meme]
* Meme #Posts (%): Roll Safe (5.9%), That's the Joke (5.3%), Sad Frog (4.0%), Arthur's Fist (3.8%), Confession Bear (2.2%), Nut Button (1.5%), This is Fine (1.2%), Reaction Images (1.0%), Conceited Reaction (1.0%), Make America Great Again (0.8%)


### 7.3 Viral Memes on Twitter and Reddit

**Case Studies: Viral Memes on Reddit and Twitter**

**Manning Face (Reddit):**
- Most shared meme on Reddit between 2016 and 2017
- Depicts NFL quarterback Peyton Manning in a black hoodie
- Used as a bait-and-switch joke in threads
- Features indicative of viral memes: close up of character, dramatic facial expression

**Roll Safe (Twitter/Reddit):**
- Most popular meme on Twitter between 2016 and 2017
- Depicts actor Kayode Ewumi pointing to his temple
- Accompanied by witty text denoting smart thinking
- Features indicative of viral memes: close up of character, positive facial expression, particular posture

**Fake CCG Card (Reddit):**
- Not detected as a viral meme by the classifier
- Depicts a modified version of a Collectible Card Game (CCG) card
- Composition of Fake CCG Card meme and "THE GAME" meme
- Older meme originating in the real world in the 1990s

**General Findings:**
- Classifiers developed with data from /pol/ helpful for characterizing memes on Twitter and Reddit
- Indicative features of viral memes: close up of character, positive facial expression.


## 8 Discussion & Conclusion

**Image Memes: Features Indicative of Virality**

* Studied composition, subjects, and intended audience features
* Scale, characters, facial emotions, poses indicative of virality
* Encourages further analysis in online discussion, abuse, content moderation
* Design implications and limitations: future work directions.


### 8.1 Design Implications

**Aesthetic Properties and Viral Memes**
* Our work provides evidence that:
  * Aesthetic properties, grounded in art theory and neuroscience findings, have predictive power in understanding whether memes will go viral
* Implications:
  * Could be used to design more effective messaging in online ads, activism campaigns, and product promotion to increase reach
  * Potentially could help optimize the production of harmful memes (e.g., disinformation, hateful content)
* Challenges:
  * Automated-moderation systems are currently inadequate compared to human moderators
  * Integrating our findings into the toolbox used by human moderators can help prioritize and reason about their decisions
* Concerns:
  * Designing automated tools that help determine whether pictures of individuals might become viral memes could have personal consequences (e.g., related to privacy, safety)
  * Further interdisciplinary work is needed to inform precautionary measures and meaningful informative feedback for social platform operators and users alike.


### 8.2 Limitations and Future Work

**Limitations of the Study:**
* **Virality is a spectrum**: Focused on most and least viral image memes to understand indicators of virality
* **Additional community-specific indicators**: Possibility of additional indicators for image memes on different platforms
* **Ephemerality's effect on sharing patterns**: Investigation needed to understand if ephemerality influences re-sharing behavior
* **Stability over time**: Open question regarding the need for frequent retraining and updates to the model.

**Future Work:**
* Extend analysis to image memes posted on multiple platforms
* Study how cultural backgrounds influence understanding and sharing of same image memes
* Investigate use of other indicators of virality, such as likes, retweets, and long-term stability.

