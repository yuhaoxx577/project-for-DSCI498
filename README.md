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

## Data Source
This project uses the Monet image dataset from Baidu AI Studio, which is based on the “I’m Something of a Painter Myself” dataset. The project focuses on the Monet JPEG image collection for training.

Dataset link:
https://aistudio.baidu.com/datasetdetail/144858
