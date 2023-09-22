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

