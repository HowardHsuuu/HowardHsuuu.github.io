---
title: "[LR] LLMs Enhancement via Negative Emotional Stimuli"
date: 2024-11-02T20:02:13+08:00
draft: false
tags: ["Large Language Model"]
---

[This review is intended solely for my personal learning]

## Paper Info
> arXiv: 2405.02814  
> Title: NegativePrompt: Leveraging Psychology for Large Language Models Enhancement via Negative Emotional Stimuli  
> Authors: Xu Wang, Cheng Li, Yi Chang, Jindong Wang, Yuan Wu  

## Prior Knowledge  
- **Emotion and Cognition in AI**: Previous research has shown that positive emotional stimuli improve LLM performance, raising the question of whether negative emotional stimuli can also have an impact.
- **Psychological Theories**: The study draws on Cognitive Dissonance Theory, Social Comparison Theory, and Stress and Coping Theory to design negative emotional prompts that may influence LLM responses.

## Goal  
To explore whether negative emotional stimuli, integrated into prompts, can enhance the performance of LLMs across various NLP tasks. The study introduces *NegativePrompt*, a novel prompting technique that applies negative emotional cues to improve LLM output quality.

## Method  
- **Design of NegativePrompt**: Ten different negative emotional stimuli were crafted based on psychological theories:
  - *Cognitive Dissonance Theory* (NP01-NP05): Phrases inducing internal conflict to prompt corrective action.
  - *Social Comparison Theory* (NP06-NP07): Phrases that encourage competition and improvement by comparing performance with others.
  - *Stress and Coping Theory* (NP08-NP10): Stimuli that introduce stress-related scenarios to examine adaptation.
- **Experimental Setup**: Five LLMs (Flan-T5-Large, Vicuna, Llama 2, ChatGPT, GPT-4) were tested on 24 Instruction Induction and 21 BIG-Bench tasks. The effectiveness of NegativePrompt was evaluated against standard prompts and alternative prompt-engineering techniques.
- **Evaluation Metrics**:
  - Accuracy in task completion (Instruction Induction and BIG-Bench benchmarks)
  - Truthfulness and informativeness (TruthfulQA benchmark)
  - Attention visualization to understand how negative emotional stimuli impact model focus

## Results  
1. **Performance Improvement**:
   - NegativePrompt led to **12.89% improvement** in Instruction Induction tasks and **46.25% improvement** in BIG-Bench tasks.
   - Few-shot learning tasks benefited more from NegativePrompt than zero-shot tasks.
2. **Truthfulness and Informativeness**:
   - NegativePrompt increased truthfulness scores by **14%** and informativeness scores by **6%**, suggesting that negative stimuli encourage more cautious and precise responses.
3. **Impact of Psychological Theories**:
   - *Cognitive Dissonance Theory*-based prompts were the most effective in inducing improvements.
   - *Social Comparison Theory* stimuli had mixed results, with some cases improving performance while others led to negative effects.
   - *Stress and Coping Theory* prompts had minimal influence on LLM behavior.
4. **Attention Analysis**:
   - LLMs exhibited increased attention to task-critical elements when exposed to negative stimuli, indicating a shift in focus due to the prompts.

## Conclusion  
NegativePrompt successfully enhances LLM performance by leveraging psychological insights into negative emotional stimuli. The findings suggest that while LLMs do not experience emotions in the same way as humans, they exhibit behavior shifts that align with human responses to motivation-driven stimuli.

## Limitations  
1. **Generalization Across Models**: The results vary between LLMs, with some models responding better to negative stimuli than others.

## Reproduction

We (BrainLLM research group at NTU MSLAB) tried to reproduce the result of this paper on smaller models. Here's the [repo](https://github.com/HowardHsuuu/NegativePrompt-Replication/tree/mistral-experiment)

## Reference  
* The paper: https://arxiv.org/abs/2405.02814
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.