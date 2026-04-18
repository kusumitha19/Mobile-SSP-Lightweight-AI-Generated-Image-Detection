# Mobile-SSP: Lightweight AI-Generated Image Detection

## Overview
This project presents **Mobile-SSP**, a lightweight deep learning framework for detecting **AI-generated (synthetic) images**.  
It combines the **Single Simple Patch (SSP)** training strategy with a **MobileNetV2 backbone** to achieve high accuracy with low computational cost.

Instead of analyzing full images, the model focuses on **localized patches**, enabling it to capture subtle **texture patterns and artifacts** introduced by generative models.


## Problem Statement
With the rapid growth of generative models such as GANs and diffusion models, distinguishing between real and AI-generated images has become challenging.

Most existing methods rely on **heavy architectures (e.g., ResNet, Transformers)**, which:
- Require high computational power  
- Are not suitable for real-time applications  
- Cannot be easily deployed on edge devices  

This project aims to design a **lightweight and efficient detection system**.


## Proposed Solution

### Mobile-SSP Framework
- Uses **Single Simple Patch (SSP)** strategy  
- Extracts random patches from images  
- Focuses on **micro-texture and noise patterns**

### MobileNetV2 Backbone
- Lightweight CNN (~3.5M parameters)  
- Uses **depthwise separable convolutions**  
- Efficient for real-time inference  


## Model Architecture

Pipeline:

Input Image  
→ SSP Patch Selection (RandomResizedCrop)  
→ MobileNetV2 Feature Extraction  
→ Fully Connected Layer  
→ Sigmoid Activation  
→ Output (Real / Fake)


## Datasets Used

Detailed dataset info: [DATASET.md](DATASET.md)

- CIFAKE Dataset  
- GenImage Dataset  



## Training Details

- Loss Function: Binary Cross Entropy with Logits  
- Optimizer: Adam  
- Learning Rate: Polynomial Decay  
- Data Augmentation:
  - RandomResizedCrop (SSP)
  - Horizontal Flip
  - Normalization  


## Results

| Model | CIFAKE Accuracy | GenImage Accuracy | Parameters |
|------|----------------|------------------|-----------|
| ResNet18 (SSP) | ~88.86% | - | High |
| ResNet50 | ~88.91% | - | ~25M |
| MobileNetV2 | ~93–95% | ~90% | ~3.4M |
| **Mobile-SSP (Proposed)** | **~95%** | **~91.29%** | **~3.5M** |

Achieves high accuracy with significant reduction in model size.

---

## Key Contributions

- Lightweight AI-generated image detection model  
- SSP-based patch learning for better generalization  
- Efficient MobileNetV2 backbone  
- Improved accuracy–efficiency trade-off  
- Suitable for real-time and edge deployment  

