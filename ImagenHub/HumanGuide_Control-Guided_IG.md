## **Human Eval - Control-Guided Image Generation**

* Semantic Consistency (SC) scoring for **Control-Guided Image Generation**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, and even work
    * SC=1 : The generated image only described partial the required attributes.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed following every required attributes in the prompt. 
* Perceptual Realism (PR) scoring for **Control-Guided Image Generation**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.

### Examples / Common cases when evaluating: Control-Guided Image Generation

**Case: The generated image is well conditioned on the control input and the prompt, but some minor perceptual faults exist.**

```
"prompt": "golden gate bridge at sunset, Golden Gate Bridge in San Francisco, USA",
"control_type": "hed"
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Control-Guided_IG/input/sample_14_control_hed.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Control-Guided_IG/ControlNet/sample_14_control_hed.jpg" width="256" /> 
</p>

* Basically, we gives SC=2 for cases like this. The generated image perfectly described all the required attributes of the user prompt, and even work.
* In this given example, I would rate the score `[0.5, 1]` because there are some missing details in the background. The details in the far-side are mostly blurred unnaturally.

**Case: The generated image is partially conditioned on the control input and the prompt, though the perceptual details are perfect.**

```
"prompt": "a person on a small sailboat in the water, transformation sequence, great britain, wearing adidas clothing, sd video, reeds, grey tarnished longcoat, training, suki, rogue, sport, glinting metal, the fifth series, sheild, laser, off putting, subdivision, smoothly",
"control_type": "openpose"
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Control-Guided_IG/input/sample_62_control_openpose.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Control-Guided_IG/ControlNet/sample_62_control_openpose.jpg" width="256" /> 
</p>

* Basically, we gives SC=1 for cases like this. The generated image only described partial the required attributes.
* In this given example, I would rate the score `[1, 2]` because there are missing objects, e.g., the sailing boat as specified in the prompt but not represented in the generated iamge. 

