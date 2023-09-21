# Simple Human Evaluation Guide

This is the Simple Human Evaluation Guide.

The Human Rating design has to be 
* Easy to follow
* Fast to rate

# Simple Evaluation Guide for Human Evaluators

One for All task:

To standardize the conduction of a rigorous human evaluation, we stipulate the criteria for each measurement as follows:
* Semantic Consistency (SC), score in range `[0, 0.5, 1]`
* Perceptual Realism (PR), score in range `[0, 0.5, 1]`


Semantic Consistency (SC) ensures that the generated image is coherent in terms of guidance provided (i.e. Prompts, Subject Token, etc.). In another words, the image has to be aligned with the requirements provided in user's inputs.

Perceptual Realism (PR) ensures the generated image align with real-world characteristics. In another words, the image has to be visually convincing and closely resembles a real photograph (Photorealism).

Rules for Semantic Consistency (SC) scoring:

* SC=0 : Image completely not following one or more of the conditions at all (e.g. not following the prompt at all, different background in editing task, wrong subject in subject-driven task etc)
* SC=0.5 : all the conditions are partly following the requirements.
* SC=1 : All the conditions are following >75% of the requirement. You agree that the overall idea is correct.

Rules for Perceptual Realism (PR) scoring:
* PR=0: Obvious distortion / artifacts at first glance
* PR=0.5: Unnatural sense of detail feeling in some area (e.g. body portion was wrong, textures, backgrounds, small color difference, watermark, wrong object size etc.) but not as bad as artifacts.
* PR=1: You agree that the image generally look real (doesn't have to be 100% perfect. Like 90% is good enough.)

## Detail explanation of SC scoring.

In image generations, we provide user input (conditions) to guide the image. The conditions can be different according to the task.
![image](https://github.com/ChromAIca/ChromAIca.github.io/assets/34955859/6c2e9b84-3375-4354-b6f7-4a80569ae252)

This is how we decide the SC score to judge whether the conditions are fulfilling the requirement:

| Condition 1                 | Condition 2 (if applicable) | Condition 3  (if applicable)| SC rating |
|-----------------------------|-----------------------------|-----------------------------|-----------|
| no following at all         | Any                         | Any                         | 0         |
| Any                         | no following at all         | Any                         | 0         |
| Any                         | Any                         | no following at all         | 0         |
| following some part         | following some or most part | following some or most part | 0.5       |
| following some or most part | following some part         | following some or most part | 0.5       |
| following some part or more | following some or most part | following some part         | 0.5       |
| following most part         | following most part         | following most part         | 1         |

## Detail explanation of PR scoring.

This is how we decide the PR score to judge whether the image looks real:

| Artifacts           | Unusual sense       | PR rating |
|---------------------|---------------------|-----------|
| obvious             | Any                 | 0         |
| not obvious         | some or little      | 0.5       |
| None                | little or None      | 1         |

* Artifacts should be something that you were able to spot at first glance. It includes:
  * Distortion, watermark, scratches, subject merged, unusual body parts, art style not harmonized etc.
* Unusual sense should be something that you were not able to spot at first glance. It includes:
  * image not harmonized, wrong shadow, wrong lighting, wrong sense of distance etc.
