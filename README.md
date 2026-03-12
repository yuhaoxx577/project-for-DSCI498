# Monet-Style Image Generation with DCGAN
## Project Overview
This project designs and implements a Generative Adversarial Network (GAN) model for generating modal style artworks. The model employs deep convolutional network architectures for both generator and discriminator, learning the stylistic features and visual patterns of original modal artworks through adversarial training. 

## Baseline Approach

The baseline solution for this project is a Deep Convolutional Generative Adversarial Network (DCGAN) for Monet-style image generation.

This project does not focus on image classification or direct style transfer. Instead, the goal is to learn the visual distribution of Monet paintings and generate new images from random noise.

The baseline model contains two main components:

- **Generator**: takes a 100-dimensional latent noise vector and progressively upsamples it into a 128x128 RGB image using transposed convolution layers.
- **Discriminator**: takes either a real Monet painting or a generated image and predicts whether the image is real or fake.

The two networks are trained adversarially. The discriminator learns to distinguish real images from generated ones, while the generator learns to produce images that can fool the discriminator.

DCGAN is used as the baseline because it is a classic and effective architecture for image generation, and it provides a clear starting point for later improvements.

## Training Setup

The baseline model is trained using adversarial learning. The discriminator is trained to distinguish real Monet paintings from generated images, while the generator is trained to produce images that can fool the discriminator.

Binary Cross Entropy (BCE) loss is used for both the generator and the discriminator. The model is optimized using the Adam optimizer, which is commonly used in DCGAN training for stable convergence.

## Experiment Configuration

The main training configuration is as follows:

- image size: 128 × 128
- batch size: 32
- latent dimension: 100
- generator feature size: 64
- discriminator feature size: 64
- number of channels: 3
- learning rate: 0.0002
- Adam beta1: 0.5
- Adam beta2: 0.999
- planned training length: 100 epochs


## Data Source
This project uses the Monet image dataset from Baidu AI Studio, which is based on the “I’m Something of a Painter Myself” dataset. The project focuses on the Monet JPEG image collection for training.

Dataset link:
https://aistudio.baidu.com/datasetdetail/144858
