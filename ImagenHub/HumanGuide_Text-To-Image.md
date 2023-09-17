## **Human Eval - Text-To-Image**

* Semantic Consistency (SC) scoring for **Text-To-Image**:
    * SC=2 : The image perfectly matched with the prompt, or the image matched with all the subject, action, position, adjective, style words in the prompt.
    * SC=1 : The image only matched with all the subject, action, and position words in the prompt, but missed some adjective (e.g. wrong color)
    * SC=0.5 : the image match with some of the subject, action, and position words in prompt, but the overall idea is wrong.
    * SC=0 : The image failed to match any of the subject, action, and position words in the prompt.
* Perceptual Realism (PR) scoring for **Text-To-Image**:
    * PR=2 : Exhibiting reasonable lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : only minor distortion found on high-level features / small objects (e.g. subject faces, small words, unusual number of fingers etc)
    * PR=0.5 : some wrong body portions spotted but still be able to identify the object.
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

OutputA|OutputB|OutputC|OutputD

<p float="left", align="center">
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DALLE/sample_9.jpg" width="256" />
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/DeepFloydIF/sample_9.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SD/sample_9.jpg" width="256" /> 
<img src="https://chromaica.github.io/ImagenHub/ImagenHub_Text-To-Image/SDXL/sample_9.jpg" width="256" /> 
</p>

* This is how I would rate them:
* OutputA: `[0.5, 2] `. SC: panda should be the one making the art instead of being in the latte. Only panda and latte words matched but not panda making latte art. PR: No distortion found.
* OutputB: `[0.5, 2]`. SC: panda should be the one making the art instead of being in the latte. Only panda and latte words matched but not panda making latte art. PR: No distortion found.
* OutputC: `[0.5, 1]`. SC: panda is drinking instead of making latte art. PR: minor distortion found on the panda's hand.
* OutputD: `[2, 1]`. SC: The prompt match perfectly with the image. PR: minor distortion found on the panda's left hand.