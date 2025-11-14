# Automated Sleep Stage Classification using EEG Signals

This project implements and compares traditional machine learning (manual feature engineering) and deep learning (CNN) approaches for automated sleep stage classification using EEG data.

## Overview

- **Objective:** Automate the classification of sleep stages (Wake, NREM1-3, REM) from raw EEG signals, evaluating both manual feature-based models and end-to-end deep learning.
- **Dataset:** [Sleep-EDF Expanded (PhysioNet)](https://physionet.org/content/sleep-edfx/1.0.0/) with 60 subjects, expert-labeled sleep epochs.
- **Methods:** Replication of Santaji & Desai (2020) manual feature pipeline and extension with additional models (XGBoost, MLP, 1D-CNN).


## Methodology

- **Preprocessing:** EEG channel selection (Fpz-Cz/Pz-Oz), segment into 10s epochs, filtering (0.1–15Hz), standardization.
- **Manual Feature Engineering:** For each epoch, decompose into Delta, Theta, Alpha, Beta bands; extract Mean, Entropy, PSD, Energy (16 features/epoch).
- **Classification Models:**
  - Decision Tree
  - SVM
  - Random Forest
  - XGBoost
  - MLP (Multi-layer Perceptron)
  - 1D-CNN (end-to-end, raw signal)

## Results

| Model             | Feature Type         | Accuracy | Macro F1 |
|-------------------|---------------------|---------|----------|
| Decision Tree     | Manual (16 features)| 69%     | 0.44     |
| SVM (Balanced)    | Manual              | 62%     | 0.48     |
| Random Forest     | Manual              | 64%     | 0.50     |
| XGBoost           | Manual              | 77%     | 0.56     |
| MLP               | Manual              | 80%     | 0.56     |
| **1D-CNN**        | **Raw Signal**      | **84%** | **0.67** |

- **Key finding:** 1D-CNN model is superior, especially for handling imbalanced sleep stages.

## How to Run

1. Download Sleep-EDF dataset and place files in `data/`.
2. Open the notebooks in `notebooks/` to preprocess, train, and evaluate models.
3. Run the provided Python scripts or notebooks using the requirements in `environment.yml` or `requirements.txt`.

## Requirements

- Python 3.8+
- Numpy, Scipy, Pandas
- Scikit-learn, XGBoost
- TensorFlow/Keras
- MNE

## References

- Santaji, Sagar & Desai, Veena. (2020). "Analysis of EEG Signal to Classify Sleep Stages Using Machine Learning."
- Kemp, B. et al. (2000). "Analysis of a sleep-dependent neuronal feedback loop: the slow-wave microcontinuity of the EEG."
- Goldberger, A. L. et al. (2000). "PhysioBank, PhysioToolkit, and PhysioNet."

---


