---
title: '[LR] Predicting Whole-Brain Neural Dynamics from Prefrontal Cortex fNIRS Signal'
date: 2025-03-17T15:32:01+08:00
draft: false
tags: ["fNIRS", "fMRI", "Neuroscience"]
---

[This review is intended solely for my personal learning]

Paper Info  
> DOI: [10.1101/2024.11.17.623979](https://doi.org/10.1101/2024.11.17.623979)  
> Title: Predicting whole-brain neural dynamics from prefrontal cortex fNIRS signal during movie-watching  
> Authors: Shan Gao, Ryleigh Nash, Shannon Burns, Yuan Chang Leong  

## Prior Knowledge
Functional near-infrared spectroscopy (fNIRS) offers a more accessible alternative to functional magnetic resonance imaging (fMRI) but is limited by shallow cortical penetration. Prior research has demonstrated potential in predicting deep-brain fMRI signals from fNIRS data through linear predictive models trained on simultaneous fMRI and fNIRS measurements.

## Goal
The primary goal of this study was to develop and validate a predictive model capable of mapping localized fNIRS signals from the prefrontal cortex (PFC) to whole-brain neural dynamics measured by fMRI during naturalistic tasks, specifically movie-watching. This approach aims to overcome the spatial limitations of fNIRS by inferring neural activity in deeper and distant brain regions from accessible cortical signals.

## Method
The study employed fNIRS data collected from 29 participants as they watched a 48-minute episode from a television series, paired with publicly available fMRI data from participants watching the same content. The analysis involved:

- Principal Component Regression (PCR) modeling to map prefrontal fNIRS signals onto whole-brain fMRI signals.
- Model training using the first half of the episode and testing on a separate held-out participant watching the second half, evaluating cross-individual and cross-stimulus generalization.
- Semantic analysis by encoding narrative content into vector embeddings, testing if the predicted fMRI time courses retained semantic information.
- Assessments of model predictions through correlations between observed and predicted fMRI activity and inter-subject functional connectivity (ISFC).

## Results
The predictive model successfully inferred fMRI activity significantly above chance in 66 out of 122 brain regions, including areas inaccessible to fNIRS, such as the temporal poles, precuneus, posterior cingulate cortex, and basal ganglia. The model achieved the highest accuracy in the default mode and control networks, consistent with their roles in higher-order cognition and narrative processing.

The predicted fMRI data replicated inter-subject functional connectivity patterns observed in the actual fMRI data (ISFC correlation: r = 0.42, p < .001). Semantic encoding analyses demonstrated that predicted fMRI signals retained meaningful semantic information, especially in language processing regions and the dorsomedial prefrontal cortex.

## Limitations
- The model's reliance on naturalistic stimuli may limit generalizability to different contexts or cognitive tasks, particularly those engaging regions underrepresented in the current stimuli, such as somatomotor areas.
- Idiosyncratic neural responses, notably in regions like the ventromedial prefrontal cortex, were less effectively predicted due to inherent variability between individuals.
- Predictive accuracy might benefit from the use of individual-specific modeling approaches, possibly requiring simultaneous fNIRS and fMRI recordings for optimization.

---

## Reference
- The paper: [https://doi.org/10.1101/2024.11.17.623979](https://doi.org/10.1101/2024.11.17.623979)
- This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.

