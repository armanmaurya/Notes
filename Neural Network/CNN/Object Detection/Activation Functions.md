---
tags:
  - AI
---
Activation functions are critical components in neural networks that introduce non-linearity to the model. Without them, the network would simply be a stack of linear transformations, and regardless of the number of layers, it could only model linear relationships. Activation functions allow the network to learn and model complex patterns and relationships in data.
### **Why Use Activation Functions?**
- **Non-linearity**: Real-world data is often non-linear. Activation functions enable the neural network to capture non-linear patterns.
- **Learning complex functions**: Activation functions help the network learn complex mappings from inputs to outputs, such as for image recognition, language processing, and more.
- **Breaking linear combinations**: Without activation functions, each layer would just be a linear combination of the previous layer's output, making the whole network a linear model, which is insufficient for complex tasks.

### Types of Activation Functions
There are several commonly used activation functions in neural networks. Each has its pros and cons, and the choice of activation function depends on the problem being solved, network architecture, and sometimes trial and error.
1. [Sigmoid Activation Function](Sigmoid%20Activation%20Function.md)
2. [ReLU Activation Function](ReLU%20Activation%20Function.md)