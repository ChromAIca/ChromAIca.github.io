## **Human Eval - Text-To-Image**

* Semantic Consistency (SC) scoring for **Text-To-Image**:
    * SC=2 : The image perfectly matched with the prompt, or the image matched with all the subject, action, position, adjective, style words in the prompt.
    * SC=1 : The image only matched with all the subject, action, and position words in the prompt, but missed some adjective (e.g. wrong color)
    * SC=0.5 : the image match with some of the subject, action, and position words in prompt.
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

Case: 