---
title: "[LR] Steering Language Models With Activation Engineering"
date: 2025-03-26T20:12:03+08:00
draft: false
tags: ["Large Language Models", "Activation Engineering"]
---

[This review is intended solely for my personal learning]

## Paper Info
> arXiv: 2308.10248  
> Title: Steering Language Models With Activation Engineering  
> Authors: Alexander Matt Turner, David Udell, Nantas Nardelli, Sam Ringer, Tom McGrath, Eric Michaud, Mantas Mazeika

## Prior Knowledge
- **Steering Language Models**: Traditionally achieved through techniques such as prompt engineering, fine-tuning, and reinforcement learning from human feedback (RLHF), which often require substantial computational resources and specialized datasets.
- **Internal Activation Manipulation**: Exploring internal activations of neural networks can offer fine-grained control over their outputs without the cost associated with retraining or extensive model tuning.

## Goal
The paper aims to introduce and validate a lightweight inference-time technique, termed **Activation Addition (ActAdd)**, for steering the output of large language models (LLMs). This method targets latent capabilities of LLMs, such as controlled sentiment expression or reduced output toxicity, without the need for additional training.

## Method
The proposed Activation Addition method comprises the following steps:

1. **Contrast Pair Selection**: Identify pairs of prompts with opposite desired attributes (e.g., positive vs. negative sentiment).
2. **Activation Extraction**: Run each prompt pair through the LLM and record their internal activations.
3. **Steering Vector Computation**: Compute a steering vector by calculating the activation difference between the two contrasting prompts.
4. **Inference-Time Activation Modification**: At inference, add this steering vector to the internal activations of the LLM to steer the model’s output toward the desired attribute.

By directly manipulating the model's internal states, ActAdd provides a precise mechanism for controlling output attributes during inference.

## Results
- **Sentiment Control**: ActAdd effectively steered LLM outputs toward positive or negative sentiment, achieving precise control over generated text sentiment.
- **Detoxification Performance**: Significantly reduced generation of toxic outputs, surpassing or matching the performance of established detoxification methods across various models (e.g., LLaMA-3, OPT).
- **Preservation of General Performance**: ActAdd modifications did not negatively impact model performance on unrelated tasks, indicating targeted and selective intervention.

## Limitations
- **Dependence on Contrast Pair Quality**: ActAdd requires carefully chosen contrastive prompts; ineffective selection could limit its applicability or performance.
- **Generalizability Concerns**: Effectiveness across different models and broader tasks beyond those tested remains an area requiring further exploration.
- **Interpretability Challenges**: While the technique is practically effective, understanding the specific internal mechanisms and impacts of activation manipulations remains complex.

Future work may focus on exploring the applicability and robustness of activation engineering.

---

## Reference
- The paper: [https://arxiv.org/abs/2308.10248](https://arxiv.org/abs/2308.10248)
- This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.

