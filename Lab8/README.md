# OpenCV Workshop Lab 8: Edge Detection

This project implements edge detection techniques using OpenCV, focusing on two popular methods: Sobel Edge Detection and Canny Edge Detection. These methods help identify and locate significant changes in pixel intensity, which often correspond to the boundaries of objects in an image. Edge detection is widely used in various applications such as object recognition, image segmentation, and pattern recognition.

## Edge Detection Overview

Edge detection aims to find areas in an image where pixel intensity changes sharply, indicating boundaries or edges. This project specifically demonstrates:

- **Sobel Edge Detection**: Efficient and directional gradient-based edge detection.
- **Canny Edge Detection**: A multi-step algorithm with noise reduction and more refined control over detected edges.

## Techniques Implemented

### Sobel Edge Detection

The Sobel operator calculates image gradients in the horizontal (X) and vertical (Y) directions. It uses two convolution kernels to compute these gradients, which highlight intensity changes.

- **Horizontal (X) Gradient**: Detects edges in the vertical direction.
- **Vertical (Y) Gradient**: Detects edges in the horizontal direction.
- **Combined Gradient**: Combines both directions to capture the overall edge magnitude.

### Key Points of Sobel Detection

- **Computationally Efficient**: Sobel is fast and effective for simple images with clear edges.
- **Edge Orientation**: Provides directional information on detected edges (horizontal, vertical, or diagonal).
- **Sensitive to Noise**: The simplicity of Sobel makes it more sensitive to noise, leading to thicker edges without refinement.

### Code Implementation

```python
# Sobel Edge Detection Example
sobel_x = cv2.Sobel(image, cv2.CV_64F, 1, 0, ksize=3)  # Detect horizontal edges
sobel_y = cv2.Sobel(image, cv2.CV_64F, 0, 1, ksize=3)  # Detect vertical edges
sobel_combined = cv2.sqrt(sobel_x**2 + sobel_y**2)     # Combine both edges
```

- **Function Parameters**:
  - `src`: Source image.
  - `ddepth`: Depth of the destination image.
  - `dx`, `dy`: Derivative orders in X and Y directions.
  - `ksize`: Size of the Sobel kernel (usually 3).

### Canny Edge Detection

The Canny Edge Detection algorithm is a more advanced method with multiple steps:

1. **Noise Reduction**: Applies Gaussian filtering to reduce noise.
2. **Gradient Calculation**: Calculates intensity gradients in the image.
3. **Non-Maximum Suppression**: Keeps only the strongest edges and removes those that are weaker.
4. **Double Thresholding**: Sets high and low thresholds for strong and weak edges.
5. **Edge Tracking by Hysteresis**: Retains edges that connect to strong edges.

### Key Points of Canny Detection

- **Accuracy**: Canny produces thin, well-defined edges.
- **Noise Resistance**: Applies Gaussian filtering, making it robust to noise.
- **Control Over Detection**: Allows adjusting the thresholds to capture fine edges accurately, making it suitable for detailed, complex images.

### Code Implementation

```python
# Canny Edge Detection Example
edges = cv2.Canny(image, 100, 200)  # Apply Canny with thresholds 100 and 200
```

- **Function Parameters**:
  - `image`: Source image.
  - `threshold1`: Lower threshold for weak edges.
  - `threshold2`: Upper threshold for strong edges.

### Tips for Choosing Canny Threshold Values

1. **Experimentation**: Start with a high strong edge threshold (`threshold2`) and moderate weak edge threshold (`threshold1`).
2. **Image Properties**: Adjust based on image lighting and contrast. For low-contrast images, consider lowering both thresholds to enhance detection.

## Comparison of Sobel and Canny Edge Detection

| Feature              | Sobel                     | Canny                                         |
| -------------------- | ------------------------- | --------------------------------------------- |
| Gradient Calculation | Simple intensity gradient | Multi-step filtering and gradient calculation |
| Noise Sensitivity    | Sensitive                 | Uses Gaussian to reduce noise                 |
| Edge Quality         | Thicker edges             | Thin, precise edges                           |
| Control              | Limited                   | User-defined thresholds for fine control      |

### Summary

- **Sobel** is suitable for quick, efficient edge detection in simple images where speed is preferred.
- **Canny** provides detailed, robust edge detection in noisy or complex images, but it requires parameter tuning for optimal results.
