Stochastic Gradient Descent (SGD) is a variant of the Gradient Descent algorithm that is used optimizing [Machine Learning](../../Machine%20Learning/Machine%20Learning.md) models. It addresses the computational inefficiency of traditional Gradient Descent method methods when dealing with large datasets in machine learning.

In SGD, instead of using the entire dataset for each iteration, only a single random training example (or a small batch) is selected to calculate the gradient and update the model parameters. This random selection introduces randomness into the optimization process, hence the term "stochastic" in stochastic Gradient Descent.

The advantage of using SGD is its computational efficiency, especially when dealing with large datasets. By using a single example or a small batch, the computational cost per iteration is significantly reduced compared to traditional Gradient Descent methods that require processing the entire dataset.
## Algorithm
- **Initialization**: Randomly initialize the parameters of the model.
- **Set Parameters**: Determine the number of iterations and learning rate (alpha for updating the parameters).
- **Stochastic Gradient Descent Loop**: Repeat the following steps until the model converges or reaches the maximum number of iterations.
	- Shuffle the training dataset to introduce randomness.
	- Iterate over each training example (or a small batch) in the shuffled order.
	- Compute the gradient of the cost function with respect to the model parameters using current training rate.
	- Evaluate the convergence criteria, such as the difference in the cost function between iterations of the gradient.
- Return Optimized Parameters: Once the convergence criteria are met or the maximum number of iterations is reached, return the optimized model parameters.

In SGD, since only one sample from the dataset is chosen at random for each iteration, the path taken by the algorithm to reach the minima is usually noisier than your typical Gradient Descent algorithm. But that doesn’t matter all that much because the path taken by the algorithm does not matter, as long as we reach the minimum and with a significantly shorter training time.
#### The path taken by Batch Gradient Descent is shown below:
![center](../images/gradient%20decent%20path.png)