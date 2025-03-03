# Image Processing for Microstructure Analysis

## Overview

This Jupyter notebook contains code for processing and analyzing 2D binary images from microstructure data (specifically for the SnowEx project). The notebook performs the following tasks:

1. **Converting BMP images to PNG** - Converts BMP images to PNG format if not already done.
2. **Batch Processing of Images** - Crops circular regions of interest from images in batches.
3. **Handling Interrupted Runs** - Checks if cropped versions of images already exist in case of an interruption during batch processing.
4. **Computing Specific Surface Area (SSA)** - For each image, the notebook calculates and stores the SSA in both X and Z directions using autocorrelation functions.

## Dependencies

Ensure the following libraries are installed before running the notebook:

- `numpy`
- `pandas`
- `matplotlib`
- `scipy`
- `opencv-python`
- `PIL` (Python Imaging Library)

You can install them via `pip`:

```bash
pip install numpy pandas matplotlib scipy opencv-python pillow
"# microCT" 
