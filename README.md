# Monet-Style Image Generation with DCGAN

## Project Description

This project implements a **Deep Convolutional Generative Adversarial Network (DCGAN)** for Monet-style image generation.

The goal of this project is not image classification or direct style transfer. Instead, the model learns the visual distribution of Claude Monet paintings and generates new images from random noise through adversarial training.

The system contains two main components:

- **Generator**: takes a 100-dimensional latent noise vector and progressively upsamples it into a 128×128 RGB image using transposed convolution layers.
- **Discriminator**: takes either a real Monet painting or a generated image and predicts whether the image is real or fake.

The two networks are trained adversarially. The discriminator learns to distinguish real Monet paintings from generated images, while the generator learns to produce images that can fool the discriminator.

This project also includes:

- training curve visualization
- generated samples saved during training
- final generated image grid
- latent space interpolation results
- saved generator and discriminator model weights

## Baseline Approach

The baseline model used in this project is **DCGAN**.

DCGAN is chosen because it is a classic and effective architecture for image generation. It provides a clear and interpretable starting point for artistic image synthesis tasks.

Main design choices include:

- convolutional / transposed convolutional structure
- batch normalization
- ReLU in the generator
- LeakyReLU in the discriminator
- Tanh output in the generator
- Sigmoid output in the discriminator

## Data Source

This project uses the dataset from **Baidu AI Studio**, based on the Kaggle Monet dataset.

Dataset link:  
https://aistudio.baidu.com/datasetdetail/144858

The project focuses on the **Monet JPEG image collection** for training.

## Data Placement

The current notebook uses the dataset path:

```python
dataroot = "./monet_jpg"
```

So before running the notebook, place the folder `monet_jpg` in the **same directory as `main.ipynb`**.

Example structure:

```text
ShortProjectTitle/
│── data/
│   │── readme_data.txt
│── ReadMe.txt
│── main.ipynb
│── monet_jpg/
│   │── 000c1e3bff.jpg
│   │── 011835cfbf.jpg
│   │── ...
```

The code supports image extensions such as:

- `.jpg`
- `.jpeg`
- `.png`

If no images are found, the notebook will raise an error indicating that the dataset path is incorrect or the folder is empty.

## Training Setup

The main training configuration is:

- **Image size**: 128 × 128
- **Batch size**: 32, or 8 if CUDA is not available
- **Latent dimension**: 100
- **Generator feature size**: 64
- **Discriminator feature size**: 64
- **Number of channels**: 3
- **Number of epochs**: 100
- **Learning rate**: 0.0002
- **Adam beta1**: 0.5
- **Adam beta2**: 0.999
- **Loss function**: Binary Cross Entropy

## Required Packages

This project is implemented in Python and uses the following packages:

- `os`
- `time`
- `random`
- `glob`
- `numpy`
- `torch`
- `torchvision`
- `PIL`
- `matplotlib`
- `IPython`

Install the required packages with:

```bash
pip install numpy torch torchvision pillow matplotlib ipython jupyter
```

If GPU acceleration is needed, install the CUDA-compatible version of PyTorch based on your system.

## How to Run the Code

Open the notebook in Jupyter Notebook or JupyterLab:

```bash
jupyter notebook main.ipynb
```

Then run all cells in order.

The notebook will load the Monet images from:

```text
./monet_jpg
```

Make sure the `monet_jpg` folder is placed in the same directory as `main.ipynb`.

## What the Notebook Does

When executed, the notebook performs the following steps:

1. Loads the Monet dataset from `./monet_jpg`
2. Applies preprocessing:
   - Resize to 128×128
   - Center crop to 128×128
   - Convert to tensor
   - Normalize to [-1, 1]
3. Builds the generator and discriminator
4. Trains the DCGAN model
5. Logs generator loss, discriminator loss, and discriminator outputs
6. Saves training curves
7. Saves generated samples during training
8. Saves final generated samples
9. Saves latent space interpolation results
10. Saves trained generator and discriminator weights

## Main Files

The submitted project contains the following main files:

- **main.ipynb**  
  Main Jupyter Notebook for data loading, preprocessing, model definition, training, visualization, final image generation, and latent space interpolation.

- **ReadMe.txt**  
  Project description, data source, required packages, and running instructions.

- **data/readme_data.txt**  
  Instructions on how to obtain the dataset and where to place it.

- **monet_jpg/**  
  Folder containing the Monet painting images used for training. The current notebook loads images from `./monet_jpg`.

## Notes

- This project is designed for Monet-style image generation only.
- The notebook assumes the Monet image folder has already been downloaded and extracted.
- If the dataset path is changed, update the `dataroot` variable in the notebook accordingly.
- Training time depends on hardware.
- If CUDA is available, the notebook will automatically use GPU.
- If CUDA is not available, the notebook can still run on CPU, but training will be slower.

## Output Summary

After training, the project produces outputs such as:

- training loss curves
- generated samples over time
- final generated sample grid
- latent space interpolation
- trained generator and discriminator weights
