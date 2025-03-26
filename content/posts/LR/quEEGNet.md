---
title: "[LR] quEEGNet: QAI for Biosignal Processing"
date: 2025-02-11T19:51:02+08:00
draft: false
tags: ["Quantum Machine Learning", "EEG"]
---

[This review is intended solely for my personal learning]

Paper Info
> arXiv: 2210.00864v1  
> Title: quEEGNet: Quantum AI for Biosignal Processing  
> Authors: Toshiaki Koike-Akino, Ye Wang  

## Prior Knowledge
### **Biosignal Processing in Human-Machine Interfaces (HMI)**
Biosignals such as EEG (electroencephalogram), EMG (electromyogram), and ECoG (electrocorticogram) are fundamental to developing brain-computer interfaces (BCI) and HMIs. However, biosignals are subject to high variability and noise, requiring robust machine-learning models for feature extraction and classification.

### **Challenges in Biosignal Processing**
- **High inter-subject variability** necessitates frequent recalibration.
- **Computational inefficiency** of deep learning models in resource-constrained environments.
- **Scalability and generalization** remain concerns in BCI applications.

## Goal
The paper introduces a **hybrid quantum-classical deep learning model** called **quEEGNet**, which integrates a variational quantum circuit (VQC) into a deep neural network (DNN) for biosignal analysis. The key objectives are:
1. Demonstrating **quantum-enhanced feature extraction** for EEG, EMG, and ECoG.
2. **Reducing the number of trainable parameters** while maintaining high classification accuracy.
3. Providing a **proof-of-concept study** showcasing quantum computing’s applicability in HMI/BCI.

## Method
### **Quantum Artificial Intelligence (QAI) Framework**
1. **Quantum Neural Network (QNN) Architecture**:
   - The model integrates **VQC-based feature extraction** into a classical DNN.
   - A **hybrid training strategy** is used where VQC layers are optimized alongside DNN layers.

2. **Variational Quantum Circuit (VQC) Design**:
   - Employs **Pauli-Y rotations** and **controlled-Z entanglement layers** for quantum state evolution.
   - Uses **Simplified 2-Design (S2D) ansatz** to mitigate barren plateau issues.

3. **Hybrid Quantum-Classical Processing**:
   - EEG/EMG/ECoG signals are preprocessed and embedded into quantum states.
   - QNN performs feature transformation before passing the output to EEGNet, a well-known deep learning model for biosignal classification.

### **Experimental Setup**
- **Datasets**: Multiple publicly available physiological datasets (EEG, EMG, ECoG) were used for evaluation.
- **Baseline Comparison**: The model is benchmarked against **EEGNet**, a classical convolutional neural network.
- **Training Details**:
  - Optimized using **Adam optimizer** with a learning rate of 0.1.
  - Implemented using **PennyLane** and **PyTorch**.
  - Quantum circuits simulated due to current hardware constraints.

## Results
| **Dataset**  | **EEGNet Accuracy (%)** | **quEEGNet Accuracy (%)** |
|-------------|-----------------|-----------------|
| Stress      | 85.87           | **87.23**       |
| RSVP        | 93.73           | **95.12**       |
| MI          | 59.61           | **60.22**       |
| ErrP        | 74.36           | **75.92**       |
| Faces Basic | 63.30           | **64.92**       |
| Faces Noisy | 75.94           | **78.01**       |
| ASL         | 23.64           | **25.16**       |

- **Performance Improvement**: quEEGNet outperformed EEGNet across all datasets, demonstrating the effectiveness of quantum-assisted feature extraction.
- **Parameter Efficiency**: The model **reduces the number of trainable parameters** while maintaining competitive performance.
- **Computational Trade-offs**: While QNN offers advantages in parameter efficiency, the practical speedup depends on the maturity of quantum hardware.

## Conclusion
The study presents **quEEGNet** as a pioneering effort in applying **quantum AI to biosignal processing**. By integrating **variational quantum circuits into deep learning models**, the approach achieves **state-of-the-art performance** across multiple datasets while maintaining computational efficiency. This work establishes **QML as a viable direction for future BCI and HMI applications**.

## Limitations
1. **Quantum Hardware Constraints**:
   - Experiments were conducted on **simulated quantum processors**, which may not fully reflect real-world hardware performance.
   - The practical deployment of quEEGNet depends on advancements in **near-term quantum computing**.
2. **Scalability**:
   - While the hybrid model **reduces parameter count**, the benefits of QNNs over classical DNNs are **not yet definitive**.
   - Further optimization, such as **AutoQML**, is necessary to enhance generalization.
3. **Limited Variants of QNN**:
   - Only one type of VQC architecture was explored.
   - Future work should investigate alternative quantum ansatz and hybrid architectures.

## References
- The paper: https://arxiv.org/abs/2210.00864
- This review was written with the assistance of Generative AI and is based on the content and results presented in the original paper.
