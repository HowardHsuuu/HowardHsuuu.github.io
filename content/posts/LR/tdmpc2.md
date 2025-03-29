---
title: "[LR] TD-MPC2"
date: 2024-11-21T20:32:33+08:00
draft: false
tags: ["Reinforcement Learning", "Robotics"]
---

[This review is intended solely for my personal learning]

Paper Info
> Title: TD-MPC2: Scalable, Robust World Models for Continuous Control  
> Authors: Nicklas Hansen, Hao Su, Xiaolong Wang  
> Conference: ICLR 2024  
> arXiv: 2310.16828  

## Prior Knowledge
- **Model-Based Reinforcement Learning (MBRL)**: Uses an internal model of the environment to plan and optimize actions rather than learning policies from direct interaction alone.
- **Temporal Difference Learning**: A method in RL that estimates the value function iteratively using bootstrapped learning.
- **Model Predictive Control (MPC)**: An optimization framework for selecting actions over a finite horizon using a learned world model.
- **TD-MPC**: A prior algorithm that performs local trajectory optimization in the latent space of an implicit world model but lacks scalability and robustness.

## Goal
The authors propose **TD-MPC2**, an extension of the TD-MPC framework, designed to scale reinforcement learning to large, uncurated datasets and generalize across multiple continuous control tasks. The key aims are:
1. **Algorithmic robustness**: Achieve strong performance across diverse tasks using a single set of hyperparameters.
2. **Scalability**: Ensure performance improves with increasing model and data sizes.
3. **Generalization**: Train a single agent to solve multiple continuous control problems across different action spaces and embodiments.

## Method
TD-MPC2 introduces several improvements over its predecessor:

### 1. **Learning an Implicit World Model**
TD-MPC2 employs a **decoder-free world model**, where observations are mapped into a **latent representation** $z$ and optimized using a combination of:
- **Joint-embedding prediction**: Encourages representations to be predictive without reconstructing observations.
- **Reward prediction**: Estimates task-specific rewards directly from the latent space.
- **Temporal Difference (TD) Learning**: Uses a learned value function to bootstrap future returns beyond the planning horizon.

The key components of the world model include:
- **Encoder** $z = h(s, e)$: Maps observations to latent states.
- **Latent dynamics** $z' = d(z, a, e)$: Predicts future latent states given an action.
- **Reward function** $r̂ = R(z, a, e)$: Predicts expected rewards.
- **Terminal value function** $q̂ = Q(z, a, e)$: Estimates long-term return.
- **Policy prior** $â = p(z, e)$: Provides an initial estimate of the best action.

### 2. **Model Predictive Control with a Policy Prior**
TD-MPC2 integrates **MPC** with a learned policy prior to optimize actions iteratively. The optimization process:
- **Samples candidate action sequences** from a Gaussian distribution.
- **Evaluates expected returns** using the learned world model.
- **Bootstraps values** beyond the planning horizon using the terminal value function.
- **Refines action distributions** over multiple iterations before execution.

### 3. **Training Generalist TD-MPC2 Agents**
To achieve generalization across diverse tasks, TD-MPC2 introduces:
- **Learnable task embeddings**: A vector representation conditioned on each task, allowing the model to generalize across multiple environments.
- **Action masking**: Handles varying action spaces by zero-padding and masking invalid dimensions.

## Results
TD-MPC2 is evaluated across **104 continuous control tasks** spanning four major domains:
1. **DMControl (39 tasks)** - Locomotion and manipulation challenges.
2. **Meta-World (50 tasks)** - Robotic manipulation tasks.
3. **ManiSkill2 (5 tasks)** - Realistic robotic skill learning.
4. **MyoSuite (10 tasks)** - Physiologically accurate musculoskeletal control.

### Key Findings:
- **State-of-the-Art Performance**: Outperforms **SAC**, **DreamerV3**, and **TD-MPC** on all four benchmarks.
- **Scalability**: Performance improves as model and dataset sizes increase.
- **Generalization**: A **317M parameter agent** is successfully trained to perform 80 diverse tasks with a **single set of hyperparameters**.
- **Efficiency**: Achieves superior sample efficiency and robustness compared to prior methods.

## Conclusion
TD-MPC2 represents a major step toward **scalable and robust model-based reinforcement learning**. By integrating **latent trajectory optimization**, **multi-task generalization**, and **implicit world modeling**, the framework achieves strong performance across a wide range of continuous control tasks. The key contributions include:
- A **decoder-free** world model that facilitates scalable learning.
- A **policy prior-enhanced planning** approach for robust action selection.
- A **single hyperparameter set** enabling broad generalization.
- **Scalability insights**, demonstrating that larger models consistently improve performance.
TD-MPC2 highlights the potential of **generalist world models** in reinforcement learning.

## Limitations
1. **High computational cost**: Training large world models requires significant GPU resources.

## Thoughts
Future work could explore leveraging pre-trained models for zero-shot learning.

## References
- The paper: https://arxiv.org/abs/2310.16828
- This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.

