Global pooling reduces each channel in the feature map to a single value. Thus, an $n_{x} \times n_{w}\times n_{c}$ feature map is reduced $1\times_{1}\times_{1}\times n_{c}$ feature map. This is equivalent to using a filter of dimensions $n_{h}\times n_{w}$ i.e., the dimensions of the feature map.
Further, it can be either global [Max Pooling](Max%20Pooling.md) or global [Average Pooling](Average%20Pooling.md).

**Performing Global Pooling using keras**
```python
import numpy as np
from keras.models import Sequential
from keras.layers import GlobalMaxPooling2D
from keras.layers import GlobalAveragePooling2D

# define input image
image = np.array([[2.0, 2.0, 7.0, 3.0],
                  [9.0, 4.0, 6.0, 1.0],
                  [8.0, 5.0, 2.0, 4.0],
                  [3.0, 1.0, 2.0, 6.0]])
image = image.reshape(1.0, 4.0, 4.0, 1.0)

# define gm_model containing just a single global-max pooling layer
gm_model = Sequential(
    [GlobalMaxPooling2D()])

# define ga_model containing just a single global-average pooling layer
ga_model = Sequential(
    [GlobalAveragePooling2D()])

# generate pooled output
gm_output = gm_model.predict(image)
ga_output = ga_model.predict(image)

# print output image
gm_output = np.squeeze(gm_output)
ga_output = np.squeeze(ga_output)
print("gm_output: ", gm_output)
print("ga_output: ", ga_output)
```
**Output:**
```
gm_output:  9.0  
ga_output:  4.0625
```