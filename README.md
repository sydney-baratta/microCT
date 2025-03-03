# Image Processing for Microstructure Analysis

## Overview

This Jupyter notebook contains code for processing and analyzing 2D binary images from microstructure data (specifically for the SnowEx project). The notebook performs the following tasks:

1. **Converting BMP images to PNG** - Converts BMP images to PNG format if not already done.
2. **Batch Processing of Images** - Crops circular regions of interest from images in batches.
3. **Handling Interrupted Runs (OPTIONAL)** - Checks if cropped versions of images already exist in case of an interruption during batch processing.
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

## Code Structure

# Cell 1: Import Libraries
In this section, the necessary libraries are imported for the entire analysis. These include libraries for data manipulation (pandas, numpy), image processing (PIL, opencv-python), and plotting (matplotlib). Additionally, some helper functions for displaying output in Jupyter are imported.

# Cell 2: Convert BMP to PNG
This section handles the conversion of BMP images to PNG format. It processes all BMP images in a specified directory by:

  - Loading the images using the Python Imaging Library (PIL).
  - Converting each image to grayscale.
  - Applying a binary threshold to the grayscale images to create black-and-white versions.
  - Saving the newly created binary images in PNG format.
  - This step ensures that all images are in a suitable format for further processing.

# Cell 3: Batch Processing of Images (Cropping)
This section processes images in batches to crop circular regions of interest from each image. The cropping process involves:

  - Loading each image in grayscale.
  - Applying a binary threshold to isolate the circular region.
  - Using contour detection to find the circular shape and crop the image around it.
  - Saving the cropped versions of each image with a new filename that indicates they have been cropped.
  - Batch processing helps manage memory usage and optimizes processing for large datasets.

# Cell 4: Handle Interrupted Runs
In case the previous image processing step is interrupted (for example, due to a system shutdown or error), this section ensures that the program does not reprocess images that have already been cropped. It checks if a cropped image already exists for each original image and skips processing if a cropped version is already found.

This step helps avoid unnecessary reprocessing and saves time, especially when working with large datasets.

# Cell 5: Specific Surface Area (SSA) Calculation
This final step calculates the Specific Surface Area (SSA) for each processed image. The SSA is computed using autocorrelation functions (ACF). The main tasks here include:

  - Extracting relevant metadata (e.g., slice height) from the filenames.
  - Performing autocorrelation analysis to compute correlation lengths in both the X and Z directions.
  - Fitting the autocorrelation data to an exponential model.
  - Computing SSA values based on these correlation lengths.
  - The results are saved in CSV files for each site, containing the SSA and correlation lengths in both X and Z directions. These results are used for further analysis and modeling of the microstructure.

## Output
For each site, the notebook produces:

  - Cropped Images - The cropped images are saved in the cropped_images directory.
  - CSV Results - For each site, a CSV file is generated containing the correlation lengths and SSA values for each slice.
  - Example of Output CSV

The CSV file for each site contains the following columns:

  - Site: The site name.
  - Top Height (cm): The top height of the slice.
  - Bottom Height (cm): The bottom height of the slice.
  - Slice Number: The slice number.
  - Correlation Length (Measured) X (mm): The measured correlation length in the X direction.
  - Correlation Length (Measured) Z (mm): The measured correlation length in the Z direction.
  - Correlation Length (Exponential) X (mm): The exponential fit for the X direction.
  - Correlation Length (Exponential) Z (mm): The exponential fit for the Z direction.
  - SSA X (mm^-1): The specific surface area in the X direction.
  - SSA Z (mm^-1): The specific surface area in the Z direction.

## Notes
Performance: The image processing (especially cropping) can be slow when dealing with large datasets (e.g., 340,000 images). The code has been optimized to run in batches to manage memory usage.
Pixel Size: The pixel_size variable needs to be set to the actual pixel size for accurate SSA calculations.
Ensure Backup: Always ensure to have backups of the original images before running this notebook.
Future Improvements
Parallel Processing: The code can be enhanced by introducing parallel processing to speed up batch image processing.
Optimization for Large Datasets: Consider implementing more efficient image processing techniques for larger datasets.



