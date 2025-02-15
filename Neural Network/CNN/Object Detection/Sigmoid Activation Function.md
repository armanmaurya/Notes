---
tags:
  - AI
---
The sigmoid function is one of the most commonly used [Activation Functions](Activation%20Functions.md) in [Neural Network](../../Neural%20Network.md). It has a characteristic "S" shaped curve, also known as a **logistic curve**, and is defined mathematically as:
$$
\sigma(x)=\frac{1}{1+e^{-x}}
$$
Where:
- $\sigma(x)$ is the sigmoid function. 
- $x$ is input to the function, which can range from negative to positive infinity.
- $e$ is Euler's number, approximately equal to 2.718.

## Key Properties
- **Range:** The sigmoid function maps any real-valued input $x$ to a value between 0 and 1.
  $$0 < \sigma(x)<1$$
 - **S-shaped curve**: The sigmoid function produced a smooth, S-shaped curve, which squashes large positive or negative inputs into a narrow range.
 - **Asymptotic behavior:**
	 - As $x\to +\infty, \sigma(x)\to1$
	 - As $x\to-\infty,\sigma(x)\to 0$.
- **Symmetry:** The sigmoid function is **monotonically increasing** and symmetric and around $x=0$, meaning:
$$
\sigma(-x)=1-\sigma(x)
$$
## Working 
**Compression to a fixed range**: Sigmoid maps all input values (whether large or small) into the (0, 1) range, making it ideal for tasks where probabilities or binary output are required.
- Large positive values will result in an output close to 1.
- Large negative values will result in an output close to 0.
- A value of $x=0$ results in $\sigma(0)$ = 0.5.

## Derivative
The derivative of the sigmoid function is essential for training neural networks using gradient-based optimization methods (e.g., backpropagation). The derivative of the sigmoid function can be expressed as:
$$
\frac{d(\sigma(x))}{dx} = \sigma(x)⋅(1-\sigma(x))
$$
This formula is useful because the derivative can be calculated directly from the output of the sigmoid function itself, without needing to compute additional exponentials.

**Key Points about Derivative:**
- The derivative is highest at $x=0$ where the output is 0.5, with $\frac{d(\sigma(0))}{dx}=0.25$
- As the input becomes large in magnitude (either positive or negative), the derivative approaches zero. This leads to **vanishing gradient problem during backpropagation**, which can show down or stop learning in deep networks.

## Application
- **Binary classification**: Since the sigmoid function outputs values between 0 and 1, it's widely used in binary classification tasks, often in the output layer of neural network.
	- Example predicting if an email is spam or not spam
- **Logistic regression:** The sigmoid function is the basis of logistic regression, a type of binary classification model.
- **Probability output**: When you want to interpret the output of a neuron as probability, sigmoid is a good choice, since its range is (0, 1), when can represent probabilities.
- **Smooth gradient**: The smoothness of the sigmoid curve ensures that the gradient doesn't change abruptly, which can be useful in simple neural networks.
## Disadvantages
Despite its usefulness in certain application, the sigmoid function has several notable drawbacks:
1. **Vanishing Gradient Problem**
   
   For a very large positive or negative inputs, the sigmoid function saturates (i.e., the output becomes almost flat at 0 or 1). As a result, the gradients of these neurons become very small, which can cause slow learning or prevent the network form learning altogether, especially in deep networks.
2. **Non-Zero Centered Output**
   
   The output of the sigmoid function is always positive, between 0 and 1. This means that the gradients during backpropagation can either all be positive or all be negative. This makes optimization more difficult because updates in weights might not be as efficient as with zero-centered activation function (like Tanh).
3. **Computational Complexity**
   The sigmoid function involves calculating an exponential, which can be computationally expensive in large-scale networks, especially when compared to simpler function like the ReLU (Rectified Linear Unit).

## PyTorch Example
In PyTorch, the sigmoid function can be used with the `torch.nn.Sigmoid` module or directly applied to tensor using `torch.sigmoid`.
**Example**
```python
import torch
import torch.nn as nn

# Example of applying sigmoid to a tensor
x = torch.tensor([-1.0, 0.0, 1.0, 2.0])  # Input tensor

# Using the torch.sigmoid function
output = torch.sigmoid(x)

print(f"Input: {x}")
print(f"Sigmoid output: {output}")
```
**Output:**
```css
Input: tensor([-1.,  0.,  1.,  2.])
Sigmoid output: tensor([0.2689, 0.5000, 0.7311, 0.8808])
```
In this example:
- For $x=-1.0$, sigmoid outputs 0.2689 (closer to 0).
- For $x=2.0$, sigmoid outputs 0.8808 (closer to 1).

**Using in Neural Networks:**
```python
import torch
import torch.nn as nn

# Define a neural network with a sigmoid output layer
class SimpleNN(nn.Module):
    def __init__(self):
        super(SimpleNN, self).__init__()
        self.linear = nn.Linear(10, 1)  # A single output node
        self.sigmoid = nn.Sigmoid()     # Sigmoid activation function

    def forward(self, x):
        x = self.linear(x)
        x = self.sigmoid(x)
        return x

# Initialize the model
model = SimpleNN()

# Create a random input tensor of size (1, 10)
input_tensor = torch.randn(1, 10)

# Get the output
output = model(input_tensor)
print(f"Model output: {output}")
```
In this network:

- A [Linear Transformation](Linear%20Transformation.md) is applied to the input, followed by a sigmoid activation function to output a value between 0 and 1.