## **Human Eval - Mask-Guided Image Editing**

* Semantic Consistency (SC) scoring for **Mask-Guided Image Editing**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, without unnecessary edits.
    * SC=1 : The generated image perfectly described all the required attributes but having unnecessary edits.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed in following the key instruction in editing, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Mask-Guided Image Editing**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.



### **Examples / Common cases when evaluating: Mask-Guided Image Editing**

<!-- Please refer to [**Examples / Common cases when evaluating: Text-Guided Image Editing**](https://github.com/ChromAIca/ChromAIca.github.io/tree/main/ImagenHub#examples--common-cases-when-evaluating-text-guided-image-editing). They are basically having the same standard. -->
#### Example 1
```
"source_global_caption": "A piece of pie has bananas and whipped cream surrounding it on a white plate.",
"instruction": "put strawberry on the plate",
"target_global_caption": "A piece of pie with bananas, whipped cream, and strawberries surrounding it on a white plate."
```
Input|Mask|BlendedDiffusion

Glide|SDInpaint|SDXLInpaint

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/input/sample_219590_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/mask/sample_219590_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/BlendedDiffusion/sample_219590_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/Glide/sample_219590_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDInpaint/sample_219590_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDXLInpaint/sample_219590_1.jpg" width="256" /> 
</p>

- BlendedDiffusion: `[0, 0]`. Generated content can not be regarded as strawberry, SC=0. In general the image is unnatural, PR=0.
- Glide: `[0.5, 0]`. Generated content looks like strawberry but it's unnatural, SC=0.5. Edi region does not seamlessly blend with context, PR=0.
- SDInpaint: `[2, 1]`. Succesfully edits a clear strawberry, SC=2. The bottom left part of the generated content does not blend well with the context.
- SDXLInpaint: `[0, 1]`. Fail to add strawberry, SC=0. THe bottom left part has unexpected red.

#### Example 2
```
"source_global_caption": "The tennis player is up in the air hoping to striking the ball.",
"instruction": "have the person jump over a tennis ball.",
"target_global_caption": "The tennis player jumps over the ball with ease."
```
Input|Mask|BlendedDiffusion

Glide|SDInpaint|SDXLInpaint

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/input/sample_237569_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/mask/sample_237569_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/BlendedDiffusion/sample_237569_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/Glide/sample_237569_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDInpaint/sample_237569_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDXLInpaint/sample_237569_1.jpg" width="256" /> 
</p>

- BlendedDiffusion: `[0, 0]`. Fail to add the tennis ball, SC=0. The edit region fail to blend well with the context. PR=0
- Glide: `[0,2]` Fail to edit the image, SC=0. The image looks natural and photorealistic in general, PR=2.
- SDInpaint: `[0.5,0]`. Successfully add a tennis ball-like object without much details, SC=0.5. The edit region does not blend well with the context, PR=0.
- SDXLInpaint: `[0,2]`. Fail to edit anything, SC=0. In general the image itself is photorealistic, PR=2.

#### Example 3
```
"source_global_caption": "This jet just landed at the airport and is making it way down the jetway",
"instruction": "Can we have a blue airplane?",
"target_global_caption": "This blue jet just landed at the airport and is making its way down the jetway."
```
Input|Mask|BlendedDiffusion

Glide|SDInpaint|SDXLInpaint

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/input/sample_249441_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/mask/sample_249441_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/BlendedDiffusion/sample_249441_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/Glide/sample_249441_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDInpaint/sample_249441_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDXLInpaint/sample_249441_1.jpg" width="256" /> 
</p>

- BlendedDiffusion: `[0, 0]`. The edited object can hardly be regarded as airplane, SC=0. Unrealistic object and unnatural image, PR=0.
- Glide: `[2, 1]`. Clearly generates the blue airplane, SC=2. The edit region does not blend seamlessly to the rest of the image, PR=1.
- SDInpaint: `[0.5,0]`. Generates a airplane-like object but not good enough, SC=0.5. In general the image is not natural, Pr=0.
- SDXLInpaint: `[2, 1]`. Successfully generates the blue airplane, SC=2. The rightmost part is a bit blurry, PR=1.

#### Example 4:
```
"source_global_caption": "A small black dog playing with a frisbee.",
"instruction": "turn the frisbee into a soccer ball",
"target_global_caption": "A small black dog playing with a soccer ball."
```
Input|Mask|BlendedDiffusion

Glide|SDInpaint|SDXLInpaint

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/input/sample_25989_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/mask/sample_25989_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/BlendedDiffusion/sample_25989_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/Glide/sample_25989_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDInpaint/sample_25989_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDXLInpaint/sample_25989_1.jpg" width="256" /> 
</p>

- BlendedDiffusion: `[0, 0.5]`. Generates a black ball rather than the soccer, SC=0. The texture of the grass in the edit region does not match well that of the context, PR=0.5.
- Glide: `[0, 1]`. Fail to add soccer, SC=0. The edit region is not bleded well with the context, PR=1.
- SDInpaint: `[2,0.5]`. Clearly generate the soccer, SC=2. The edit region does not blend well with the context, PR=0.5
- SDXLInpaint: `[2, 2]`. Successfully add a soccer, SC=2. The soccer is naturally blended with the context, PR=2.

#### Example 5:
```
"source_global_caption": "A Zebra standing in between a group of large rocks",
"instruction": "Make the zebra a regular horse.",
"target_global_caption": "A horse standing in between a group of large rocks"
```
Input|Mask|BlendedDiffusion

Glide|SDInpaint|SDXLInpaint

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/input/sample_291861_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/mask/sample_291861_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/BlendedDiffusion/sample_291861_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/Glide/sample_291861_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDInpaint/sample_291861_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Mask-Guided_IE/SDXLInpaint/sample_291861_1.jpg" width="256" /> 
</p>

- BlendedDiffusion: `[0, 0]`. Generated content can not be regarded as horse, SC=0. The middle left part is not natural, PR=0.
- Glide: `[0.5, 0]`. The object is horse-like but not good, SC=0.5. The whole image is not natural, PR=0.
- SDInpaint: `[2, 1]`. Succesfully generate a horse, SC=2. The edit region does not blend well wtih the context, PR=1.
- SDXLInpaint: `[1,1]`. Succesfully generate a regular horse, but it also changes the shape of the horse, SC=1. The horse legs are a bit unnatural, PR=1.

