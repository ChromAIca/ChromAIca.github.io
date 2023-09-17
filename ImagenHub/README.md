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


Important: Please refer to [HumanGuide_Text-To-Image.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Text-To-Image.md) for more detail and examples.

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

Important: Please refer to [HumanGuide_Text-Guided_IE.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Text-Guided_IE.md) for more detail and examples.





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

Important: Please refer to [HumanGuide_Mask-Guided_IE.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Mask-Guided_IE.md) for more detail and examples.

## **Human Eval - Subject-Driven Image Editing**

* Semantic Consistency (SC) scoring for **Subject-Driven Image Editing**:
    * SC=2 : Subject accurately represents the intended subject, closely matching all visual characteristics. And the result preserves the source background well.
    * SC=1 : Subject somewhat represents the intended subject, mismatch low-level features such as facial/texture details. Or there are minor change in background.
    * SC=0.5 : Subject partially resembles the intended subject, mismatch high-level features such as colors, body proportions. Or there are easily observable change in background.
    * SC=0 : Subject bears little resemblance to the intended subject, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Subject-Driven Image Editing**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, or incompletion can be spotted on the object or in the background.

Important: Please refer to [HumanGuide_Subject-Driven_IE.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Subject-Driven_IE.md) for more detail and examples.




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

Important: Please refer to [HumanGuide_Multi-Subject_IG.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Multi-Subject_IG.md) for more detail and examples.

## **Human Eval - Control-Guided Image Generation**

* Semantic Consistency (SC) scoring for **Control-Guided Image Generation**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, and even work
    * SC=1 : The generated image only described partial the required attributes.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed following every required attributes in the prompt. 
* Perceptual Realism (PR) scoring for **Control-Guided Image Generation**:
    * PR=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * PR=1 : Image generally look real but with minor visual flaws on trivial objects.
    * PR=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * PR=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.

Important: Please refer to [HumanGuide_Control-Guided_IG.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Control-Guided_IG.md) for more detail and examples.



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

Important: Please refer to [HumanGuide_Subject-Driven_IG.md](https://github.com/ChromAIca/ChromAIca.github.io/blob/main/ImagenHub/HumanGuide_Subject-Driven_IG.md) for more detail and examples.



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

