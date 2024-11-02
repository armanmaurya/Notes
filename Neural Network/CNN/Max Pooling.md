---
tags:
  - AI
---
Max pooling is a [Pooling](Pooling%20Layer.md) operation that selects the maximum element from the region of the feature map covered by the filter. Thus, the output after max-pooling layer would be a feature map containing the most prominent features of the previous feature map.
![Max_pooling](../images/Max_pooling.png)
This can be achieved using MaxPooling2D layer in keras as follows: 
```python
import numpy as np
from keras.models import Sequential
from keras.layers import MaxPooling2D

# define input image
image = np.array([[2.0, 2.0, 7.0, 3.0],
                  [9.0, 4.0, 6.0, 1.0],
                  [8.0, 5.0, 2.0, 4.0],
                  [3.0, 1.0, 2.0, 6.0]])
image = image.reshape(1.0, 4.0, 4.0, 1.0)

# define model containing just a single max pooling layer
model = Sequential(
    [MaxPooling2D(pool_size = 2, strides = 2)])

# generate pooled output
output = model.predict(image)

# print output image
output = np.squeeze(output)
print(output)
```
**Output:**
```
[[9. 7.]
[8. 6.]]
```


