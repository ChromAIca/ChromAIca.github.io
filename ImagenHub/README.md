# Human Evaluation Guide

> Our Evaluation Guide is extended from the evaluation standard in [DreamEdit](https://arxiv.org/abs/2306.12624).

# Evaluation Guide for Human Evaluators

Please refer to the [Task-Specific Guide for Human Evaluation scoring](https://github.com/ChromAIca/ChromAIca.github.io/tree/main/ImagenHub#task-specific-guide-for-human-evaluation-scoring) when perform human evaluation. This general guide only presents the basic idea.

To standardize the conduction of a rigorous human evaluation, we stipulate the criteria for each measurement as follows:
* Semantic Consistency (SC), score in range `[0, 0.5, 1, 2]`
* Perceptual Realism (PR), score in range `[0, 0.5, 1, 2]`


Semantic Consistency (SC) ensures that the generated image is coherent in terms of guidance provided (i.e. Prompts, Subject Token, etc.). In another words, the image has to be aligned with the requirements provided in user's inputs.


General design rules for Semantic Consistency (SC) scoring:
* SC=2 : The generated image perfectly described all the required attributes of the provided guidance.
* SC=1 : Low-level features mismatch spotted in the generated image.
* SC=0.5 : High-level features mismatch spotted in the generated image.
* SC=0 : The generated image failed in following the majority of required attributes of the provided guidance.


Perceptual Realism (PR) ensures the generated image align with real-world characteristics. In another words, the image has to be visually convincing and closely resembles a real photograph (Photorealism).


General design rules for Perceptual Realism (PR) scoring:
* PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence.
* PR=1 : Nearly no distortion, incompletion found. including sense of distance, lighting or shadow details.
* PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. watermark) can be spotted but do not strongly detract from its overall appearance.
* PR=0 : Obvious noise, distortion, or incompletion can be spotted.



> We present each image with a human evaluation in `[<SC score>,<PR score>]`.



# Task-Specific Guide for Human Evaluation scoring:

In the Task-Specific Scoring Guide we outline the details of the score judgement.

## **Human Eval - Text-Guided Image Editing**

* Semantic Consistency (SC) scoring for **Text-Guided Image Editing**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, without unnecessary edits.
    * SC=1 : The generated image perfectly described all the required attributes but having unnecessary edits.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed in following the key instruction in editing, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Text-Guided Image Editing**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.



### **Examples / Common cases when evaluating: Text-Guided Image Editing**

> Note that all the images on the left are Inputs, while the images on the right are the outputs.
>
> We present each image with a human evaluation in `[<SC score>,<PR score>]`.

<br><br>

**Case: Output image looks nearly identical to the input image.**

```
"source_global_caption": "An empty kitchen filled with dishes and appliances, with a game show on TV.",
"instruction": "let there be granite floor in the kitchen",
"target_global_caption": "An empty kitchen with granite floors filled with dishes and appliances, with a game show on TV."
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_102625_2.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/CycleDiffusion/sample_102625_2.jpg" width="256" /> 
</p>

* Basically, we gives SC=0 for cases like this. The PR score would vary according to the realism of the image (are there anything that looks unnatural?)
* If the Output image is exactly identical to the input image, we would rate the score `[0, 2]` (we assume the input image is a realistic photo.).
* In this given example, I would rate the score `[0, 1]` because there are some unnatural spots. 

<br><br>

**Case: Output image is following the prompt well, but causing unnecessary edits.**

```
"source_global_caption": "An empty kitchen filled with dishes and appliances, with a game show on TV.",
"instruction": "let there be granite floor in the kitchen",
"target_global_caption": "An empty kitchen with granite floors filled with dishes and appliances, with a game show on TV."
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_102625_2.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/InstructPix2Pix/sample_102625_2.jpg" width="256" /> 
</p>

> Btw this is how a granite floor look like:
>
> <img src="https://www.regattagranitesindia.com/wp-content/uploads/2019/03/Rosewood-granite-flooring.jpg" alt="Granite floor tiles for having a traffic friendly surface" width="256" />
>
> <img src="https://marblerenewal.ca/wp-content/uploads/2015/11/Living-Room.jpg" width="256" />

* It seems the output image is following the prompt and the floor does look like a granite floor. However, the pattern also applied on other areas which makes the kitchen looks dirty.
* We treat this case "unnecessary edits.", therefore the score SC=1.
* The image also look nearly identical to the input image, so PR=1 or 2.
* In this given example, I would rate the score `[1, 1]` or `[1, 2]` (if you want to assume its a dirty kitchen).

<br><br>

**Case: Output image is following the prompt well, but the background completely changed.**

```
"source_global_caption": "some fruits are sitting on a table in bowls.",
"instruction": "remove middle fruit and put a cat in place",
"target_global_caption": "A cat sits on a table surrounded by bowls of fruit."
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_102724_1.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/Prompt2prompt/sample_102724_1.jpg" width="256" /> 
</p>


* For Editing tasks, no matter how the image following the prompt well, we give SC=0 as long as the result is in a complete different background.
* The PR score would vary according to the realism of the image. (are there anything that looks unnatural?)
* In this given example, I would rate the score `[0, 0.5]` or `[0,0]`.  The image looks real at first glance but there are some distortion in the body and on the fruits / background.



> How do we define unnecessary edits and complete different background?
>
> ```
> "source_global_caption": "An empty kitchen with granite floors filled with dishes and appliances, with a game show on TV.",
> "instruction": "let the cabinets be made of dark wood",
> "target_global_caption": "An empty kitchen with dark wood cabinets and granite floors filled with dishes and appliances, with a game show on TV."
> ```
>
> Input | Unnecessary/Bad Edit | Complete different background
>
> <p float="left", align="center">
>   <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_102625_3.jpg" width="256" />
>   <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/MagicBrush/sample_102625_3.jpg" width="256" /> 
>   <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/Pix2PixZero/sample_102625_3.jpg" width="256" /> 
> </p>

<br><br>

**Case: Output images are following the prompt (how well and how real are they?)**

```
"source_global_caption": "A skateboarder is doing a trick on a hand rail.",
"instruction": "What if the man had a hat?",
"target_global_caption": "A skateboarder with a hat is doing a trick on a hand rail."
```

Input | OutputA | OutputB | 
OutputC | OutputD | OutputE

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_139276_1.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/InstructPix2Pix/sample_139276_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/MagicBrush/sample_139276_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/Prompt2prompt/sample_139276_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/Text2Live/sample_139276_1.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/SDEdit/sample_139276_1.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[2, 1] `. The hat suits well thus SC=2. PR=1 because there is minor facial distortion on the man.
* OutputB: `[1, 1]`. The hat suits well, but there is unnecessary edits on his hand, therefore SC=1. PR=1 because there is minor distortion on the man's face.
* OutputC: `[0.5, 0.5]`. The hat exists but does not suit well, thus SC=0.5. PR=0 or 0.5 because the important object look distorted.
* OutputD: `[1, 2]`. The hat suits well, but the background color doesn't match thus SC=1. PR=1 or 2 as the image look quite real with no distortion.
* OutputE: `[0, 0]`. SC=0 because the background completely changed. And PR=0 or 0.5 because the whole image look distorted.

<br><br>

**Perfect Cases: The Editing following the prompt perfectly and look very real**

```
"source_global_caption": "A bull is on a farm walking around a pen.",
"instruction": "Have the cow wear a hat.",
"target_global_caption": "A stylish cow wearing a hat walks around a pen on a farm."
```

<p float="left", align="center">
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/input/sample_111376_1.jpg" width="256" />
  <img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-Guided_IE/InstructPix2Pix/sample_111376_1.jpg" width="256" /> 
</p>

* In this given example, I would rate the score `[2, 2]` . The hat gives a nice specular reflection.





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
- Glide: `[0.5, 0]`. Generated content looks like strawberry but it's unnatural, SC=0.5. Edi region does not seemlessly blend with context, PR=0.
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
- Glide: `[2, 1]`. Clearly generates the blue airplane, SC=2. The edit region does not blend seemlessly to the rest of the image, PR=1.
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


## **Human Eval - Subject-Driven Image Editing**

* Semantic Consistency (SC) scoring for **Subject-Driven Image Editing**:
    * SC=2 : Subject accurately represents the intended subject, closely matching all visual characteristics.
    * SC=1 : Subject somewhat represents the intended subject, mismatch low-level features such as facial/texture details. Or there are minor change in background.
    * SC=0.5 : Subject partially resembles the intended subject, mismatch high-level features such as colors, body proportions. Or there are easily observable change in background.
    * SC=0 : Subject bears little resemblance to the intended subject, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Subject-Driven Image Editing**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, or incompletion can be spotted on the object or in the background.



### Examples / Common cases when evaluating: Subject-Driven Image Editing

TBA



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


## **Human Eval - Control-Guided Image Generation**

* Semantic Consistency (SC) scoring for **Control-Guided Image Generation**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, and even work
    * SC=1 : The generated image perfectly described all the required attributes, but with unnecessary objects that is harming the scene.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed following every required attributes in the prompt. 
* Perceptual Realism (PR) scoring for **Control-Guided Image Generation**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.

### **Examples / Common cases when evaluating: Mask-Guided Image Editing**

Please refer to [**Examples / Common cases when evaluating: Text-Guided Image Editing**](https://github.com/ChromAIca/ChromAIca.github.io/tree/main/ImagenHub#examples--common-cases-when-evaluating-text-guided-image-editing). They are basically having the same standard.


## **Human Eval - Style-Guided Image Generation**

* Semantic Consistency (SC) scoring for **Style-Guided Image Generation**:
    * SC=2 : Aesthetic styles match accurately including color palette, stroke type, and paint type. And image perfectly matches to the user prompt.
    * SC=1 : Aesthetic styles match accurately including color palette, stroke type, and paint type. but image missing minor objects to the user prompt.
    * SC=0.5 : Aesthetic styles bears partial resemblance.
    * SC=0 : Obvious aesthetic styles completely mismatch or object mismatch to the user prompt.
* Perceptual Realism (PR) scoring for **Style-Guided Image Generation**:
    * PR=2 : 
    * PR=1 : Nearly no distortion, incompletion found. including sense of distance, lighting or shadow details.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. watermark) can be spotted but do not strongly detract from its overall appearance.
    * PR=0 : Obvious noise, distortion, or incompletion can be spotted.



### Examples / Common cases when evaluating: Style-Guided Image Generation

TBA



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




# Frequently Asked Questions (FAQ)
TBA



# Human Evaluation Design Rationale

## Score Design

We set 
* Score=2: Having some desire properties hopefully the field will push toward to (what the majority of SOTA models were not capable of generating those consistently)
* Score=1: Decent but not perfect results
* Score=0.5: for minor flaws
* Score=0: for serious flaws.



Insights we can want to get from our results.

* Robustness of each model.

