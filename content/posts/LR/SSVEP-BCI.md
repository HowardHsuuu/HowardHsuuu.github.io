---
title: "[LR] Binocular Vision SSVEP BCI for Dual-Frequency Modulation"
date: 2024-10-12T20:32:51+08:00
draft: false
tags: ["Brain–Computer Interface", "SSVEP"]
---

[This review is intended solely for my personal learning]

Paper Info
> DOI: 10.1109/TBME.2022.3212192  
> Title: A Binocular Vision SSVEP Brain–Computer Interface Paradigm for Dual-Frequency Modulation  
> Authors: Yike Sun, Liyan Liang, Jingnan Sun, Xiaogang Chen, Runfa Tian, Yuanfang Chen, Lijian Zhang, and Xiaorong Gao  

## Prior Knowledge
- **SSVEP and BCIs:** Steady-State Visual Evoked Potentials (SSVEPs) are brain responses elicited by periodic visual stimuli. Their robustness and high signal-to-noise ratio make them a cornerstone in non-invasive BCI research
- **Dual-Frequency Stimulation:** Traditional dual-frequency paradigms, such as the checkerboard arrangement, allow the encoding of more targets but are hampered by intermodulation artifacts, which can compromise signal quality.
- **Binocular Vision Approach:** By using circularly polarized light to deliver different frequencies to each eye, the binocular vision paradigm minimizes interference from intermodulation harmonics, thereby enhancing signal fidelity.

## Goal
To design and evaluate a novel dual-frequency SSVEP paradigm based on binocular vision that suppresses intermodulation harmonics and enhances overall BCI performance, particularly in training-free applications.

## Method
The study was structured around two primary experiments:
1. **Experiment 1: Offline SNR Analysis**
   - **Participants:** 9 subjects.
   - **Design:** A 6-target experiment comparing the binocular vision paradigm with the traditional checkerboard arrangement.
   - **Measurements:** Signal-to-noise ratios (SNR) were calculated for broadband, narrowband, and intermodulation components to assess the quality of the evoked potentials.

2. **Experiment 2: Online BCI Evaluation**
   - **Participants:** 12 subjects.
   - **Design:** A 40-target training-free online experiment.
   - **Analysis:** Utilized a customized Filter Bank Dual-Frequency Canonical Correlation Analysis (FBDCCA) algorithm to decode the SSVEP responses, with additional offline analysis using Task-Related Component Analysis (TRCA) for comparison.

Stimuli were presented on a circularly polarized display, where alternating odd and even rows contained different frequencies, ensuring each eye received a distinct stimulus.

## Results
- **Improved Signal Quality:**  
  The binocular vision paradigm yielded significantly higher broadband and narrowband SNRs, and reduced intermodulation noise by approximately 2 dB compared to the traditional checkerboard setup.
  
- **Enhanced BCI Performance:**  
  In the online experiment, the training-free system achieved an average Information Transfer Rate (ITR) of 104.56 bits/min—nearly double that of the conventional approach. Offline analyses further confirmed the robustness of the binocular paradigm.

- **Effective Algorithm Adaptation:**  
  The tailored FBDCCA algorithm successfully decoded dual-frequency responses, providing high classification accuracy without the need for extensive training.

## Conclusion
This study demonstrates that the binocular vision approach can effectively suppress intermodulation harmonics, resulting in improved SSVEP signal quality and enhanced BCI performance. The innovative integration of hardware (circularly polarized displays) and the specialized FBDCCA algorithm paves the way for scalable, training-free BCI systems capable of handling a larger number of targets.

## Limitations
The study was conducted under controlled laboratory conditions with specialized hardware like circularly polarized displays, which might limit its immediate real-world application. Moreover, the small sample size calls for further research with a more diverse population to validate the results. Future work should also focus on expanding the scope of the FBDCCA algorithm to ensure its effectiveness across various dual-frequency paradigms and BCI configurations, thereby enhancing the practical utility of the approach.

---

## Reference
* The paper: https://ieeexplore.ieee.org/document/9911680
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.