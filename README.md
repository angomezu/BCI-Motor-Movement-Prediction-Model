# EEG-Based Motor Movement Prediction using Supervised Learning

This repository contains a machine learning pipeline for classifying motor movements (left fist, right fist, both feet) based on EEG (Electroencephalography) data. The project lays the groundwork for real-time Brain-Computer Interface (BCI) systems aimed at assistive technologies and neurorehabilitation applications.

**Status**: Work in Progress  
**Last Updated**: March 30, 2025

---

## Project Overview

- **Objective**: Predict motor movements from EEG signals using supervised learning techniques.
- **Application**: Foundation for brain-computer interface systems that assist individuals with motor impairments.
- **Dataset**: [PhysioNet EEG Motor Movement/Imagery Dataset](https://archive.physionet.org/pn4/eegmmidb/)
- **Subjects**: 109 individuals, each completing 14 experimental runs (rest, motor, and imagery tasks)
- **EEG Recording**: 64 channels, sampled at 160 Hz

---

## Methodology

### Preprocessing

- Parsed EDF files and extracted raw EEG signals
- Applied a bandpass filter (1–40 Hz) to eliminate muscle and environmental noise
- Merged multiple sessions to align labels across movement types
- Handled missing values using imputation techniques

### Feature Engineering

- **Time-Domain Features**: Mean, Variance, RMS, Hjorth Parameters (Activity, Mobility, Complexity)
- **Frequency-Domain Features**: Power Spectral Density (PSD), FFT Mean
- **Spatial Features**: Common Spatial Patterns (CSP) for signal projection and dimensionality reduction

### Data Balancing

- Addressed class imbalance using SMOTE (Synthetic Minority Oversampling Technique)

### Model Training

- Implemented a Random Forest Classifier
- Train/test split: 80% / 20%
- Model evaluated on accuracy, precision, recall, F1-score, and AUC

---

## Results

- **Test Accuracy**: 95.38%
- **AUC Score**: 0.94
- **Top Features**: CSP components and Hjorth Mobility

| Class            | Precision | Recall | F1-Score |
|------------------|-----------|--------|----------|
| Left Fist (T1)   | 0.88      | 1.00   | 0.93     |
| Right Fist (T2)  | 1.00      | 0.86   | 0.92     |
| Rest (T0)        | 1.00      | 1.00   | 1.00     |

---

## Future Work

- Test model generalization with data from additional subjects
- Deploy the model in a real-time EEG classification setting using OpenBCI or Lab Streaming Layer
- Connect to VR/AR or robotic simulation environments (e.g., Unity or Unreal Engine)
- Explore deep learning methods such as CNNs applied directly to EEG signal matrices
- Evaluate model robustness under noise and subject variability

---

## Repository Contents

- `Model.ipynb` / `Model_V2.ipynb`: Notebooks for data processing, feature engineering, and modeling
- `Technical Report.docx`: Detailed write-up of the project workflow and results
- `Barrera_Project_Phase2.pdf`: Progress summary with visual analysis
- `Supervised Learning for Motor Movement Prediction.pptx`: Presentation slides

---

## Author

**Angel Barrera**  
Master’s Student, Applied Data Science  
East Tennessee State University  
Focus: Brain-Computer Interfaces, Machine Learning, and Neurotechnology Applications

---

## References

1. Goldberger AL et al. "PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals." *Circulation*, 2000.  
2. PhysioNet EEG Motor Movement/Imagery Dataset: [https://archive.physionet.org/pn4/eegmmidb/](https://archive.physionet.org/pn4/eegmmidb/)  
3. Wu et al. "Probabilistic Common Spatial Patterns for Multichannel EEG Analysis." *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 2015.  
