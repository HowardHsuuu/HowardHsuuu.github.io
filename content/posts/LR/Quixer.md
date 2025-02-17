---
title: "[LR] Quixer: A Quantum Transformer Model"
date: 2024-09-27T19:56:26+08:00
draft: false
tags: ["Quantum Computing", "Quantum Machine Learning", "Transformer"]
---

[This review is intended solely for my personal learning]

[**Qiix** at Qiskit Hackathon Taiwan 2024 was inspired by this paper]

Paper Info  
> arXiv: 2406.04305  
> Title: Quixer: A Quantum Transformer Model  
> Authors: Nikhil Khatri, Gabriel Matos, Luuk Coopmans, Stephen Clark (Quantinuum)  

## Prior Knowledge
- **Linear Combination of Unitaries (LCU)**  
  The LCU technique allows the combination of multiple unitary operators into one overall operator using additional control qubits and postselection. Given unitaries $U_0, U_1, \dots, U_{n-1}$ with complex coefficients $b_0, b_1, \dots, b_{n-1}$, one can effectively prepare a block-encoded operator
  $$
  M = \sum_{j=0}^{n-1} b_j U_j.
  $$

- **Quantum Singular Value Transformation (QSVT)**  
  QSVT is a framework that applies polynomial transformations to the singular values (or spectrum) of a block-encoded matrix. In practice, if $M$ is block-encoded, QSVT can implement a transformation
  $$
  P(M) = c_d M^d + \cdots + c_1 M + c_0 I,
  $$
  where the coefficients $\{c_i\}$ are real numbers. This mechanism is essential in quantum algorithms that require nontrivial matrix functions.

- **Classical Transformers**  
  Modern language models use attention mechanisms (typically multi-head dot-product self-attention) to mix token information. Variants like FNet and linear-attention have shown that alternative mixing methods can achieve competitive performance.

- **Quantum Neural Networks**  
  Prior work has explored quantum analogues of classical neural networks (e.g., quantum RNNs). However, constructing a full-scale quantum Transformer for NLP remains largely uncharted until the advent of models like Quixer.

## Goal
To design and validate a quantum Transformer model—**Quixer**—that:

1. Replaces classical self-attention with an LCU-based token mixing strategy.  
2. Introduces nonlinearity via a QSVT-based polynomial transformation of the combined operator.  
3. Demonstrates viable performance on the Penn Treebank (PTB) language modeling task, benchmarked against classical neural baselines.

## Method

1. **Unitary Token Embeddings**  
   Each token’s embedding $\vec{w}$ is passed through a trainable matrix $W_E$, yielding angles $\theta_{\vec{w}}$. These angles configure a parameterized quantum circuit $U(\theta_{\vec{w}})$ on $q$ qubits, thereby encoding the token as a unitary operator.

2. **Mixing via LCU**  
   For a context of $n$ tokens, each token is associated with a unitary $U_j$. The model learns coefficients $\{b_j\}$ to form
   $
   M = \sum_{j=0}^{n-1} b_j U_j.
   $
   An LCU circuit is used to prepare this operator via block encoding and postselection on an ancilla qubit.

3. **Nonlinearity via QSVT**  
   A polynomial transformation is applied to $M$:
   $
   P(M) = c_d M^d + \cdots + c_1 M + c_0 I,
   $
   where the coefficients $\{c_i\}$ are trained analogously to activation function parameters in classical networks. This is implemented by interleaving applications of the block-encoded $M$ with controlled phase gates on an ancilla, as prescribed by the QSVT framework.

4. **Feed-Forward and Output**  
   After applying $P(M)$ to the data register initialized in $|0\rangle$, a trainable feed-forward unitary $U_{\mathrm{FF}}$ is applied. Multiple Pauli observables (e.g., $X$, $Y$, $Z$ on each qubit) are measured to yield a classical vector $\vec{o}$. Finally, a classical network $f_{\text{out}}$ maps $\vec{o}$ to the next-token probabilities.

5. **Resource Estimates**  
   - **Qubits**: Requires $q$ qubits for data, $\lceil \log_2(n)\rceil$ qubits for the LCU control register, plus additional ancillas for QSVT and postselection.  
   - **Gate Complexity**: Roughly on the order of $d\,n\,g\,\log(n)$ (or better), where $g$ denotes the gate count for each parameterized token unitary $U_j$.

## Results

- **Penn Treebank Evaluation**  
  Quixer processes a context window of 32 tokens to predict the next token. In simulation, it achieves a test perplexity of approximately 122.0, which is competitive with certain LSTM and FNet baselines. Postselection success rates for the LCU and QSVT steps are on the order of a few percent, emphasizing the need for high-fidelity quantum hardware.

- **Comparison to Classical Models**  
  Quixer outperforms smaller LSTM variants and is on par with an FNet of similar dimensionality, though it lags behind a classical Transformer of comparable scale. Nonetheless, it marks the first demonstration of a quantum Transformer on a standard language corpus like PTB.

## Conclusion
Quixer leverages LCU-based mixing and QSVT-based nonlinearity to construct a quantum Transformer model. While the current results are based on classical simulation and does not yet outperform state-of-the-art classical models, the model provides a promising blueprint for future quantum NLP systems as hardware improves. Its modular design also allows for various specializations (e.g., fixed versus trainable polynomial coefficients), paving the way for a family of quantum Transformer architectures.

## Limitations

1. **Barren Plateaus**  
   Large parametric quantum circuits risk encountering vanishing gradients as the number of qubits increases.
2. **Postselection Overhead**  
   The reliance on successful postselection in the LCU and QSVT steps reduces the overall fraction of successful circuit runs.
3. **Hardware Constraints**  
   Present-day quantum devices are limited in both qubit count and fidelity, which constrains the scale of models that can be implemented.
4. **Classical Simulation**  
   The experiments are performed on classical simulators; performance under realistic quantum noise and error correction remains to be evaluated.

## Reference
* The paper: https://arxiv.org/abs/2406.04305
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.
