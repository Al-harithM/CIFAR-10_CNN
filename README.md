# CIFAR-10_CNN

## CIFAR-10 Image Classification Using CNN and PyTorch

A deep learning project that implements a Convolutional Neural Network (CNN) using **PyTorch** to classify images from the CIFAR-10 dataset into 10 different categories.

The project explores image preprocessing, data augmentation, CNN architecture design, GPU training, model evaluation, and performance comparison with ResNet-18.

## Project Overview

The objective of this project is to build and train a CNN capable of recognizing objects in small RGB images.

The model is trained using the CIFAR-10 dataset, which contains 60,000 32×32 color images divided into 10 classes.

The project includes:
- Building a custom CNN architecture from scratch.
- Applying image normalization and data augmentation.
- Training the model using PyTorch.
- Utilizing GPU acceleration for faster training.
- Evaluating overall and per-class classification accuracy.
- Comparing the custom CNN with a ResNet-18 architecture.

## Dataset

The project uses the **CIFAR-10 dataset**, which consists of 60,000 images across 10 categories.

The dataset contains 50,000 training images and 10,000 official test images. In this implementation, the original training dataset is split into 70% training and 30% testing.

The 10 classification categories are:

1. Airplane
2. Automobile
3. Bird
4. Cat
5. Deer
6. Dog
7. Frog
8. Horse
9. Ship
10. Truck

Each image has:
- Image dimensions: 32 × 32 pixels
- Color channels: 3 (RGB)
- Number of classes: 10

## Data Preprocessing and Augmentation

The following preprocessing techniques are applied:

**Normalization**

Images are converted into PyTorch tensors and normalized using a mean of (0.5, 0.5, 0.5) and a standard deviation of (0.5, 0.5, 0.5) for the RGB channels.

**Data Augmentation**

To increase training data diversity and improve generalization, the following transformations are applied:
- Random Horizontal Flip
- Random Rotation (up to 10 degrees)
- Random Cropping (32 × 32 with padding of 4 pixels)

A subset of the augmented dataset is combined with the original training subset.

## CNN Architecture

A custom CNN architecture is implemented using PyTorch.

The network consists of three convolutional blocks followed by three fully connected layers.

| Layer | Configuration |
|---|---|
| Conv1 | 3 → 32 filters, 3×3 kernel |
| BatchNorm1 | 32 channels |
| MaxPooling1 | 2×2 |
| Conv2 | 32 → 64 filters, 3×3 kernel |
| BatchNorm2 | 64 channels |
| MaxPooling2 | 2×2 |
| Conv3 | 64 → 128 filters, 3×3 kernel |
| BatchNorm3 | 128 channels |
| MaxPooling3 | 2×2 |
| Fully Connected 1 | 2048 → 120 |
| Fully Connected 2 | 120 → 84 |
| Output Layer | 84 → 10 |

**Activation Function:** ReLU

**Pooling:** Max Pooling (2×2)

**Normalization:** Batch Normalization

**Total Trainable Parameters:** 350,590

The final output layer contains 10 neurons, corresponding to the 10 CIFAR-10 classes.

## Training Configuration

The custom CNN is trained using the following configuration:

| Parameter | Value |
|---|---|
| Framework | PyTorch |
| Loss Function | CrossEntropyLoss |
| Optimizer | Stochastic Gradient Descent (SGD) |
| Learning Rate | 0.001 |
| Momentum | 0.9 |
| Batch Size | 64 |
| Training Epochs | 5 (GPU training run) |
| Hardware Acceleration | CUDA GPU |

The model is trained using GPU acceleration to improve training performance.

## Model Evaluation

The trained CNN is evaluated using the test dataset.

### Overall Accuracy

**Test Accuracy: 80.84%**

### Per-Class Accuracy

| Class | Accuracy |
|---|---:|
| Airplane | 88.5% |
| Automobile | 92.3% |
| Bird | 75.1% |
| Cat | 63.7% |
| Deer | 81.6% |
| Dog | 74.3% |
| Frog | 88.3% |
| Horse | 78.8% |
| Ship | 82.2% |
| Truck | 83.7% |

The model performs particularly well on automobiles, airplanes, and frogs, while cats and dogs remain more challenging categories.

## ResNet-18 Benchmark

As an additional experiment, ResNet-18 is implemented to compare its performance against the custom CNN.

The ResNet-18 implementation is adapted for CIFAR-10 images by:
- Replacing the original first convolutional layer with a 3×3 convolution.
- Removing the initial max-pooling layer.
- Replacing the final fully connected layer with a 10-class output layer.

**ResNet-18 Training Configuration:**
- Optimizer: AdamW
- Learning Rate: 0.001
- Weight Decay: 0.0001
- Scheduler: Cosine Annealing
- Batch Size: 64
- Epochs: 20
- Pretrained Weights: Not used

### Benchmark Results

| Model | Test Accuracy | Trainable Parameters |
|---|---:|---:|
| Custom CNN | 80.84% | 350,590 |
| ResNet-18 | 94.47% | 11,173,962 |

ResNet-18 achieved higher classification accuracy, demonstrating the benefits of a deeper residual network, although it requires significantly more trainable parameters.

## Technologies and Libraries

- Python
- PyTorch
- Torchvision
- NumPy
- Matplotlib
- Google Colab
- CUDA

## How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/YOUR_USERNAME/cats_vs_dogs_CNN.git
   ```

2. Navigate to the project directory:

   ```bash
   cd cats_vs_dogs_CNN
   ```

3. Install the required libraries:

   ```bash
   pip install torch torchvision numpy matplotlib
   ```

4. Open the Jupyter Notebook:

   ```bash
   jupyter notebook cats_vs_dogs_CNN.ipynb
   ```

5. Run the notebook cells sequentially.

The CIFAR-10 dataset is downloaded automatically through Torchvision. If running outside Google Colab, update or remove the Google Drive mounting cell and adjust the dataset storage path.

A CUDA-compatible GPU is recommended for faster training, but CPU execution is also possible.

## Future Improvements

Potential improvements for this project include:
- Experimenting with deeper CNN architectures.
- Applying additional data augmentation techniques.
- Hyperparameter tuning to improve classification accuracy.
- Implementing learning-rate scheduling for the custom CNN.
- Exploring dropout and regularization techniques.
- Comparing additional architectures such as VGG and ResNet variants.

## Acknowledgments

- [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html)
- [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)
- [Torchvision Documentation](https://pytorch.org/vision/stable/index.html)

---

**Project Focus:** Deep Learning | Computer Vision | Image Classification | Convolutional Neural Networks
