# Active Learning for Image Classification

This repository contains the implementation and experimental results for the paper **"Active Learning for Image Classification"**, authored by Sergey Ilizirov, Michal Barsht, and Amir Steiner (November 2024). The project proposes an active learning strategy that integrates uncertainty-based sampling with CNN-based feature representations to optimize labeling efforts in image classification tasks.

Active learning is a critical approach for reducing dependency on large labeled datasets by intelligently selecting the most informative samples for annotation. This project introduces a new active learning strategy tailored for image classification tasks, especially in domains with limited labeling budgets (e.g., medical imaging). Our method combines uncertainty-based sampling with CNN feature representations to identify and prioritize images for labeling, outperforming standard uncertainty and random sampling in most scenarios.

---

## Introduction

Deep learning models excel in image classification tasks but require large labeled datasets, which can be expensive or impractical to obtain in specialized fields. Active learning addresses this challenge by focusing on the most informative samples. In this project:
- We leverage uncertainty metrics (e.g., entropy) to measure sample informativeness.
- We enhance this with CNN feature clustering to identify similar samples with high uncertainty, enabling more targeted labeling efforts.

---

## Proposed Method

The active learning system works iteratively:
1. **Initialization**: Randomly sample and label a subset of the dataset.
2. **Uncertainty Estimation**: Compute uncertainty scores for unlabeled samples using entropy.
3. **Data Selection**: Use clustering on feature representations of uncertain samples to identify additional informative samples.
4. **Labeling**: Label selected samples and add them to the labeled dataset.
5. **Model Training**: Fine-tune the CNN model using the updated labeled dataset.
6. Repeat steps 2–5 for a predefined number of iterations or until performance converges.

## Experiments

### Dataset
The experiments were conducted on the **CIFAR-10 dataset**, containing 60,000 images across 10 classes, with 50,000 training and 10,000 test images.

### Baselines
The proposed method was compared against:
- **Random Sampling**: A baseline active learning strategy.
- **Uncertainty Sampling**: Selecting the most uncertain samples based on entropy.

### Results
The proposed method demonstrated competitive performance, outperforming uncertainty sampling in most iterations, particularly in scenarios with minimal labeled data, highlighting its efficiency in labeling budgets.

**Sample Graph:**
![Accuracy vs. Iterations](result.png)

---

## How to Run the Code

### Prerequisites
- Python 3.8+
- Required libraries: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `torch`

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repository/active-learning.git
   cd active-learning
