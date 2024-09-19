```python
import torchvision.transforms as transforms
from PIL import Image

# Load an image using PIL
image_path = 'path_to_your_image.jpg'  # Replace with your image path
image = Image.open(image_path)

# Transform the image to a tensor and normalize it
transform = transforms.Compose([
    transforms.Resize((128, 128)),  # Resize the image
    transforms.ToTensor()  # Convert to tensor (values in range [0, 1])
])

# Apply the transformation to the image
input_image = transform(image).unsqueeze(0)  # Add batch dimension			
```
