---
title: "[LR] Swarm Intelligence for EEG Channel Selection in Emotion Recognition"
date: 2025-03-22T19:21:17+08:00
draft: false
tags: ["Brain–Computer Interface", "EEG"]
---

[This review is intended solely for my personal learning]

Paper Info  
> DOI: [10.1007/978-3-031-05409-9_23](https://doi.org/10.1007/978-3-031-05409-9_23)  
> Title: A Swarm Intelligence Approach: Combination of Different EEG-Channel Optimization Techniques to Enhance Emotion Recognition  
> Authors: Sabahudin Balic, Lukas Kleybolte, and Christian Märtin


## Prior Knowledge
- **EEG-based Emotion Recognition**: EEG captures electrical brain activity via multiple electrodes. Its high temporal resolution makes it suitable for decoding emotional states in real-time. However, the full 32-channel setup is often computationally expensive and redundant.
- **Swarm Intelligence**: Algorithms like Particle Swarm Optimization (PSO), Cuckoo Search (CS), and Grey Wolf Optimizer (GWO) mimic social behavior of animals to solve optimization problems.
- **Feature vs. Channel Selection**: Traditional feature selection targets discriminative features across frequency bands, while channel selection focuses on spatially optimizing electrode positions.

## Goal
To evaluate and compare different EEG channel selection techniques—both classical and swarm intelligence-based—to optimize emotion classification performance while significantly reducing computation time.

## Method
### Dataset & Emotion Model
- **DEAP Dataset**: 32-channel EEG recordings from 40 subjects watching 32 emotion-evoking music videos.
- **Emotion Labels**: Based on Russell’s Circumplex Model, which maps emotions in 2D space using Arousal and Valence dimensions (High/Low quadrants).
### Preprocessing & Feature Extraction
- EEG signals were downsampled to 128 Hz, filtered (4–45 Hz), and segmented into 2s windows (256 points) with 0.125s overlap.
- FFT was used to extract power across five bands: δ, θ, α, β, γ.
- Feature set: 160 features (32 channels × 5 bands).
### Channel Selection Techniques
- **Classical Methods**:
  - *PCA*: Unsupervised, variance-preserving projection.
  - *mRMR*: Supervised mutual information-based selection maximizing relevance and minimizing redundancy.
- **Swarm Intelligence Methods**:
  - *PSO*: Simulates bird/fish social movement.
  - *CS*: Inspired by cuckoo parasitism with Lévy flights for global exploration.
  - *GWO*: Mimics hierarchical grey wolf hunting behavior.
Each method selected the top 20 out of 32 EEG channels.

### Classifier
- **Bidirectional LSTM**:
  - Four LSTM layers (first bidirectional), interspersed with dropout.
  - Dense layers for binary classification of arousal and valence.
  - Trained for 200 epochs using Adam optimizer.

## Results
- **mRMR** emerged as the most time-efficient method with minimal accuracy trade-off.
- **Cuckoo Search** achieved the highest accuracy, albeit with higher selection time.
- Reducing to only 10 channels with CS still yielded 91.32% (arousal) and 91.84% (valence), cutting training to ~4h.

## Limitations
- **Homogeneous Channel Count**: Fixed reduction to 20 channels across all subjects limits the adaptive power of swarm intelligence.
- **Swarm Methods are Costly**: CS and GWO, while accurate, introduce 4–7h additional selection time per subject.
- **Lack of Real-time Testing**: Results are from offline DEAP dataset; online or real-world deployment was not evaluated.

## Reference
* The paper: https://doi.org/10.1007/978-3-031-05409-9_23  
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.