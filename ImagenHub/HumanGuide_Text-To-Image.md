## **Human Eval - Text-To-Image**

* Semantic Consistency (SC) scoring for **Text-To-Image**:
    * SC=2 : The image perfectly matched with the prompt, or the image matched with all the subject, action, position, adjective, style words in the prompt.
    * SC=1 : The image only matched with all the subject, action, and position words in the prompt, but missed some adjective (e.g. wrong color)
    * SC=0.5 : the image match with some of the subject, action, and position words in prompt, but the overall idea is wrong.
    * SC=0 : The image failed to match any of the subject, action, and position words in the prompt.
* Perceptual Realism (PR) scoring for **Text-To-Image**:
    * PR=2 : Exhibiting reasonable lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : only minor distortion found on high-level features / small objects (e.g. subject faces, small words, unusual number of fingers etc)
    * PR=0.5 : some wrong body portions spotted but still be able to identify the object, or a huge sense of unnatural feeling exists.
    * PR=0 : The image is heavily distorted, or huge potion of artifacts appeared.

### **Examples / Common cases when evaluating: Text-To-Image**

> Note that all the images on the left are Inputs, while the images on the right are the outputs.
>
> We present each image with a human evaluation in `[<SC score>,<PR score>]`.

Our dataset contain serveral categories of the image.

**Case: Rating Conflicting image**

```
"prompt": "A panda making latte art.",
"category": "Conflicting",
```

OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_9.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SD/sample_9.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SDXL/sample_9.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[0.5, 2] `. SC=2: panda should be the one making the art instead of being in the latte. Only panda and latte words matched but not panda making latte art. PR=2: Lighting looks reasonable, No distortion found.
* OutputB: `[0.5, 1]`. SC=0.5: panda is drinking instead of making latte art. PR=1: minor distortion found on the panda's hand.
* OutputC: `[2, 1]`. SC=2: The prompt match perfectly with the image. PR=1: minor distortion found on the panda's left hand.

**Case: Rating Counting image**
```
"prompt": "One cat and two dogs sitting on the grass.",
"category": "Counting",
```

OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_16.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_16.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SD/sample_16.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[2, 1] `. SC=2: prompt perfectly align. PR=1: minor distortion on the cat's facial features.
* OutputB: `[0.5, 1]`. SC=0.5: 3 dogs appeared instead of 1 cat and 2 dogs. PR=1: minor distortion was found on the animal's face and the watermark.
* OutputC: `[2, 1]`. SC=2: The prompt match perfectly with the image. PR=1: minor distortion on the dog's facial features.


**Case: Rating Positional image**

```
"prompt": "A stop sign on the right of a refrigerator.",
"category": "Positional",
```
OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_50.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/OpenJourney/sample_50.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SDXL/sample_50.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[0.5, 1] `. SC=0.5: refrigerator not found but the stop sign is here. PR=1: minor distortion on the cat's facial features.
* OutputB: `[0, 1]`. SC=0: Failed to generate refrigerator nor the stop sign. PR=1: 
* OutputC: `[2, 1]`. SC=2:  PR=1:



**Case: Rating Text image**

```
"prompt": "A sign that says 'Deep Learning'.",
"category": "Text",
```
OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_76.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_76.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SDXL/sample_76.jpg" width="256" /> 
</p>

* This is how I would rate them:


**Case: Rating Misspellings image**
```
"prompt": "Bzaseball galove.",
"category": "Misspellings",
```
OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_43.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/OpenJourney/sample_43.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_43.jpg" width="256" /> 
</p>

* This is how I would rate them:

**Case: Rating Long prompt image**
```
"prompt": "a beautiful photorealistic anime illustration of urbex industrial architecture city architecture unfinished building abandoned post office by renzo piano, laser extraterrestial sunset lake vaporwave elysian at night reclaimed by nature magic realism myst wilderness, archdaily, wallpaper, highly detailed, trending on artstation. ",
"category": "Misc",
```

OutputA|OutputB|OutputC

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_95.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_95.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/OpenJourney/sample_95.jpg" width="256" /> 
</p>

* This is how I would rate them:


