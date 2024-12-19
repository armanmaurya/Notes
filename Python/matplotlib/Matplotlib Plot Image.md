## Plot Single Image
```python
from PIL import Image
import matplotlib.pyplot as plt

# Load an image using PIL
image_path = 'image.jpg'  # Replace with your image path
image = Image.open(image_path)

# Display the image 
plt.imshow(image) 
plt.axis('off') # Hide axis 
plt.show()
```
## Plot Multiple Image
To plot multiple images using matplotlib, you can use subplots.
The `plt.subplots(2, 2)` creates a 2x2 grid of subplots, which is essentially a matrix. Here's a breakdown:

- `2` (rows): The number of rows in the grid.
- `2` (columns): The number of columns in the grid.

This will give you a matrix (array) of axes where each axis can hold one plot or image. For example:

- `axs[0, 0]` is the top-left subplot.
- `axs[0, 1]` is the top-right subplot.
- `axs[1, 0]` is the bottom-left subplot.
- `axs[1, 1]` is the bottom-right subplot.

If you want a different grid, you can modify the numbers. For example, `plt.subplots(1, 3)` would create a 1x3 grid (1 row, 3 columns), and `plt.subplots(3, 1)` would create a 3x1 grid (3 rows, 1 column).
Here's an example of how to display multiple images in a grid:
```python
import matplotlib.pyplot as plt
from PIL import Image

# Load an image using PIL

image_path = 'image.jpg' # Replace with your image path
image = Image.open(image_path)

fig, axs = plt.subplots(2, 2)

# Display images in the grid

axs[0, 0].imshow(image)

axs[0, 1].imshow(image)

axs[1, 0].imshow(image)

axs[1, 1].imshow(image)
```