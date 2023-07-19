# Deep Fake Face Detection Project

## Overview

This repository contains the implementation and exploration of a Deep Fake Face Detection project. The focus of this project is to detect face images generated from multiple Generative Adversarial Network (GAN) architectures using a novel pairwise learning model.

## Problem Statement

The goal of this project is to explore and develop a model that can effectively detect deep fake face images generated from various GAN architectures. The existing detection models often struggle to generalize across different GAN architectures. This project aims to reimplement the pairwise learning model proposed by Hsu C. et al., which utilizes statistics between real and fake image pairs to improve detection performance.

## Model Architecture

The project's model architecture consists of two main blocks:

1. **Common Fake Feature Network (CFFN):** This network extracts discriminative common fake features (CFFs) from image pairs using contrastive learning. The CFFN's hidden layers contain two convolutional layers and four dense net layers, resulting in a 384-dimensional feature vector.

2. **Classification Network (CN):** The CN takes the output from the trained CFFN and projects it into a 2D vector representation. It then performs binary cross-entropy loss to classify the incoming image as real or fake.

## Training Steps

The training process involves first training the CFFN using pairs of real and fake images to learn their discriminative features. The CFFN uses contrastive loss to minimize the L2 norm distance between the feature vectors of genuine and fake pairs. Once the CFFN is trained, the CN is trained to project the CFFN output from the high-dimensional space to a 2D vector for classification.

## Initial Experiments

The initial experiments used the CelebA dataset for training the CFFN + CN. The GAN models were trained on the CelebA dataset to generate fake images. The performance was evaluated using precision and recall metrics for different GAN architectures.

## Final Experiments

In the final experiments, the CFFN + CN network was retrained using an expanded GAN dataset. The model's performance was further evaluated using Fréchet Inception Distance (FID) and Inception Score (IS) metrics. The final model showed improvements in precision while maintaining good generalizability.

## Conclusion

The deep fake face detection project successfully implemented a novel pairwise learning model that outperformed existing models in detecting deep fake face images. The model demonstrated good generalizability and learned discriminative features between real and fake images. Further exploration and improvements may include retraining with different loss function values, curating higher-quality fake face image datasets, and investigating subclassification of fake images based on GAN models.
