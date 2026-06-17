# Visual Entailment with Deep Learning

## Overview

This project presents an end-to-end multimodal deep learning system for Visual Entailment classification. The objective is to determine whether a textual hypothesis is supported or contradicted by the content of a given image.

The system combines computer vision and natural language processing techniques to learn semantic relationships between visual content and textual descriptions. A pretrained convolutional neural network is used for image understanding, while a recurrent neural network processes textual information. Both modalities are fused through a Feature-wise Linear Modulation (FiLM) mechanism to enable effective cross-modal reasoning.

---

## Problem Statement

Visual Entailment is a multimodal reasoning task where a model must determine the semantic relationship between an image and a textual hypothesis.

Given:

* A premise image
* A hypothesis sentence

The model predicts one of the following classes:

* **Entailment** – the image supports the hypothesis.
* **Contradiction** – the image contradicts the hypothesis.

This task requires simultaneous understanding of visual and textual information and the ability to reason across both modalities.

---

## Features

* Image preprocessing and augmentation
* Text preprocessing and vectorization
* Visual feature extraction using transfer learning
* Bidirectional sequence modeling for text understanding
* Multimodal feature fusion using FiLM
* End-to-end deep learning pipeline
* Two-stage transfer learning and fine-tuning strategy
* Prediction generation for unseen data

---

## Deep Learning Architecture

This project implements a multimodal deep learning framework for Visual Entailment classification by combining image understanding and natural language processing techniques.

### Image Encoder

Visual features are extracted using **EfficientNetB0**, a pretrained convolutional neural network trained on the ImageNet dataset.

Transfer learning is employed to leverage rich visual representations learned from large-scale image data. The original classification head is removed and replaced with custom layers specifically designed for the visual entailment task.

Key components:

* EfficientNetB0 pretrained on ImageNet
* Global Average Pooling
* Transfer Learning
* Fine-Tuning

### Text Encoder

Hypothesis sentences are processed using a natural language processing pipeline consisting of:

* Text Vectorization
* Embedding Layer
* Bidirectional LSTM (BiLSTM)

The embedding layer converts tokens into dense vector representations, while the BiLSTM captures contextual information from both forward and backward directions, enabling a richer understanding of sentence meaning.

### Multimodal Fusion

To effectively combine image and text information, the model utilizes **Feature-wise Linear Modulation (FiLM)**.

The FiLM layer generates scaling and shifting parameters from the textual representation and applies them to visual features extracted from the image encoder. This enables the model to dynamically adjust visual representations based on the hypothesis text and improves cross-modal reasoning.

### Classification Head

The fused representation is passed through fully connected neural network layers consisting of:

* Dense Layers
* ReLU Activations
* Dropout Regularization

A Softmax output layer produces probabilities for the two target classes:

* Entailment
* Contradiction

---

## Training Strategy

The model is trained using a two-stage approach.

### Stage 1: Transfer Learning

* EfficientNetB0 backbone remains frozen.
* Custom text encoder, fusion layers, and classification layers are trained.
* Allows the model to learn task-specific representations while preserving pretrained visual knowledge.

### Stage 2: Fine-Tuning

* Selected layers of EfficientNetB0 are unfrozen.
* Smaller learning rates are used for stable optimization.
* Fine-tuning enables the visual encoder to adapt more effectively to the visual entailment task.

Training incorporates:

* Adam Optimizer
* Sparse Categorical Crossentropy Loss
* Early Stopping
* Model Checkpointing
* Learning Rate Scheduling
* Dropout Regularization

---

## Techniques Used

* Transfer Learning
* EfficientNetB0
* Bidirectional LSTM (BiLSTM)
* Text Embeddings
* FiLM Fusion
* Multimodal Deep Learning
* Data Augmentation
* Fine-Tuning
* Dense Neural Networks
* Dropout Regularization
* Adam Optimizer
* Sparse Categorical Crossentropy Loss

---

## Author

**Varadraj Tarapure**
Master of Artificial Intelligence
RMIT University
