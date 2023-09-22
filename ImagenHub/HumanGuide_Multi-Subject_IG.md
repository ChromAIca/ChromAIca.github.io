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