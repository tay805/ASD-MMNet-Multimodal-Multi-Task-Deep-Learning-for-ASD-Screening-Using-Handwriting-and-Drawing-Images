# ASD-MMNet: Multimodal Deep Learning for ASD Screening Using Handwriting and Drawing Images

**Author:** Tawseef Ahmed Teli   
**Framework:** TensorFlow / Keras  
**Primary backbone:** ConvNeXtTiny

## Overview

ASD-MMNet is a multimodal, multi-task deep learning framework developed for research into autism spectrum disorder (ASD) screening using handwriting and drawing images.

The framework combines complementary visual and handcrafted features to learn representations of drawing structure, edge patterns, and texture. A shared feature-fusion module supports four related prediction tasks within a single model.

## Key Features

- **Multimodal feature extraction:** Combines RGB images, Canny edge maps, and HOG–LBP texture descriptors.
- **Transfer learning:** Uses an ImageNet-pretrained ConvNeXtTiny backbone for RGB feature extraction.
- **Multi-task learning:** Predicts diagnosis category, severity level, age group, and task type.
- **Data preprocessing:** Includes dataset discovery, label normalization, image resizing, feature extraction, and data augmentation.
- **Two-phase training:** Uses frozen-backbone warm-up followed by fine-tuning.
- **Model evaluation:** Includes accuracy, weighted and macro F1-scores, ROC-AUC, precision–recall curves, and per-class metrics.
- **Statistical analysis:** Implements bootstrap confidence intervals and five-fold cross-validation.
- **Baseline comparisons:** Evaluates alternative input modalities, binary classification, and a ResNet50-based architecture.
- **Explainability:** Includes Grad-CAM visualization and feature-space analysis.
- **Model export:** Saves the trained model and label encoders for subsequent inference.

## Architecture

The model consists of three parallel feature-extraction branches:

| Branch | Input representation | Feature extractor |
|---|---|---|
| RGB | Original color image | ConvNeXtTiny |
| Edge | Canny edge map | Lightweight CNN |
| Texture | HOG and LBP descriptors | Multilayer perceptron |

The extracted features are concatenated and passed through shared fusion layers. Four task-specific output heads generate predictions for diagnosis category, severity, age group, and image task type.

## Workflow

1. Environment setup and dependency installation.
2. Dataset loading, discovery, and label cleaning.
3. Exploratory data analysis and class-distribution visualization.
4. Label encoding and train/validation/test partitioning.
5. RGB, edge, and texture feature preparation.
6. Multimodal model construction and compilation.
7. Warm-up training with a frozen pretrained backbone.
8. Fine-tuning and checkpoint selection.
9. Test-set evaluation and diagnostic performance visualization.
10. Bootstrap confidence intervals and cross-validation.
11. Baseline comparisons and subgroup analysis.
12. Explainability, model export, and single-image inference.

## Requirements

The notebook uses Python and the following major libraries:

- TensorFlow / Keras
- NumPy
- pandas
- OpenCV
- scikit-image
- scikit-learn
- Matplotlib
- Seaborn
- Albumentations
- tf-keras-vis

The notebook was designed for a Google Colab-style environment and includes Google Drive integration. Dependency versions should be checked and pinned when reproducing experiments.

## Dataset

The notebook expects a locally accessible image dataset organized hierarchically by diagnosis, severity, age group, task type, and image files.

The dataset path must be configured before execution. The dataset source, licensing terms, participant consent arrangements, and any required ethics approvals should be documented before public redistribution or clinical research use.

**Important:** The notebook's dataset path is a configurable placeholder. Users must provide the appropriate dataset and verify that its labels and organization match the expected structure.

## Reproducibility

For reproducible experiments:

- Record the dataset version and preprocessing configuration.
- Set and document random seeds.
- Keep training, validation, and test partitions separate.
- Ensure that images from the same participant do not leak across partitions.
- Record library versions, model checkpoints, and evaluation settings.
- Report results on held-out data and distinguish them from cross-validation results.

Participant-level splitting requires verified participant identifiers. Filename-derived identifiers should not be assumed to establish participant independence unless validated against the dataset documentation.

## Outputs

Depending on the execution path, the notebook generates training checkpoints, evaluation metrics, plots, classification reports, confidence intervals, cross-validation results, and a serialized Keras model with label encoders.

Generated outputs depend on the dataset, software environment, configuration, and training run. Do not interpret the notebook's reported results as independently validated clinical performance.

## Limitations

This project is a research implementation, not a clinically validated diagnostic system. Dataset size, class definitions, image acquisition conditions, demographic representation, label quality, and data leakage may affect model performance.

External validation on independent datasets and evaluation with qualified clinical collaborators are necessary before considering practical screening applications.

## Author

**Tawseef Ahmed Teli**

## Disclaimer

This repository is intended for research and educational purposes. It does not provide medical advice, establish an ASD diagnosis, or replace assessment by qualified healthcare professionals.
