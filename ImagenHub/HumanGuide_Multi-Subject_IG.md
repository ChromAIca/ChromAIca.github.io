## **Human Eval - Multi-Subject-Driven Image Generation**

* Semantic Consistency (SC) scoring for **Multi-Subject-Driven Image Generation**:
    * SC=2 : Subjects accurately represents all the intended subjects, and the prompt action match exactly.
    * SC=1 : Subjects somewhat represents the intended subject, mismatch low-level features such as facial/texture details on one of the subjects. Or Both subjects accurately represents all the intended subjects but the prompt action only match in certain degree.
    * SC=0.5 : Subjects partially resembles the intended subject, mismatch high-level features such as colors, and body proportions on one of the subjects. Or Both subjects accurately represents all the intended subjects but the prompt action does not match.
    * SC=0 : Subjects bears little resemblance to the intended subject, or there are any missing subjects.
* Perceptual Realism (PR) scoring for **Multi-Subject-Driven Image Generation**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture and background details, and overall visual coherence.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Obvious noise, distortion, or incompletion can be spotted.

### Examples / Common cases when evaluating: Multi-Subject-Driven Image Generation

**Case: Both subjects accurately represents all the intended subjects but the prompt action does not match.**

```
"source_global_caption": "An empty kitchen filled with dishes and appliances, with a game show on TV.",
"instruction": "let there be granite floor in the kitchen",
"target_global_caption": "An empty kitchen with granite floors filled with dishes and appliances, with a game show on TV."
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Multi-Subject_IG/input/sample_0.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Multi-Subject_IG/CustomDiffusion/sample_0.jpg" width="256" /> 
</p>

* Basically, we gives SC=0.5 for cases like this. Both subjects accurately represents all the intended subjects but the prompt action does not match.
* In this given example, I would rate the score `[0.5, 1]` because there are some unnatural spots on the cat but looks generally real. The pot look flawless. 

E.g. 
```
Prompt : A <token_A> Cat under <token_B> chair.
Result : The cat perfect resembles the intended subject. The chair has the wrong pattern texture. (White Metal chair become White limestone chair) 
```
SC=1 : Subjects somewhat represents the intended subject, mismatch low-level features such as facial/texture details on one of the subjects.

E.g. 
```
Prompt : A <token_A> Cat under <token_B> chair.
Result : The cat perfect resembles the intended subject. The chair has the wrong color.
```
SC=0.5 : Subjects partially resembles the intended subject, mismatch high-level features such as colors, and body proportions on one of the subjects.

E.g. 
```
Prompt : A <token_A> Cat under <token_B> chair.
Result : The cat perfect resembles the intended subject. The chair is missing. OR The chair is a completely different chair.
```
SC=0 : Subjects bears little resemblance to the intended subject, or there are any missing subjects.