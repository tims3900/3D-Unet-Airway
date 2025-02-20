# 3D U-Net for Lung Segmentation

This repository contains a 3D U-Net implementation for lung segmentation using PyTorch. The model is trained and evaluated on a dataset of lung CT scans.

![image](https://github.com/user-attachments/assets/d0b98b17-9b80-4523-b7b2-4fbb7fdbb18a)

## Model Architecture

The 3D U-Net implemented in this project follows a standard U-Net architecture with the following specifications:

- **Encoder:** 5 levels of downsampling blocks. Each block consists of two 3x3x3 convolutions followed by ReLU activation and a 2x2x2 max pooling operation.
- **Decoder:** 5 levels of upsampling blocks. Each block consists of a 2x2x2 transposed convolution, concatenation with the corresponding encoder feature map, followed by two 3x3x3 convolutions with ReLU activation.
- **Connections:** Skip connections are used to concatenate feature maps from the encoder to the decoder at corresponding levels, providing context information and improving segmentation accuracy.
- **Layers:** The model has a total of 10 convolutional layers (5 in the encoder and 5 in the decoder) and 5 max pooling layers.
- **Input/Output:** The input to the model is a 3D CT scan volume, and the output is a 3D segmentation mask of the same size.

## Data Augmentation

The following augmentation techniques are applied upon the dataset:

- **Random Flipping:** Randomly flips the input patch and mask patch along a randomly chosen axis (depth, height, or width).
- **Random Blackout:** Randomly selects a region within the patch and sets its pixel values to 0 for both the input and mask. This simulates occlusions or missing data in the input images.
- **Augmentation Probability:** The probability of applying augmentation is controlled by hyperparameters.
                                    
## Dataset                                                                      
The dataset used in this project is available at the following link:            
> [BAS Dataset](https://github.com/EndoluminalSurgicalVision-IMR/ATM-22-Related-Work/tree/main/BAS-Dataset)
## Refrences
The implementation is based on this paper:                                     
> [Automatic airway segmentation from Computed Tomography using robust and efficient 3-D convolutional neural networks](https://arxiv.org/abs/2103.16328) 
