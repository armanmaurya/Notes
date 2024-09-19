We could apply linear transformation to the incoming data using the **torch.nn.Linear()** module in PyTorch. This module is designed to create a Linear Layer in the neural networks. A linear layer computes the linear transformation as below-
$$
y= xA^T + b
$$
Where,
- $x$ is the incoming data. It must be a tensor of dtype float 32 and shape (*, in_features). 
- $y$ is the output data after the transformation with same dtype as $x$ and with shape (*, out_features). Note that all dimensions except last are of the same shape as input data.
- $A$ is the learnable weights of shape (out_features, in_features). Out_features is the dimension of the output data. 
- $b$ is the additional bias learned during the training.

>**Note:-** Weights $A$ and bias $x$ are initialized randomly.
# Stepwise Implementation
Below are the steps to follow to apply a linear transformation to incoming data --

### Step 1: Import PyTorch
The required library is PyTorch. The first step is to import PyTorch.
```python
import torch
```
### Step 2: Define the Input Data
Now define the input data. We are going to apply a linear transformation to this data. The input data must be a Tensor of dtype float 32.  We created a tensor of size [3, 4] using a random generator.  We can interpret this tensor as an input of three samples each of size 4. Here for the input data the in_features = 4, see the next step. Note that in a Neural network, this data is incoming from the previous layer.

```python
data = torch.randn(3,4)
```

### Step 3: Define the Number of Input and Output Features

The ‘in_features’ is the number of features in each input sample, and the ‘out_features’ is the number of features in each output sample. The in_features  depend on the input tensor as in the second step the in_features = 4. The out_features are decided according to our need and the neural network architecture.

```python
in_features = 4
out_features = 2
```

### Step 4: Define a Linear Transformation

 We define linear transformation ‘linear’ using the torch.Nn.Linear () module.  We pass the in-features and out_features as parameters. We could also pass the optional parameter bias = False if we don’t want the layer to learn the bias. Note that the module torch.Nn.Linear () performs as a layer in the neural network.
```python
 linear = torch.nn.Linear(in_features, out_features)
```

### Step 5: Apply the Linear Transformation to the Input Data:

Now we apply the defined linear transformation to the input data (incoming data). We could print the output data, shape and size of the output data after transformation.
```python
data_out = linear(data)
```

---
**Example 1:**

Here the in_features=5 as the input data size is [5]. And we set out_features = 3, so the size of output data (data after transformation) is [3]. In the above example, the input data is in a one-dimensional tensor.
```python
# Python program to apply Linear transform 
# to incoming data 
# Step 1: Importing PyTorch 
import torch 

# Step 2: Define incoming data as torch 
# tensor (float32) 
data = torch.tensor([23., 12., 33., 4.01, -65.]) 
print("Data before Transformation:\n", data) 
print("dtype of Data:", data.dtype) 
print("Size of Data:", data.size()) 

# Step 3: Define the in_features, out_features 
in_features = 5
out_features = 3

# Step 4: Define a linear transformation 
linear = torch.nn.Linear(in_features, out_features) 

# Step 5: Apply the Linear transformation to 
# the tensor 
data_out = linear(data) 
print("Data after Transformation:\n", data_out) 
print("Size of Data after Transformation:", data_out.size()) 

```

**Output:**

You may get the output tensor with different elements at each run as the weights and biases are initialized randomly.
```
Data before Transformation:
 tensor([ 23.0000,  12.0000,  33.0000,   4.0100, -65.0000])
dtype of Data: torch.float32
Size of Data: torch.Size([5])
Data after Transformation:
 tensor([-6.3559, -1.5512, 22.3267], grad_fn=<AddBackward0>)
Size of Data after Transformation: torch.Size([3])
```
**Example 2:**

Here the in_features=4 as the input tensor size is [3, 4]. And we set out_features = 2, so the size of the output tensor (data after transformation) is [3, 2]. The dimension except the last dimension is the same as input tensor. The last dimension is the same as out_features.
```python
# Python program to apply Linear transform 
# to incoming data 
# Step 1: Importing PyTorch 
import torch 

# Step 2: Define input data as torch tensor (float32) 
data = torch.randn(3, 4) 
print("Tensor before Transformation:\n", data) 
print("dtype of Tensor:", data.dtype) 
print("Size of Tensor:", data.size()) 

# Step 3: Define the in_features, out_features 
in_features = 4
out_features = 2

# Step 4: Define a linear transformation 
linear = torch.nn.Linear(in_features, out_features) 

# Step 5: Apply the Linear transformation to the tensor 
data_out = linear(data) 
print("Transformed Tensor:\n", data_out) 
print("Size of Transformed Tensor:", data_out.size()) 
```

**Output:** 

You may get the output tensor with different elements at each run as the weights and biases are initialized randomly.
```
Tensor before Transformation:
 tensor([[ 0.0664,  1.8933, -0.4003, -0.2383],
        [-0.7531,  1.8737, -2.0936, -0.8959],
        [-1.6239, -1.1321, -0.5427, -0.4834]])
dtype of Tensor: torch.float32
Size of Tensor: torch.Size([3, 4])
Transformed Tensor:
 tensor([[-0.5405,  0.4570],
        [-0.5507, -0.3917],
        [ 0.4763, -0.3399]], grad_fn=<AddmmBackward>)
Size of Transformed Tensor: torch.Size([3, 2])
```