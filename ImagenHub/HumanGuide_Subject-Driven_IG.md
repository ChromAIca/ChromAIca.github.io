
### Examples / Common cases when evaluating: Subject-Driven Image Generation

**Case: Normal situation.**

```
"subject_id": 16,
"subject": "dog8",
"prompt": "A <token> dog swimming in a river"
```
<p>Input | Token | OutputA | OutputB | OutputC | OutputD | OutputE</p>
<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/input/sample_83.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/BLIPDiffusion_Gen/sample_83.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/DreamBooth/sample_83.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/DreamBoothLora/sample_83.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/SuTI/sample_83.jpg" width="256" />   
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/TextualInversion/sample_83.jpg" width="256" />   
</p>

* This is how I would rate them:
* OutputA: `[0.5, 1]`. SC=0.5: The subject of the output does not quite match the input image. PR=1: It looks real.
* OutputB: `[1, 1]`. SC=1: The output does match the subject and prompt. PR=1: It looks real.
* OutputC: `[0, 1]`. SC=0: The subject of the output does not match the input image.  PR=1: It looks real.
* OutputD: `[1, 1]`. SC=1: The output does match the subject and prompt. PR=1: It looks real.
* OutputE: `[0, 0]`. SC=1: The subject does match the token. PR=0: Serious unusual body.



**Case: Partial match.**

```
"subject_id": 2,
"subject": "bear_plushie",
"prompt": "a <token> bear plushie in a basket"
```
<p>Input | Token | OutputA | OutputB | OutputC | OutputD | OutputE</p>
<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/input/sample_12.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/BLIPDiffusion_Gen/sample_12.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/DreamBooth/sample_12.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/DreamBoothLora/sample_12.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/SuTI/sample_12.jpg" width="256" />   
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IG/TextualInversion/sample_12.jpg" width="256" />   
</p>

* This is how I would rate them:
* OutputA: `[0, 1]`. SC=0: The output does not match the prompt. PR=1: It looks real.
* OutputB: `[0.5, 1]`. SC=0.5: The hat of the subject does not match the input image. PR=1: It looks real.
* OutputC: `[0, 1]`. SC=0: The output does not match the subject. PR=1: It looks real.
* OutputD: `[0, 0.5]`. SC=0: The output does not match the prompt. PR=0.5: Some unnatural sense in the gound.
* OutputE: `[0, 0.5]`. SC=0: The output does not match the subject and prompt. PR=0.5: Some unnatural sense in the blue part.

