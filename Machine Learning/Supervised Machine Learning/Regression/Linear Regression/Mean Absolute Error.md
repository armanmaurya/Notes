- Calculates the **average difference between the calculated values and actual values.**
- Also known as scale dependent accuracy, as it calculates error in observations taken on the same scale used to predict the accuracy of the machine learning model.

**Mathematical Formula**
$$
\text{MAE} = \frac{1}{n}\sum_{i=1}^n |y_{i}-\hat{y_{i}}|
$$
Where, 
- $y_{i}$ : Actual value for the ${i^{ih}}$ observation
- $\hat{y_{i}}$ : Calculated value for the $i^{th}$ observation
- $n$ : Total number of observations
## Calculating Mean Absolute Error
##### Method 1: Manual Calculation of MAE
```python
actual = [2, 3, 5, 9]
calculated = [3, 3, 8, 7, 6]

n = 5
sum = 0

for i in range(n):
	sum += abs(actual[i]- calculated[i])
	
error = sum/n
print("Mean absolute error :" + str(error))
```
##### Method 2: Using `sklearn.metrics`
```python
from sklearn.metrics import mean_absolute_error as mae

# list of integers of actual and calculated
actual = [2, 3, 5, 5, 9]
calculated = [3, 3, 8, 7, 6]

# calculate MAE
error = mae(actual, calculated)
print("Mean absolute error : " + str(error))
```
## Why Choose MAE
1. **Robustness to Outliers**: MAE is resilient to outliers, treating all errors equally.
2. **Linear Penalty**: The linear nature of MAE means that each error's impact on model learning is directly proportional to its magnitude.
