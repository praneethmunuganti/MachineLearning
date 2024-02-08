# Machine Learning

This repo is a consolidation of my learning on machine learning. Intent of this repo is to act as a showcase and as a knowledge base.


Below are high level notes on ML and project links.

### Basic definitions

- Supervised learning: inputs are mapped to labelled output, you want machine to learn how to correctly label an output using set of inputs is supervised machine learning - Regression, classification, recommender systems
- Unsupervised - data isn't associated with any output label - clustering, anomaly detection, dimensionality reduction

### Supervised learning

- Linear regression: Fit a line to input data vs output. f(x) - wx+b (Univariate linear regression as a simple example)

#### General concepts
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
- Overfitting, intro to regularization
  - We want models to generalize well, make good predictions on new input data
	- Fitting training data too well is overfitting, high variance(high variance with the new data point), will not generalize
	- Addressing overfitting
	  - Get more training data
		- Use fewer features - feature selection. Too many features plus very little data will overfit the model
		- Regularization helps mitigate overfitting problem - shrink values of parameters, keep all features but prevent each feature to have less affect
- Underfitting
  - Model fits poorly, low accuracy, high bias


### Unsupervised learning
- K means clustering
	- Randomly initialize K clusters centriods (these are not the point themselves)
	-  Find distance from each cluster centriod to every point and assign points to cluster centriod
	-  Move cluster centriods using mean of average pionts assigned to cluster K
		-  What happens if a cluster has 0 training examples assigned to it, eliminate such clusters, if we need more clusters, randomly assign another set of cluster centriods
	-  Repeat step 2,3 till convergence, i.e., the cluster centriods do not changed anymore when we find the average of points assigned to a cluster
	-  Notes
		- K means is also applied to clusters not clearly separated, like height, weight and trying to find 3 clusters for s,m,l t shirt sizes (K=3)
		- Want to minimize the cost function = average of distance squared (distance from cluster centriod to each point) - called distortion cost function
		- Every step of K means is to reduce the cost function. If it goes up with each step, something is wrong. If the cost function is constant or going down very slowly, this is when we can stop the K means as it has converged
	- Initializing K means
		- How can we randomly guess the best initial centriods?
		- Intial selection could change the final clusters completely. Better to try multiple random initializations to get the best local optima
			- Create multiple random inital cluster centriods and find cost function(after convergence). Pick the one the gives the least cost.
	- How to pick the right way of K?
		- Using elbow method, plotting cost function on Y axis and no of clusters on X axis
			- Choose whenever there is a drop
			- Also choose a value for the purpose of the clustering
      - Can also do this using silouette score
