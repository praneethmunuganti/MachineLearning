# Machine Learning

This repo is a consolidation of my learning on machine learning. Intent of this repo is to act as a showcase and as a knowledge base.



Below are high level notes on ML and project links. 

- Supervised learning: inputs are mapped to labelled output, you want machine to learn how to correctly label an output using set of inputs is supervised machine learning - Regression, classification, recomender systems
- Unsupervised - data isn't associated with any output label - clustering, anomaly detection, dimensionality reduction
- Supervised model/concepts
  - Linear regression: Fit a line to input data vs output. f(x) - wx+b (Univariate linear regression as a simple example)
  - Cost function: Used to find best parameter to your model
    - Average sum of squared error is an example. For regressions, sum of squared error is a commonly used cost function
    - Contour plots are best to visualize cost functions (how cost function value changes with changing parameter values)
  - Gradienct descent: It is an algorithm you can use to minimize any function
    - Specifically for linear regression, it can be used to determine which values w and b will minimize cost function
    - Alpha/learning rate controls how big of the step you take downhill towards minimum. This is between 0 and 1
    - Note: A cost function like sum of squared error is convex and will only have one minimum. You would have a different approach/thought process if a cost function has multiple minimum and you have to find the global minimum (Notes on how would follow in points below)
    - How do know if the gradient descent is working well? You look at the learning curve. The curve should indicate decrease in cost with each iteration. Any spike in this curve indicates something is wrong
    - Another way to determine if gradient descent has effectively minimized cost function is automatic convergence test. Set a threshold where further iteration not decrease the cost by this threshold determines convergence. Note this threshold is called convergence criterion or tolerance
    - Choosing right learning rate: start by 0.001, then 0.01 and 0.1, then 1 and see how the learning curve. This curve should be smooth
  - Feature scaling
    - Helps algorithms like gradient descent to converge faster and more efficiently
    - Approaches
      - Divide values by maximum
      - Mean normalization: (each value - mean) / (max of values - min of values)
      - z score normalization: (each vlaue - mean) / standard deviation
    - General aim is to have inputs scaled to -1 to 1, -2 to 2, basically equally distributed
  - Feature engineering
    -  Creating a new feature which would add value/increase accuracy to the model prediction
  - Overfitting
    - We want models to generalize well, make good predictions on new input data
		- Fitting training data too well is overfitting, high variance(high variance with the new data point), will not generalize
		- Addressing overfitting
		  - Get more training data
			- Use fewer features - feature selection. Too many features plus very little data will overfit the model
			- Regularization helps mitigate overfitting problem - shrink values of parameters, keep all features but prevent each feature to have less affect 
	- Underfitting
    - Model fits poorly, low accuracy, high bias
  

    





