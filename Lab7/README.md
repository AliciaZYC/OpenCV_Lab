# OpenCV Workshop Lab 7: Thresholding

## Overview

This lab introduces **thresholding techniques** used in image processing for **segmentation**. These techniques convert grayscale images into binary images by comparing pixel values to a threshold. The lab covers:

- **Simple Thresholding**: Uses a fixed threshold value for the entire image.
- **Adaptive Thresholding**: Adjusts the threshold for different regions of the image.
- **Otsu’s Binarization**: Automatically calculates the optimal threshold value.

## Code Overview

### 1. `simple_threshold(image)`

This function applies **simple thresholding** to the input image.

- **Binary Threshold**: Sets pixel values greater than the threshold to 255 and others to 0.
- Example code:

```python
_, thresh_simple = cv2.threshold(image, 127, 255, cv2.THRESH_BINARY)
```

### 2. `adaptive_threshold(image)`

This function applies **adaptive thresholding**, helpful when lighting conditions vary across the image. It uses two methods:

- **Mean Adaptive Thresholding**: Computes the mean of the neighborhood values.
- **Gaussian Adaptive Thresholding**: Computes a weighted sum of neighborhood values.

```python
thresh_mean = cv2.adaptiveThreshold(image, 255, cv2.ADAPTIVE_THRESH_MEAN_C,
                                    cv2.THRESH_BINARY, 11, 2)
thresh_gaussian = cv2.adaptiveThreshold(image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                        cv2.THRESH_BINARY, 11, 2)
```

### 3. `otsu_threshold(image)`

This function applies **Otsu’s Binarization** to determine the best threshold value based on the image’s histogram.

- Example code:

```python
_, thresh_otsu = cv2.threshold(image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
```
