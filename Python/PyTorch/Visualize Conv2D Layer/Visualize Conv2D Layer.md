```Python
import torch
import torch.nn as nn
import torchvision.transforms as transforms
import matplotlib.pyplot as plt
from PIL import Image
import numpy as np

# Load an image using PIL
image_path = 'image.jpg'  # Replace with your image path
image = Image.open(image_path)

# Transform the image to a tensor and normalize it
transform = transforms.Compose([
    transforms.ToTensor()  # Convert to tensor (values in range [0, 1])
])

# Apply the transformation to the image
input_image = transform(image).unsqueeze(0)  # Add batch dimension

# Define a Conv2d layer with 3 input channels (RGB) and 10 output channels
conv_layer = nn.Conv2d(in_channels=3, out_channels=10, kernel_size=3, stride=1, padding=1)

# Apply the Conv2d layer to the input
output_image = conv_layer(input_image)

# Convert the output image to a NumPy array
output_image = output_image.detach().numpy().squeeze()

# Normalize each output channel for better visualization (scale between 0 and 1)
output_image = (output_image - np.min(output_image, axis=(1, 2), keepdims=True)) / (
    np.max(output_image, axis=(1, 2), keepdims=True) - np.min(output_image, axis=(1, 2), keepdims=True)
)

  

# Plot the original image
plt.figure()
plt.imshow(image)
plt.title('Original Image')
plt.axis('off')
plt.show()

# Plot the first 10 output channels in a 2x5 grid
fig, axs = plt.subplots(2, 5, figsize=(15, 6))  # Create a grid of 2 rows and 5 columns

for i in range(10):
    ax = axs[i // 5, i % 5]
    ax.imshow(output_image[i], cmap='gray')  # Visualize each output channel
    ax.set_title(f'Output Channel {i + 1}')
    ax.axis('off')
  
plt.tight_layout()
plt.show()
```