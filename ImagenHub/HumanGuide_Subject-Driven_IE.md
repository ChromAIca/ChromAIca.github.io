### Examples / Common cases when evaluating: Subject-Driven Image Editing

**Case: Normal situation.**

```
"subject": "fancy_boot"
```
<p>Input | Token | OutputA | OutputB | OutputC</p>
<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IE/input/sample_79.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IE/token/sample_79.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IE/BLIPDiffusion_Edit/sample_79.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IE/DreamEdit/sample_79.jpg" width="256" /> 
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Subject-Driven_IE/PhotoSwap/sample_79.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[0, 1] `. SC=0: The subject does not match the token. PR=1: It looks real.
* OutputB: `[1, 0.5]`. SC=1: The subject does match the token. PR=0.5: Some unusual sense in the ankle.
* OutputC: `[1, 1]`. SC=1:The subject does match the token. PR=1: It looks real.

**Case: Background not match.**
