It is a [Supervised Machine Learning](Supervised%20Machine%20Learning.md) technique, used to predict the value of the dependent variable for new, unseen data. It models the relationship between the input features and the target variable, allowing for the estimation or prediction of numerical values.

[Regression](Regression.md) analysis problem works with if output variable is a real or continuous value, such as “salary” or “weight”. Many different models can be used, the simplest is the linear regression. It tries to fit data with the best hyper-plane which goes through the points.
## Terminologies
- **Response Variable**: The primary factor to predict or understand in regression, also known as the dependent variable or target variable.
- **Predictor Variable**: Factors influencing the response variable, used to predict its values; also called independent variables.
- **[Outliers](../Neural%20Network/CNN/Outlier.md)**: Observations with significantly low or high values compared to others, potentially impacting results and best avoided.
- **Multicollinearity**: High correlation among independent variables, which can complicate the ranking of influential variables.
- **Underfitting and Overfitting**: Overfitting occurs when an algorithm performs well on training but poorly on testing, while underfitting indicates poor performance on both datasets.

## Types
There are several types of regression:

- **Simple Regression**
    - Used to predict a continuous dependent variable based on a single independent variable.
    - Simple linear regression should be used when there is only a single independent variable.
- **Multiple Regression**
    - Used to predict a continuous dependent variable based on multiple independent variables.
    - Multiple linear regression should be used when there are multiple independent variables.
- **NonLinear Regression**
    - Relationship between the dependent variable and independent variable(s) follows a nonlinear pattern.
    - Provides flexibility in modeling a wide range of functional forms.