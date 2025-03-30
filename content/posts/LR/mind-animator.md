---
title: "[LR] Reconstruction of Dynamic Natural Vision from Slow Brain Activity"
date: 2025-03-30T10:51:36+08:00
draft: false
tags: ["brain decoding", "fMRI", "video reconstruction", "diffusion", "ICLR 2025"]
---

[This review is intended solely for my personal learning]

Paper Info
> arXiv: 2405.03280v2  
> Title: Animate Your Thoughts: Decoupled Reconstruction of Dynamic Natural Vision from Slow Brain Activity  
> Authors: Yizhuo Lu, Changde Du, Chong Wang, Xuanliu Zhu, Liuyun Jiang, Xujin Li, and Huiguang He  

## Prior Knowledge
- **Brain decoding with fMRI**: Functional MRI measures brain activity through BOLD (Blood-Oxygen-Level Dependent) signals, which reflect neural activation across 3D voxel grids. Decoding methods aim to map these signals back to perceptual experiences like images or videos.
- **Contrastive learning and CLIP**: Contrastive loss functions (e.g., InfoNCE) train models to align representations from different modalities. CLIP is a pre-trained vision-language model that embeds text and images into a shared space, useful for representing high-level semantics.
- **VQ-VAE (Vector Quantized Variational Autoencoder)**: A generative model that discretizes image data into latent tokens, enabling compression and reconstruction. It’s commonly used in diffusion models for reducing the input dimensionality while preserving structure.
- **Transformer and sparse causal attention**: Transformers model long-range dependencies via attention. Sparse causal attention masks future tokens and restricts attention to a sparse set, ensuring temporal consistency while reducing computational cost—critical for decoding motion from fMRI.
- **Stable Diffusion and U-Net**: Stable Diffusion is a text-to-image model that generates visuals via iterative denoising in a latent space. Its U-Net backbone processes image latents at multiple resolutions and is commonly inflated for video generation.

## Goal
To accurately reconstruct dynamic natural vision (videos) from fMRI recordings by explicitly disentangling and decoding **semantic**, **structural**, and **motion** features — each aligned with distinct neural processes — in order to improve both reconstruction fidelity and neurobiological interpretability.

## Method

The proposed system, **Mind-Animator**, adopts a **two-stage pipeline**:

### Stage 1: fMRI-to-Feature Decoding
This stage maps the brain signal $x \in \mathbb{R}^n$ (fMRI voxels) into three disentangled representations:

1. **Semantic Decoder**
   - Projects fMRI into the CLIP (ViT-B/32) latent space using a tri-modal contrastive learning setup:

    $$
    L_{\mathrm{semantic}} = \alpha \cdot L_{\mathrm{InfoNCE}}(f, t) + (1 - \alpha) \cdot L_{\mathrm{InfoNCE}}(f, v)
    $$

     where $f$, $t$, $v$ are embeddings from fMRI, text, and video, respectively.

   - A 3-layer MLP then maps $f$ to the text-conditioning format $c$ used by Stable Diffusion.

2. **Structure Decoder**
   - Uses VQ-VAE encoding of the **first frame** to represent low-level visual structure.
   - A 2-layer MLP is trained with MSE loss:

    $$
    L_{\mathrm{structure}} = \frac{1}{B} \sum_{i=1}^{B} \left\| D_{\mathrm{structure}}(f_i) - \Phi(v_{i,1}) \right\|_2^2
    $$

3. **Motion Decoder: Consistency Motion Generator (CMG)**
   - A Transformer with **sparse causal attention** decodes inter-frame motion from latent video tokens.
   - Frame embeddings are predicted autoregressively using fMRI as conditioning input: $L_{\mathrm{motion}}$ = mean squared error between decoded and ground truth motion tokens
   - Cross-attention ensures that spatial details in fMRI directly affect motion prediction.

### Stage 2: Feature-to-Video Generation
- Instead of training a video generation model, the authors **inflate** a text-to-image Stable Diffusion model into a per-frame generator.
- Reconstructed features are passed frame-by-frame into the U-Net (SD) and then decoded by VQ-VAE to reconstruct the video clip.

## Results
Evaluated on **CC2017**, **HCP**, and **Algonauts2021** datasets.

### Quantitative Results (CC2017)
| Metric       | Mind-Animator | Best Baseline (Mind-Video) |
|--------------|----------------|-----------------------------|
| SSIM         | **0.321**      | 0.177                       |
| PSNR         | 9.22           | 8.87                        |
| Hue-PCC      | 0.786          | 0.768                       |
| CLIP-PCC     | 0.425          | 0.409                       |
| EPE (↓)      | **5.42**       | 6.12                        |
| VIFI         | **0.608**      | 0.593                       |

- **Retrieval accuracy** on CC2017 (Top-10, Large Set): 2.39% vs. 1.28% (Mind-Video).
- Maintains robustness even on extended datasets, demonstrating generalization.

### Ablation Study
| Model Variant         | SSIM | VIFI | EPE ↓ |
|-----------------------|------|------|--------|
| Full Model            | 0.319 | 0.604 | 5.57  |
| w/o Semantic Decoder  | 0.097 | 0.523 | 8.72  |
| w/o Structure Decoder | 0.184 | 0.555 | 7.68  |
| w/o Motion Decoder    | 0.136 | 0.585 | 6.37  |

Removing any one of the decoders leads to a noticeable drop in quality, validating the model’s modular design.

### Motion Validity
- A shuffle test confirms that **motion information arises from fMRI**, not model bias.
- EPE is a more sensitive motion metric than CLIP-PCC in this setting.

### Interpretability
- Voxel-wise maps show:
  - **High-level cortex (HVC)** encodes semantics.
  - **V1 and MT** jointly encode motion.
  - **Ventral cortex** for structure.

This aligns well with neuroscience literature and supports the brain-inspired design of the decoders.

## Limitations  
- Low temporal resolution of fMRI limits fine-grained motion fidelity.
- Static structure assumption (only the first frame is used).
- Potential inductive bias from frozen pretrained components.

## Reference  
* The paper: https://arxiv.org/abs/2405.03280v2  
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.
