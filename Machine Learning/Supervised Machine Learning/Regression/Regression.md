- It is a [Supervised Machine Learning](../Supervised%20Machine%20Learning.md) technique, used to predict the value of the dependent variable (target variable) for new, unseen data.
- It is a statistical approach used to analyze the relationship between a dependent variable (target variable) and one or more independent variables (predictor variables). 
### Terminologies Related to Regression Analysis
- **Response Variable**: The primary factor to predict or understand in regression, also known as **dependent variable** or **target variable**.
- **Predictor Variable**: Factors influencing the response variable, used to predict its values; also called **independent variables**.
- [Outlier](../../../Neural%20Network/CNN/Outlier.md) :- Observations with significantly low or high values compared to others, potentially impacting results and best avoided.
- **Multicollinearity**: High correlation among independent variables, which can complicate the ranking of influential variables.
- **Underfitting and Overfitting**: Overfitting occurs when an algorithm performs well on training but poorly on testing, while underfitting indicates poor performance on both datasets.

## Regression Types
There are two main types of regression:
- **Simple Regression**
	- Used to predict a continuous dependent variable based on a single independent variable.
	- Simple linear regression should be used when there is only single independent variable.
- **Multiple Regression**
	- Used to predict a continuous dependent variable based on multiple independent variables.
	- Multiple linear regression should be used when there are multiple independent variables.
- **Non-Linear Regression**
	- Relationship between the dependent variable and independent variables follows a nonlinear pattern.
	- Provides flexibility in modeling a wide range of functional forms.

## Algorithms
There are many different types of regression algorithms, but some of the most common include:
1. **[Linear Regression](Linear%20Regression/Linear%20Regression.md)**
   It is one of the simplest and most widely used statistical modes. This assumes that there is a linear relationship between the independent and dependent variables. This mean that the change in the dependent variable is proportional to the change in the independent variables.
2. **[Polynomial Regression](Polynomial%20Regression.md)**
   It is used to modal non-linear relationships between the dependent variable and the independent variables. It adds polynomial terms to the linear regression model to capture more complex relationships.
3. **[Support Vector Regression](Support%20Vector%20Regression.md)**
	- Method for predicting continuous values by finding a function that fits the data within a specified margin of tolerance (ϵ).
	- It focuses on minimizing errors outside this margin while keeping the model as simple as possible.
	- SVR supports kernels like linear, polynomial, and RBF, making it effective for capturing both linear and nonlinear patterns in the data.
1. **[Decision Tree Regression](Decision%20Tree%20Regression.md)**
	- Builds a decision tree to predict the target value. 
	- A decision tree is a tree-like structure that consists of nodes and branches. Each node represents a decision, and each branches represents the outcome of that decision. 
	- The goal of decision tree regression is to build a tree that can accurately predict the target value for new data points.
2. **[Random Forest Regression](Random%20Forest%20Regression.md)**
	- Ensemble method that Combines multiple decision tree to predict the target value.
	- Ensemble methods are a type of machine learning algorithm that combines multiple models to improve the performance of the overall models.
	- Random forest regression works by building a large number of decision trees, each of which is trained on a different subset of the training data.
	- The final prediction is made by averaging the predictions of all of the trees.