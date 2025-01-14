# Evolver: Chain-of-Evolution Prompting to Boost Large Multimodal Models for Hateful Meme Detection

[Evolver: Chain-of-Evolution Prompting to Boost Large Multimodal Models for Hateful Meme Detection](https://arxiv.org/html/2407.21004) ; Equal Contribution.; arxiv.org


**Hateful Meme Detection using LMMs**

**Principles of Prompts:**
- Include hateful meme definition
- Limit prompt to 30 words

**Method Overview:**
1. Define task as binary classification of image-text pairs
2. Use large multimodal model (LMM) for prediction
3. Extract evolutionary information and contextual relevance amplifier
4. Combine extracted info and amplifier for final prediction
5. Amplifier enhances in-context hatefulness information
6. Apply definition of a hateful meme as contextual relevance amplifier
7. Final prediction: y ^ = LMM(memes T, X D, Info, Amp)

**Components:**
- Memes T: memes to be detected
- X D: instruction for LMM to detect hateful memes
- Info: extracted information
- Amp: contextual relevance amplifier

**Two Key Principles:**
1. **Include the hateful meme definition**: directly apply definitions from FHM, MAMI, and HarM datasets
2. **Limit the prompt to 30 words**: addressing LMMs' challenges with long-text comprehension

**Comparison of Results:**
| Model Size (B) | Dataset: FHM | AUC Up | ACC Up | Dataset: MAMI | AUC Up | ACC Up | Dataset: HarM | AUC Up | ACC Up |
|---|---|---|---|---|---|---|---|---|---|---|
| 1B | CLIP | - | 58.3 | BERT | - | 67.4 | - | 74.5 | 68.4 |
| Text | - | 66.1 | - | Image-Region | - | 70.2 | - | 70.2 | 64.2 |
| 1B | Gemini-Pro-V, Openflamingo, MMICL, MiniGPT-v2, InstructBLIP | 57.0, 56.8, 57.4, 57.1, 55.0, 54.5 | 56.4, 60.1, 64.1, 64.1, 56.8, 60.6 | - | Evolver (Ours), Evolver † (Ours) | 63.5, 62.3 | 59.9, 59.9 | 59.3, 57.3 |
| 13B | LLAVA-1.5 | - | 61.4 | - | BLIP-2 | - | 63.8 | - | - |
| 11B | API-based (zero-shot) | 66.0 | 65.7 | BERT | 59.4 | 59.4 | - | - | - |
| GPT-4V, OpenAI | 70.5, 70.3 | - | - | CLIP | 77.7 | 80.8 | MAMI | 81.4 | 78.7 |

**Note**: The "*" symbol represents that the API-based models cannot directly apply our CoE prompt due to ethical considerations.
