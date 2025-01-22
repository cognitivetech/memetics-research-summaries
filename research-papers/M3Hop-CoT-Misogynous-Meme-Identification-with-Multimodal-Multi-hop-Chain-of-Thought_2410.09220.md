# M3Hop-CoT: Misogynous Meme Identification with Multimodal Multi-hop Chain-of-Thought

[M3Hop-CoT: Misogynous Meme Identification with Multimodal Multi-hop Chain-of-Thought](https://arxiv.org/html/2410.09220) arxiv.org


**Misogynous Memes Identification using Multi-Modal Chain-of-Thought (M3Hop-CoT)**

**Challenges of Identifying Misogynous Memes:**
- Understanding world knowledge and common sense required
- Limited data for learning complex multi-modal interactions

**Benefits of Developing Deep Learning Models:**
- Understanding hidden meanings in memes
- Supporting humanities research
- Raising awareness on a large scale

**Previous Research:**
- Primarily focused on developing robust deep-learning models for identifying misogynous memes from scratch
- Learning complex multi-modal interactions can be difficult with limited data

**Advancement of Large Language Models (LLMs):**
- Highly adept at question-answering and reasoning tasks
- Overlooks cultural diversity and contextual knowledge crucial for multimodal reasoning
- Concept of Chain-of-Thought (CoT) demonstrated potential for multi-hop reasoning with LLMs

**Challenges in Analyzing Memes:**
- Implicit meanings not fully conveyed through text and images
- Neglecting one modality can negatively impact model performance

**Proposed Approach:**
- M3Hop-CoT framework: deep learning-based, multi-modal approach utilizing LLM as reasoning module
- Extract Entity-object-relationship (EORs) of meme-image using a scene graph
- Feed meme text, image, and EORs into multi-hop CoT LLM to identify emotions, targets, contexts
- Eliminate need for external resources and bridge the gap between modalities at zero cost
- Utilize hierarchical cross-attention mechanism to ensure weighted contribution of each reasoning step.

**Contributions:**
1. First study to introduce multimodal LLM in a CoT manner for misogynous meme identification
2. Introduction of M3Hop framework: utilizes meme text and EORs as prompt to LLM in multi-hop CoT manner, enabling detection of three crucial rationales (emotion, target, context)
3. Validation through empirical evaluation on several datasets, demonstrating strong performance.

---

Thank you to arXiv for use of its open access interoperability.