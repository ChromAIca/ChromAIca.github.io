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

## Example

