
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
