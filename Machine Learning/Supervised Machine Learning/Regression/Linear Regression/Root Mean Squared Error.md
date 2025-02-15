---
aliases:
  - RMSE
---
- The square root of the mean of the square of all the errors.
- It is considered an excellent general-purpose error metric for numerical predictions.
- RMSE is a good measure of accuracy, but only compare prediction errors of different models or model configurations for a particular variable and not between variables, as it is scale dependent.
- It is the measure of how well a regression line fits the data points.

The formula for calculating RMSE is:
$$
RMSE = \sqrt{ \frac{1}{n} \sum_{i=1}^n (y_{i}-\hat{y}_{i})^2}
$$
Where, 
- $y_{i}$ : Actual Value
- $\hat{y}_{i}$ : Predicted Value
- $n$ : number of observations

> **Note:** The different between the actual value and the predicted values is known as residuals.

## Significance of RMSE
- **Scale-Dependent**: RMSE has the same units as the target variable. A lower RMSE indicates better model performance, but the value must be compared with the scale of the target variable to make sense.
- **Sensitive to Outliers**: Since RMSE square the error terms, larger errors have a disproportionately large effect, making RMSE sensitive to outliers.
- **Comparing Models**: RMSE can be used to compare models. A model with a lower RMSE value is generally considered better at predicting the target variable.

Interpreting RMSE involves understanding its relationship with the data: 
- **Low RMSE:** Indicates that the model's predictions are close to the actual values.
- **High RMSE**: Indicates large errors in prediction.