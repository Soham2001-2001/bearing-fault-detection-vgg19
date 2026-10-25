# Bearing Fault Detection Using Phase Space Reconstruction and Fine-Tuned VGG19

![Python](https://img.shields.io/badge/Python-3.x-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-orange)
![OpenCV](https://img.shields.io/badge/OpenCV-Image%20Analysis-green)
![IEEE](https://img.shields.io/badge/IEEE-Published-00629B)

Research published in IEEE conference proceedings at IIT Mandi.

📄 **Paper:** [Read on IEEE Xplore](https://ieeexplore.ieee.org/document/10725105)

## Overview

Bearings are a common point of failure in rotating machinery, and detecting faults early helps prevent breakdowns and downtime. This project converts raw machine signal data into images using **phase space reconstruction**, which produces chaotic-pattern plots that look different for each bearing fault condition. These images are then classified by a **VGG19** convolutional neural network, fine-tuned in **PyTorch**.

The repository also includes an **image similarity tool** that compares two bearing-condition images using histograms and Normalized Cross-Correlation (NCC), to show how distinct the patterns of different fault conditions are.

## Approach

1. **Phase space reconstruction:** machine signal data is reconstructed into phase space and rendered as images, giving a distinct chaotic pattern for each bearing fault condition.
2. **Image classification:** a pretrained VGG19 CNN is fine-tuned on these images to detect and classify the fault condition.
3. **Image similarity analysis:** two condition images (for example a Ball fault and a Normal bearing) are compared with histogram and NCC metrics.

## Image Similarity Tool

The tool compares two specific images and reveals their similarity through five metrics:

| Metric | Type | What it tells you | Better match |
|--------|------|-------------------|--------------|
| **Histogram intersection** | Histogram | How much the two histograms overlap | Higher |
| **Correlation** | Histogram | How strongly the two histograms are linearly related | Higher |
| **Chi-square** | Histogram | The difference between the two histograms | Lower |
| **Bhattacharyya distance** | Histogram | The distance between the two distributions | Lower |
| **Normalized Cross-Correlation (NCC)** | Pixel-level | Pixel-wise similarity, robust to brightness and contrast changes | Closer to 1 |

Histogram metrics compare the overall distribution of pixel values, while NCC compares the images pixel by pixel. Using both gives a more complete picture than any single score.

**Sample images included:**

- `Ball_007_0000.jpg`: sample image from the Ball fault condition
- `Normal_4140.jpg`: sample image from the Normal condition

## Repository Contents

| File | Description |
|------|-------------|
| `image_similarity.py` | Image comparison script (histograms and NCC) |
| `Ball_007_0000.jpg` | Sample Ball fault image |
| `Normal_4140.jpg` | Sample Normal condition image |

## Tech Stack

- Python
- PyTorch (VGG19 fine-tuning, transfer learning)
- OpenCV (image similarity tool)
- Deep Learning, Computer Vision

## Requirements

```bash
pip install opencv-python
```

## Usage

Clone the repository and run the similarity tool from the folder that contains the images:

```bash
git clone https://github.com/Soham2001-2001/bearing-fault-detection-vgg19.git
cd bearing-fault-detection-vgg19
python image_similarity.py
```

## Reading the Similarity Results

- **Very similar images:** high intersection and correlation, low chi-square and Bhattacharyya distance, and NCC close to 1.
- **Clearly different fault conditions:** lower intersection and correlation, higher chi-square and Bhattacharyya distance, and NCC further from 1.

## Publication

This work was published in IEEE conference proceedings at IIT Mandi. The full paper is available on [IEEE Xplore](https://ieeexplore.ieee.org/document/10725105).

## Author

**Soham Rath**
[LinkedIn](https://www.linkedin.com/in/soham-rath-51a340203) · [GitHub](https://github.com/Soham2001-2001) · sohamssr25@gmail.com
