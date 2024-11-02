Linear Transformations form the core of [Fully Connected (dense) Layer](Fully%20Connected%20Layer.md) in [Neural Network](../../Neural%20Network.md). The essence of a linear transformation is mapping an input vector to an output vector using a weight matrix. This operation is described by the equation:
$$
y=W⋅x+b
$$
Where:
- $y$ is the **output vector** (the result of the transformation).
- $W$ is the **weight matrix** (parameters learned during training).
- $x$ is the **input vector** (features or previous layer's activations).
- $b$ is the **bias vector** (added after the transformation to shift the result).
## Properties
A transformation $T$ is linear if it satisfies two key properties:
1. **Additive** (or linearity with respect to addition):
	$$T(x_{1}+x_{2})=T(x_{1})+T(x_{2})$$
2. Some prop

## Matrix representation of a Linear Transformation:
In [Neural Network](../../Neural%20Network.md), linear Transformations are implemented through [Matrix Multiplication](../../../Science/Maths/Matrices/Matrix%20Multiplication.md). Suppose we have:
- An **input vector $x$** with size $n$.
- A **weight matrix $W$** dimensions $m\times n$ (i.e., $m$ rows and $n$ columns), where $m$ is the size of the output vector.
- A **bias vector $b$** with size $m$.

The linear transformation can be expressed as:
$$
y=W⋅x +b
$$
Where $W$ is a matrix containing the **weights** that connect each input element to each output element.

**Example:**
- The **input vector $x$** has 3 elements: $x=[x_{1},x_{2},x_{3}]$.
- The **output vector $y$** has 2 Elements $y=[y_{1},y_{2}]$.
- The **weight matrix $W$** has dimensions $2\times3$ (2 outputs, 3 inputs):
$$
W=\begin{bmatrix}
w_{11} && w_{12} && w_{13} \\
w_{21} && w_{22} && w_{23}
\end{bmatrix}
$$
- The **bias vector $b$** is $\begin{bmatrix}b_{1}, b_{2}\end{bmatrix}$.

The output vector $y$ is computed as:

$$
\begin{bmatrix}
y_{1}\\
y_{2}
\end{bmatrix} = \begin{bmatrix}
w_{11} && w_{12} && w_{13} \\
w_{21} && w_{22} && w_{23}
\end{bmatrix}.\begin{bmatrix}
x_{1}  \\
x_{2}  \\
x_{3}
\end{bmatrix} + \begin{bmatrix}
b_{1}  \\
b_{2}
\end{bmatrix}
$$

$$
y_{1} = w_{11}x_{1} + w_{12}x_{2} + w_{13}x_{3} + b_{1}
$$
$$
y_{2}=w_{21}x_{1} + w_{22}x_{2} +w_{23}x_{3}+b_{2}
$$
This is a linear transformation from a 3D space (input) to a 2D space (output).
## Geometric interpretation
A linear transformation can be interpreted as a way to **transform vectors in space**. Depending on the weight matrix $W$, a linear transformation can do the following to the input vector:
1. **Scaling**: The input vector can be stretched or compressed.
2. **Rotation**: The input vector can be flipped across some axis.
3. **Reflection** The input vector can be flipped across some axis.
4. **Shear:** The input vector can be skewed, shifting the direction of components relative to each other.

For example, in 2D space, a weight matrix $W$ could rotate, reflect, or scale a vector $x$, producing an output vector $y$.
## Bias in Linear Transformation
The **bias vector $b$** shifts the output of the transformation. Without the bias, the linear transformation always maps the origin (zero vector) to the origin. Adding a bias term allows the network too shift the entire transformation, giving it more flexibility to fit data.

**In geometric terms:**
- **Without bias:** The transformation is linear mapping though the origin
- **With bias**: The transformation can be translated (shifted) away from the origin.

## In Neural Networks:
In neural networks, linear transformation are used to combine the learned weights with the input data. However, by themselves, Linear Transformations cannot model complex, non-linear patterns in data. This is why **activation functions** are introduced after linear transformation to introduce non-linearity. For example:
- After the linear transformation $y=W⋅x+b$, an activation function like **ReLU** or [Sigmoid Activation Function](Sigmoid%20Activation%20Function.md) is applied to $y$.

This combination of linear transformation and non-linear activation functions allows [Neural Network](../../Neural%20Network.md) to approximate complex functions.

## Matrix multiplication in Linear Transformations:
The matrix multiplication in a linear transformation is essential for understanding how input features are weighted and combined to form the output. Here's a step-by-step example with PyTorch:
```python
import torch

# Define input vector (3 features)
x = torch.tensor([1.0, 2.0, 3.0])

# Define weight matrix (2 output features, 3 input features)
W = torch.tensor([[0.5, -0.2, 0.8],
                  [-0.3, 0.7, 0.1]])

# Define bias vector (2 output features)
b = torch.tensor([0.1, -0.2])

# Compute the linear transformation
y = torch.matmul(W, x) + b

print(f"Input vector: {x}")
print(f"Weight matrix: \n{W}")
print(f"Bias vector: {b}")
print(f"Output vector: {y}")
```
This code performs the matrix multiplication $\mathbf{W}⋅\mathbf{x}$, then adds the bias vector $\mathbf{b}$, producing the output $\mathbf{y}$.
### Summary:
- A **linear transformation** maps an input vector to an output vector using a weight matrix and a bias vector.
- In neural networks, the linear transformation combines input features linearly, forming the core of the computation in fully connected layers.
- The bias allows the transformation to be shifted, adding flexibility.
- The combination of linear transformations and non-linear activation functions makes neural networks capable of modeling complex data.