# Lab 11: Generative AI

This project demonstrates key concepts in Generative AI, including adversarial images, diffusion models, and generative adversarial networks (GANs).

## Features

### Adversarial Images

- Generates adversarial images by adding random noise to a grayscale image.
- Uses the `cv2.addWeighted` function for blending the original image with noise.
- Saves the adversarial image to disk and displays it.

### Diffusion Models

- Simulates adding Gaussian noise to an image in multiple steps (forward diffusion).
- Implements denoising using a Gaussian blur to reverse the added noise.
- Saves intermediate noisy images and the final denoised image to disk.

### Generative Adversarial Networks (GANs)

- Builds a simple GAN architecture with:
  - **Generator**: Creates fake images from random noise.
  - **Discriminator**: Classifies images as real or fake.
- Demonstrates the architecture of both models but does not train them in this script.

---

## Function Details and Parameters

### `create_adversarial_image(image_path, save_path)`

Generates and saves an adversarial image by adding random noise.

- **Parameters**:
  - `image_path` (str): Path to the input image file.
  - `save_path` (str): Path to save the generated adversarial image.

### `apply_diffusion(image_path, save_folder)`

Simulates a diffusion process by adding Gaussian noise in steps and saving the noisy images.

- **Parameters**:
  - `image_path` (str): Path to the input image file.
  - `save_folder` (str): Path to the folder where intermediate noisy images will be saved.

### `denoise_image(noisy_image_path, save_path)`

Applies Gaussian blur to denoise a noisy image and saves the result.

- **Parameters**:
  - `noisy_image_path` (str): Path to the input noisy image file.
  - `save_path` (str): Path to save the denoised image.

### GAN Classes

- **`Generator(latent_dim)`**:
  - **Parameters**:
    - `latent_dim` (int): Dimension of the input noise vector.
  - **Description**: Creates fake images from random noise using a neural network.
- **`Discriminator`**:
  - **Description**: Classifies images as real or fake using a neural network.

---

## Prerequisites

- Python 3.8+
- Libraries:
  - OpenCV
  - NumPy
  - PyTorch

Install the required libraries using:

```bash
pip install numpy opencv-python torch torchvision
```

## How to Run

1. Prepare an Image:

Place a grayscale image file named image.jpg in the same directory as the script.

2. Install dependencies:
   ```
   pip install numpy opencv-python torch torchvision
   ```
3. Run the script:
   ```
   python3 lab11.py
   ```

## References

- Generative AI Applications in digital art, content creation, and medical imaging.
- Diffusion models as alternatives to GANs for handling complex data distributions.
- FGSM technique for adversarial image generation.
