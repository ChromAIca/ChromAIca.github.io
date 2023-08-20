# Human Evaluation Guide

> Our Evaluation Guide is extended from the evaluation standard in [DreamEdit](https://arxiv.org/abs/2306.12624).

## Evaluation Guide for Human Evaluators

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
* VF=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence.
* VF=1 : Nearly no distortion, incompletion found. including sense of distance, lighting or shadow details.
* VF=0.5 : Minor distortion, incompletion or other visual flaws (e.g. watermark) can be spotted but do not strongly detract from its overall appearance.
* VF=0 : Obvious noise, distortion, or incompletion can be spotted.


### Task-Specific Guide for scoring:

In the Task-Specific Scoring Guide we outline the details of the score judgement.

**Text-Guided Image Editing**
* Semantic Consistency (SC) scoring for **Text-Guided Image Editing**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, without unnecessary edits.
    * SC=1 : The generated image perfectly described all the required attributes but having unnecessary edits.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed in following the key instruction in editing, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Text-Guided Image Editing**:
    * VF=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * VF=1 : Image generally look real but with minor visual flaws on trivial objects.
    * VF=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * VF=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.


**Mask-Guided Image Editing**
* Semantic Consistency (SC) scoring for **Mask-Guided Image Editing**:
    * SC=2 : The generated image perfectly described all the required attributes of the user prompt, without unnecessary edits.
    * SC=1 : The generated image perfectly described all the required attributes but having unnecessary edits.
    * SC=0.5 : Some required attributes appeared on the generated image but in a unnatural sense or seems incomplete.
    * SC=0 : The generated image failed in following the key instruction in editing, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Mask-Guided Image Editing**:
    * VF=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence. No distortion found.
    * VF=1 : Image generally look real but with minor visual flaws on trivial objects.
    * VF=0.5 : Minor distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted on important objects but do not strongly detract from its overall appearance.
    * VF=0 : Large portion of noise, distortion, incompletion or other visual flaws (e.g. blurry or look unrealistic) can be spotted.


**Subject-Driven Image Editing**
* Semantic Consistency (SC) scoring for **Subject-Driven Image Editing**:
    * SC=2 : Subject accurately represents the intended subject, closely matching all visual characteristics.
    * SC=1 : Subject somewhat represents the intended subject, mismatch low-level features such as facial/texture details.
    * SC=0.5 : Subject partially resembles the intended subject, mismatch high-level features such as colors, body proportions. 
    * SC=0 : Subject bears little resemblance to the intended subject, or result in a completely different background.
* Perceptual Realism (PR) scoring for **Subject-Driven Image Editing**:
    * VF=2 : Exhibiting realistic lighting, shadows, texture details, correct sense of distance and overall visual coherence.
    * VF=1 : 
    * VF=0.5 : 
    * VF=0 : Large portion of noise, distortion, or incompletion can be spotted on the object or in the background.


**Multi-Subject-Driven Image Generation**
* Semantic Consistency (SC) scoring for **Multi-Subject-Driven Image Generation**:
    * SC=2 :
    * SC=1 :
    * SC=0.5 : 
    * SC=0 : 
* Perceptual Realism (PR) scoring for **Multi-Subject-Driven Image Generation**:
    * VF=2 : 
    * VF=1 : 
    * VF=0.5 : 
    * VF=0 : Obvious noise, distortion, or incompletion can be spotted.


**Control-Guided Image Generation**
* Semantic Consistency (SC) scoring for **Control-Guided Image Generation**:
    * SC=2 :
    * SC=1 :
    * SC=0.5 : 
    * SC=0 : 
* Perceptual Realism (PR) scoring for **Control-Guided Image Generation**:
    * VF=2 : 
    * VF=1 : 
    * VF=0.5 : 
    * VF=0 : Obvious noise, distortion, or incompletion can be spotted.


**Style-Guided Image Generation**
* Semantic Consistency (SC) scoring for **Style-Guided Image Generation**:
    * SC=2 : Aesthetic styles match accurately including color palette, stroke type, and paint type. And image perfectly matches to the user prompt.
    * SC=1 : Aesthetic styles match accurately including color palette, stroke type, and paint type. but image missing minor objects to the user prompt.
    * SC=0.5 : Aesthetic styles bears partial resemblance.
    * SC=0 : Obvious aesthetic styles completely mismatch or object mismatch to the user prompt.
* Perceptual Realism (PR) scoring for **Style-Guided Image Generation**:
    * VF=2 : 
    * VF=1 : Nearly no distortion, incompletion found. including sense of distance, lighting or shadow details.
    * VF=0.5 : Minor distortion, incompletion or other visual flaws (e.g. watermark) can be spotted but do not strongly detract from its overall appearance.
    * VF=0 : Obvious noise, distortion, or incompletion can be spotted.


**Subject-Driven Image Generation**
* Semantic Consistency (SC) scoring for **Subject-Driven Image Generation**:
    * SC=2 : Subject accurately represents the intended subject, and the background perfectly matches to the user prompt. 
    * SC=1 : Subject mismatch low-level features such as facial/texture details of the intended subject. But the background matches to the user prompt.
    * SC=0.5 : Subject mismatch high-level features such as colors and body proportions of the intended subject. But the background matches to the user prompt.
    * SC=0 : Subject bears little resemblance to the intended subject, or the background does not align to the user prompt.
* Perceptual Realism (PR) scoring for **Subject-Driven Image Generation**:
    * VF=2 : Exhibiting realistic lighting, shadows, texture and background details, and overall visual coherence.
    * VF=1 : 
    * VF=0.5 : 
    * VF=0 : Obvious noise, distortion, or incompletion can be spotted.


### Frequently Asked Questions (FAQ)
TBA

## Human Evaluation Design Rationale

### Score Design

We set 
* Score=2: Having some desire properties hopefully the field will push toward to (what the majority of SOTA models were not capable of generating those consistently)
* Score=1: Decent but not perfect results
* Score=0.5: for minor flaws
* Score=0: for serious flaws.
