# OSPC: Artificial VLM Features for Hateful Meme Detection

[OSPC: Artificial VLM Features for Hateful Meme Detection](https://arxiv.org/html/2407.12836) arxiv.org

**Methodology Overview**
- Describe overall methodology with rationale and motivation explained in individual sections
- Utilize foundational models for broader contextual understanding
- Shift focus from exact sensitivity levels to improving meme understanding

**Challenges**
- Significant discrepancies among annotators from the same cultural background (TotalDefMeme dataset)
- Establishing a universal threshold for meme classification is challenging due to subjectivity and cultural sensitivity

**Visual Processing**
- Llava's innovation: enhanced image resolution and OpenAI's CLIP technology
- OCR processing trick to filter out irrelevant languages
- Importance of Vision-Language Model (VLM) with understanding capabilities for multiple national languages

**Efficient Processing**
- Leverage advanced quantization methods like K-quants from llama.cpp project
- Employ importance matrix technique for optimal quantization and preventing performance degradation

**Singaporean Meme Analysis**
- Complexity of task: significant discrepancies among annotators, various categories requiring nuanced understanding (Hate, Offensive, Propaganda, Harassment/Cyberbullying, Violence, Self-inflicted harm, Exploitation)
- Importance of a model trained across all four national languages for comprehensive understanding.

**Application of Matrix on Q4(bit) KM Quantized Model**
- Used custom text tailored to challenge requirements on a rented 24GB GPU
- Resulted in downsized Q2(bit) K quantized model for final submission

**Visual CLIP Encoder Precision**
- Pre-quantized 6-bit model used due to minimal effect on precision
- Achieved an AUROC of **0.69** on OSPC test dataset

**Model Behavior and Precision Concerns**
- LLMs generate several token options based on context, using top-p or top-k sampling methods
- Implemented fixed prompt for precise response elicitation
  - "<|imstart|>user [img-1]"+text+prob+"<|imend|>"
    * text: OCR-detected text
    * prob: request for probabilistic response

**Model Constraints and Grammar**
- Responses constrained to single-digit outputs via specific grammar
  - strictly limiting responses between **0** and **9**.

---

Thank you to arXiv for use of its open access interoperability.
