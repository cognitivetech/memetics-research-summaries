# Zero shot VLMs for hate meme detection: Are we there yet?

[Zero shot VLMs for hate meme detection: Are we there yet?](https://arxiv.org/html/2402.12198) arxiv.org

**Case Analysis: Misclassified Memes**

**Segmentation using SLIC algorithm**:
- Segment misclassified memes into superpixels (5-12 depending on image size)
- Control size of each superpixel to avoid being too small or large
- Occlude regions one at a time and query model for predictions

**CASE 1: Original meme misclassified as positive, correct prediction after occlusion**:
- **FHM dataset**: Memes contain human/animal images and profane text. Occlusion removes confusing regions leading to correct prediction
- **MAMI dataset**: Memes have perturbed women's faces or embedded text with misogynistic words. Occlusion changes focus, allowing correct prediction
- **HARM P+C dataset**: Memes composed of stacked images and long text. Occlusion fails to explain performance gap; more research needed

**CASE 2: Original meme misclassified as positive, no correct prediction after occlusion**:
- **FHM dataset**: Majority of memes are hateful, incorrectly annotated as not hateful. No change in predictions during occlusion
- **MAMI dataset**: Memes portray nudity, vulgarity, and feminism. Model correctly classifies them as misogynistic
- **HARM P+C dataset**: Most memes contain images of Trump or mention his name, long embedded texts confuse the model

**CASE 3: Original meme misclassified as negative, correct prediction after occlusion**:
- **FHM dataset**: Memes have small font size and numerous color variations. Occlusion focuses model on important regions for correct classification
- **MAMI dataset**: Memes portray nudity or vulgarity, embedded text contains word 'MILF'. Occlusion brings focus to disturbing elements, leading to correct prediction
- **HARM P+C dataset**: Memes contain images of Trump or mention his name. Long embedded texts confuse the model; occlusion helps bring back focus

**CASE 4: Original meme misclassified as negative, no correct prediction after occlusion**:
- **FHM dataset**: Memes have implicit hate, individually image and text do not portray anything harmful but together imply semantics that confuse the model
- **MAMI dataset**: Memes bear implicit misogynistic content with words like 'dishwater', 'sandwich maker'. Model struggles to infer correct class, occlusion doesn't help
- **HARM P+C dataset**: Memes portray fake conversations between political leaders. Implicit harm causes model misclassification both for original and occluded memes.

---

Thank you to arXiv for use of its open access interoperability.
