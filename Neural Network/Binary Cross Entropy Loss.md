---
tags:
  - AI
---
It is a type of [Cross Entropy Loss Function](Cross%20Entropy%20Loss.md) used inn binary classification problems where the target variable has two possible outcomes, 0 and 1 and it measures the performance of the classification model whose output is a probability is a between them. The goal of the model is to minimize this loss function during training to improve its predictive accuracy.

Mathematically, It is defined as:
$$
\text{BCE} = – \frac{1}{N} \sum_{i=1}^{N} \left[ y_{\text{true}} \log(p_{\text{pred}}) + (1 – y_{\text{true}}) \log(1 – p_{\text{pred}}) \right]
$$
Where, 
- **N**: This is the total number of samples in your dataset.
- **$y_{\text{true}}$**: This is the actual label for each sample. In a binary classification problem, this would be either 0 or 1.
- **$y_{\text{pred}}$**: This is the predicted probability that the sample belongs to the positive class (class 1). It’s the output of your model.
- **log**: This is the natural logarithm function.

The formula calculates the loss for each individual sample using `y_true * log(y_pred) + (1 - y_true) * log(1 - y_pred)`, and then averages these losses over all samples.

The term `y_true * log(y_pred)` calculates the loss for the positive class (when the actual label `y_true` is 1). If the model predicts a high probability for the positive class (meaning `y_pred` is close to 1), this term will be close to 0. But if the model predicts a low probability (meaning `y_pred` is close to 0), this term will be a large positive number, contributing to a larger overall loss.

The term `(1 - y_true) * log(1 - y_pred)` calculates the loss for the negative class (when the actual label `y_true` is 0). If the model predicts a low probability for the positive class (meaning it predicts a high probability for the negative class, so `y_pred` is close to 0), this term will be close to 0. But if the model predicts a high probability for the positive class (meaning `y_pred` is close to 1), this term will be a large positive number, contributing to a larger overall loss.

So, the Binary Cross-Entropy Loss formula effectively measures how well the model’s predictions align with the actual labels. It penalizes confident but incorrect predictions more heavily, which helps the model learn to make more accurate predictions over time.

Below is the Python code with manual implementation and using PyTorch with corresponding results:

```python
import torch  
import torch.nn as nn  
  
class BinaryCrossEntropy_Loss:  
"""  
This class provides two methods to calculate Binary Cross-Entropy Loss.  
"""  
def __init__(self):  
pass  
  
@staticmethod  
def binary_cross_entropy_manual(y_pred, y_true):  
"""  
Calculate Binary Cross-Entropy Loss manually.  
  
Parameters:  
y_pred (torch.Tensor): The predicted probabilities.  
y_true (torch.Tensor): The actual labels.  
  
Returns:  
torch.Tensor: The calculated Binary Cross-Entropy loss.  
"""  
def sigmoid(x):  
return 1 / (1 + torch.exp(-x))  
  
N = y_pred.shape[0]  
y_pred = sigmoid(y_pred)  
loss = -1 / N * torch.sum(y_true * torch.log(y_pred) + (1 - y_true) * torch.log(1 - y_pred))  
return loss  
  
@staticmethod  
def binary_cross_entropy_pytorch(y_pred, y_true):  
"""  
Calculate Binary Cross-Entropy Loss using PyTorch's built-in function.  
  
Parameters:  
y_pred (torch.Tensor): The predicted probabilities.  
y_true (torch.Tensor): The actual labels.  
  
Returns:  
torch.Tensor: The calculated Binary Cross-Entropy loss.  
"""  
y_pred = torch.sigmoid(y_pred)  
loss_fn = nn.BCELoss()  
loss = loss_fn(y_pred, y_true)  
return loss  
  
if __name__ == "__main__":  
def binary_cross_entropy_test(N=10, C=2):  
"""  
Test the BinaryCrossEntropy_Loss class with some random data.  
  
Parameters:  
N (int): The number of samples.  
C (int): The number of classes.  
"""  
y_true = torch.randint(C, size=(N,)) # generate vector (N,) with 0's and 1's  
y_true = y_true.float()  
print(f"y_true: {y_true}")  
y_pred = torch.randn(N, 1).squeeze() # generate (N, C) matrix with normal distribution values [0:1]  
print(f"y_pred: {y_pred}")  
  
binary_cross_entropy_manual = BinaryCrossEntropy_Loss.binary_cross_entropy_manual(y_pred, y_true)  
print(f"binary_cross_entropy_manual: {binary_cross_entropy_manual}")  
  
binary_cross_entropy_pytorch = BinaryCrossEntropy_Loss.binary_cross_entropy_pytorch(y_pred, y_true)  
print(f"binary_cross_entropy_pytorch: {binary_cross_entropy_pytorch}")  
  
binary_cross_entropy_test()
```
```python
>>> y_true: tensor([0., 0., 0., 0., 1., 0., 0., 0., 0., 1.])  
>>> y_pred: tensor([ 1.8055, 0.9193, -0.2527, 1.0489, 0.5396, -1.2046, -0.9479, 0.8274,  
-0.0548, -0.1902])  
>>> binary_cross_entropy_manual: 0.8834649920463562  
>>> binary_cross_entropy_pytorch: 0.8834649920463562
```
## Where It is Used
Binary Cross-Entropy is widely used in the field of deep learning, especially in tasks like image recognition, natural language processing, and other areas where binary classification is needed.
## Advantages
1. **Probabilistic Interpretation**: Binary Cross-Entropy loss provides a probabilistic interpretation. It allows the model to output the probabilities of each class, which could be useful in understanding the model’s confidence in its decisions.
2. **Stability**: When used with a sigmoid activation function, Binary Cross-Entropy can be quite stable, as it’s less likely to reach extreme values.

## Disadvantages
1. **Binary Classification Only**: Binary Cross-Entropy is only suitable for binary classification problems. For multi-class classification problems, one would need to use Categorical Cross-Entropy.
2. **Sensitive to Imbalanced Data**: Binary Cross-Entropy can be sensitive to imbalanced datasets, where the number of samples in each class is not equal.
3. **Numerical Stability**: Although generally stable, the log operations in Binary Cross-Entropy can sometimes lead to numerical instability.
