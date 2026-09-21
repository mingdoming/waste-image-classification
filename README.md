# Waste Image Classification

Applied Study on Transfer Learning-Based Classification of Household Waste

## Overview

This project investigates deep learning-based image classification for automated household waste sorting.

A baseline Convolutional Neural Network (CNN) and a transfer learning-based ResNet50 model were implemented and compared using a public waste image dataset.

The main objective was to examine whether transfer learning can improve classification performance and generalization under limited-data conditions.

## Research Background

The increasing amount of household waste has created a need for automated waste classification technologies.

This study applies deep learning-based image classification to household waste and compares a simple CNN baseline with a pretrained ResNet50 model.

## Dataset

The Garbage Classification Dataset from Kaggle was used.

The dataset contains approximately 2,500 images across six waste categories:

- Cardboard
- Glass
- Metal
- Paper
- Plastic
- Trash

### Preprocessing

- Image resizing to 224 × 224
- Pixel normalization
- Data augmentation
  - Horizontal flipping
  - Brightness adjustment
  - Contrast adjustment
- Train / Validation split: 8:2
- Random seed: 42

## Methodology

### 1. Baseline CNN

A CNN model was implemented as the baseline model.

The network consists of:

- 3 Conv2D layers
- MaxPooling2D layers
- ReLU activation
- Dropout (0.3)
- Dense layer
- Softmax output layer for six classes
- Sparse categorical cross-entropy loss
- Adam optimizer

The baseline model was used to evaluate classification performance without transfer learning.

### 2. ResNet50 Transfer Learning

A ResNet50 model pretrained on ImageNet was used for transfer learning.

Key settings:

- Input size: 224 × 224 RGB
- ImageNet pretrained weights
- Residual Block architecture
- Lower 140 layers frozen
- Upper 30 layers fine-tuned
- Fine-tuning learning rate: 1e-4
- Dropout: 0.3
- Softmax output layer for six classes

The pretrained visual features were adapted to the household waste classification task through fine-tuning.

## Experimental Results

### Baseline CNN

The baseline CNN achieved:

- Accuracy: 63.96%
- Macro F1-score: 0.6092

The training accuracy increased to approximately 0.85, while validation accuracy remained around 0.63, indicating an overfitting tendency.

Class-level F1-scores were:

| Class | F1-score |
|---|---:|
| Paper | 0.75 |
| Cardboard | 0.83 |
| Glass | 0.58 |
| Metal | 0.48 |
| Plastic | 0.55 |
| Trash | 0.45 |

The lower performance of some classes was associated with visual similarity in material, texture, and color.

### ResNet50

The fine-tuned ResNet50 achieved:

- Accuracy: 89.90%
- Macro F1-score: 0.8838

The model showed more stable training behavior than the baseline CNN.

The validation accuracy converged around 0.90, while validation loss decreased below 0.2 during training.

Class-level F1-scores were:

| Class | F1-score |
|---|---:|
| Cardboard | 0.93 |
| Glass | 0.90 |
| Metal | 0.83 |
| Paper | 0.94 |
| Plastic | 0.89 |
| Trash | 0.79 |

## Model Comparison

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Baseline CNN | 63.96% | 0.6092 |
| ResNet50 | 89.90% | 0.8838 |

The ResNet50 model improved accuracy by more than 25 percentage points compared with the baseline CNN.

The results indicate that pretrained visual features and fine-tuning can improve classification performance and generalization for household waste images.

## Evaluation

Model performance was evaluated using:

- Accuracy
- Macro F1-score
- Class-level F1-score
- Classification Report
- Confusion Matrix
- Training / Validation Accuracy
- Training / Validation Loss

## Research Presentation

This research was presented at the 2025 Fall Conference of the Society of Convergence Knowledge.

**Title:**  
전이학습 기반 생활폐기물 이미지 분류 응용연구

**English Title:**  
Applied Study on Transfer Learning-Based Classification of Household Waste

**Authors:**  
Somin Yim, Jihoon Seo

**Institution:**  
Kangnam University

**Presentation Type:**  
Oral Presentation

## Future Work

Future research directions include:

- Integration with IoT sensors
- Integration with robotic vision systems
- Real-time waste recognition
- Intelligent automated waste sorting systems
- Validation using real-world waste sorting environments

## Technologies

- Python
- TensorFlow
- Keras
- NumPy
- Pandas
- scikit-learn
- Matplotlib

## Files

```text
waste-image-classification/
├── README.md
├── classification.ipynb
└── .gitignore
