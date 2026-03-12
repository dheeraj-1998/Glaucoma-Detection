# Glaucoma Detection using U-Net (Deep Learning)

## Overview

Glaucoma is one of the leading causes of irreversible blindness
worldwide. Early detection is critical to prevent permanent damage to
the optic nerve. This project presents a deep learning--based system
that automatically detects glaucoma by analyzing retinal fundus images.

The system segments the **optic disc (OD)** and **optic cup (OC)** using
a **U-Net convolutional neural network architecture** and computes the
**Cup-to-Disc Ratio (CDR)**. The CDR is a clinically important biomarker
used by ophthalmologists to detect glaucoma progression.

This work was developed as part of a final-year research project and
focuses on improving segmentation accuracy while reducing computational
complexity through entropy-based sampling.

------------------------------------------------------------------------

# Research Contribution

This project contributes to glaucoma detection research by:

-   Implementing **U-Net based retinal image segmentation**
-   Introducing **entropy-based pixel sampling** to reduce computational
    cost
-   Automatically computing **Cup-to-Disc Ratio (CDR)** from segmented
    regions
-   Providing a scalable approach for **automated glaucoma screening
    systems**

------------------------------------------------------------------------

# Methodology

## 1. Image Preprocessing

The preprocessing stage enhances the retinal images to improve
segmentation quality.

Steps include:

-   Conversion of images from **RGB to L*a*b color space**
-   Intensity normalization
-   Cropping the image around the optic disc region
-   Standardizing pixel intensity values between 0 and 1

This preprocessing improves contrast between retinal structures and
background regions.

------------------------------------------------------------------------

## 2. Entropy-Based Sampling

Analyzing every pixel in high-resolution retinal images is
computationally expensive. To address this issue, an **entropy-based
sampling approach** is used.

Key idea: - Pixels with higher entropy contain more information (edges,
vessels, boundaries). - Sampling focuses on these informative regions. -
This reduces computational complexity while maintaining segmentation
accuracy.

------------------------------------------------------------------------

## 3. U-Net Architecture

The segmentation model is based on the **U-Net architecture**, widely
used in biomedical image segmentation.

### Encoder (Contracting Path)

-   Multiple **3×3 convolution layers**
-   **ReLU activation**
-   **2×2 max pooling** for down-sampling
-   Feature map size doubles at each stage

### Bottleneck

-   Deep feature extraction layer connecting encoder and decoder.

### Decoder (Expanding Path)

-   **Up-convolution layers**
-   Skip connections with encoder layers
-   Reconstruction of segmentation masks.

Output layers generate:

-   Optic Disc segmentation
-   Optic Cup segmentation

------------------------------------------------------------------------

# Cup-to-Disc Ratio (CDR) Calculation

Once segmentation is completed, the system calculates:

CDR = Cup Area / Disc Area

Higher CDR values indicate higher glaucoma risk.

Example results:

  Sample   Disc Area   Cup Area   Predicted CDR
  -------- ----------- ---------- ---------------
  1        19695       13385      0.68
  2        39488       27855      0.71
  3        39774       28589      0.72

The model achieved approximately **94% segmentation accuracy** for optic
cup and optic disc regions.

------------------------------------------------------------------------

# Dataset

The model is evaluated using the **DRISHTI-GS dataset**, a publicly
available retinal image dataset used in glaucoma research.

Dataset includes: - Retinal fundus images - Ground truth optic disc
masks - Ground truth optic cup masks

------------------------------------------------------------------------

# Technologies Used

Programming: - Python

Deep Learning: - TensorFlow / Keras - Convolutional Neural Networks -
U-Net architecture

Image Processing: - OpenCV - NumPy - Scikit-image

Visualization: - Matplotlib

------------------------------------------------------------------------

# Project Structure

glaucoma-detection/ │ ├── glaucoma.ipynb \# Main notebook containing
model implementation ├── dataset/ \# Retinal image dataset ├── models/
\# Saved model weights ├── results/ \# Segmentation outputs ├── utils/
\# Utility functions └── README.md \# Project documentation

------------------------------------------------------------------------

# Applications

This research can be applied to:

-   Automated glaucoma screening systems
-   Clinical decision support systems
-   Large-scale ophthalmology screening programs
-   Medical imaging research
-   AI-based diagnostic tools

------------------------------------------------------------------------

# Future Work

Potential improvements include:

-   Training on larger retinal datasets
-   Incorporating **Attention U-Net architectures**
-   Adding glaucoma classification models
-   Deploying the system as a **web or mobile application**
-   Integrating with hospital diagnostic systems

