## **Human Eval - Subject-Driven Image Generation**

* Semantic Consistency (SC) scoring for **Subject-Driven Image Generation**:
    * SC=2 : Subject accurately represents the intended subject, and the background perfectly matches to the user prompt. 
    * SC=1 : Subject mismatch low-level features such as facial/texture details of the intended subject. But the background matches to the user prompt.
    * SC=0.5 : Subject mismatch high-level features such as colors and body proportions of the intended subject. But the background matches to the user prompt.
    * SC=0 : Subject bears little resemblance to the intended subject, or the background does not align to the user prompt.
* Perceptual Realism (PR) scoring for **Subject-Driven Image Generation**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture and background details, and overall visual coherence.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Obvious noise, distortion, or incompletion can be spotted.

### Examples / Common cases when evaluating: Subject-Driven Image Generation

TBA
