### Examples / Common cases when evaluating: Subject-Driven Image Editing

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

