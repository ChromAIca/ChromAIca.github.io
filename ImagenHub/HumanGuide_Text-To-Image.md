## **Human Eval - Text-To-Image**

* Semantic Consistency (SC) scoring for **Text-To-Image**:
    * SC=2 : The image perfectly matched with the prompt, or the image matched with all the subject, action, position, adjective, style words in the prompt.
    * SC=1 : The image only matched with all the subject, action, counting, and position words in the prompt, but missed some adjective (e.g. wrong color)
    * SC=0.5 : the image match with some of the subject, action, counting, and position words in prompt, but the overall idea is wrong.
    * SC=0 : The image failed to match any of the subject, action, and position words in the prompt.
* Perceptual Realism (PR) scoring for **Text-To-Image**:
    * PR=2 : Exhibiting reasonable lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : only minor distortion found on high-level features / small objects (e.g. subject faces, small words, unusual number of fingers etc)
    * PR=0.5 : some wrong body portions spotted but still be able to identify the object, or a sense of unnatural feeling exists.
    * PR=0 : The image is heavily distorted, or huge potion of artifacts appeared. Just anything we can clearly tell its AI-generated at first glance.

### **Examples / Common cases when evaluating: Text-To-Image**
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
* OutputB: `[0, 0.5]`. SC=0: Failed to generate refrigerator nor the stop sign. PR=0.5: The whole thing looks unnatural.
* OutputC: `[2, 1]`. SC=2: The prompt match perfectly with the image.  PR=1 or 2: The stop sign looks like pinned on the wall with an unnatural angle.



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
* OutputA: `[0.5, 1] `. SC=0.5: A sign appeared, but failed to spell the word.  PR=1: The image look generally real but with some lighting issues.
* OutputB: `[0.5, 0.5]`. SC=0.5: A sign appeared, but failed to spell the word.  PR=0.5: The background looks so unnatural.
* OutputC: `[0.5, 0]`. SC=0.5: A sign appeared, but failed to spell the word.  PR=0.5: Heavy distortion on both text and strong artifacts in the background.


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

* The prompt should mean "Baseball glove". This is how I would rate them:
* OutputA: `[2, 2] `. SC=2: It is a baseball glove. PR=2 or 1: It looks highly resemble to a baseball glove.
* OutputB: `[0, 0.5]`. SC=0 or 0.5: It's just some balls, not even a baseball. PR=0.5: The balls are stacking in an unnatural way.
* OutputC: `[0, 0]`. SC=0: It looks similar to a baseball court but no baseball nor glove appeared in the image. PR=0 or 0.5: The image is heavily distorted as the objects cannot be recognized.


**Case: Rating Long prompt image**

Long prompt ratings are highly subjective.

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

* Let's analyze the prompt.
* style: photorealistic, anime, renzo piano, vaporwave
> This is how the renzo piano building looks like (just by googling). We can assume its some kind of industrial building.
> <p float="left", align="center">
> <img src="https://images.adsttc.com/media/images/57d9/66c5/e58e/ce72/2b00/01e9/newsletter/2496569412_97e61ae248_o.jpg?1473865406" width="256" /> 
> <img src="https://images.adsttc.com/media/images/55f6/78a4/e58e/cec1/f800/008e/large_jpg/626.008.jpg?1442216093" width="256" /> 
> </p>
> This is how vaporwave looks like (just by googling). We can assume it is a style dominated by a mixture of purple-like colors.
> <p float="left", align="center">
> <img src="https://esq.h-cdn.co/assets/16/33/1280x960/sd-aspect-1471537670-es-081716-vaporwave.jpg" width="256" /> 
> <img src="https://retro.nativ3.io/wp-content/uploads/2021/05/5155536-1536x1024.jpg" width="256" /> 
> </p>
* Then we can get the idea of the prompt (it's subjective): an illustration of unfinished/abandoned renzo piano style industrial building, sunset vaporwave
* This is how I would rate them:
* OutputA: `[2, 1] `. SC=2 or 1: The image showed the industrial building, the sunset, and the vaporware (mixed with anime) feeling. PR=0.5: The ground and the bridge on the top look distorted and give an unnatural feeling.
* OutputB: `[2, 1]`. SC=2 or 1: The image showed the industrial building, the sunset, and the vaporware feeling. PR=1: The image generally looks real and with nice reflection, but the roof lighting looks unnatural.
* OutputC: `[0.5, 0.5]`. SC=0.5:  The image showed the sunset, and the vaporware (mixed with anime) feeling, but a building is not found. PR=0.5: The trees appeared in an unnatural way. Also, artifacts appeared on the railings.

