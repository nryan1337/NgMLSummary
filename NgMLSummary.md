
# Summary of Machine Learning Coursera Course

## Description

This was pretty much the greatest online course I have ever completed. I wanted to have a summary here as a reminder of all the points that were covered and I want to be able to help others to get the info in one place too. If you haven't completed the course do it and the assignments too!

## Week 1: Introduction

### Topics Covered

* Supervised and Unsupervised Learning
* Model Representation
* Cost Function
* Gradient Descent
* Linear Algebra Review

### Supervised and Unsupervised Learning

__Supervised learning__ is the case where the outcome variable is known e.g.
* predicting house prices
* classifying tumor as benign or malignant

The machine learning problem is training a model on past data (with a known outcome) to predict future data (with an unseen or unknown outcome).

__Unsupervised learning__ is the case where there is no outcome variable, and our task is to look for patterns in the data e.g.
* customer segmentation (grouping) for a marketing campaign
* examining social network data to look for friendship groups

The machine learning problem is to cluster the data into meaningful groups.

### Model Representation

In the case of a supervised learning problem:

* m is the number of training examples
* X are the input variables in the training data
* y is the outcome variable
* h is the learning algorithm that maps the Xs to ys.

e.g. X is the size of the house, number of bedrooms etc and y is the price of the house.

### Cost Function

* h is the learning algorithm (also called the hypothesis)
* h(x) = theta0 + theta1 * x
* how do we choose theta0 and theta1?
* J(theta0, theta1) = 1/2m * sum(h(xi) - yi)^2 where i is the ith training example, and J is the cost function.
* later on when you write matlab code the vectorised implementation of the above looks like this:
J = 1 / 2m x sum((X*theta - y).^2);
* basically the cost function gives you an idea of how much your predicted values differ from your outcome values: actual minus expected idea.

### Gradient Descent

* The idea with gradient descent is that we learn some theta parameters using our hypothesis, then we look at what value our cost function gives us
* we then keep changing the theta values to give us a smaller value of our cost function
* then we keep repeating the process until we reach a global minimum value (or something like a global minimum) where updating the thetas doesn't reduce the cost function any more
* then we stop and keep the final theta values.

Practically this is how we do it (note we have to feed our previous step's theta values into the current calculation).

this is the case where we have 2 theta parameters, and say we want 100 iterations of gradient descent:

the alpha parameter can be thought of as the size of the steps towards a global minimum in gradient descent, too big and you overstep the mark, too small and it may not converge in a reasonable number of steps.

What the first eqns are saying is: temp parameter = theta - alpha * derivative of the cost function

for iter = 1:num_iters # num_iters = 100

&nbsp;&nbsp; temp0 = theta(1) - alpha/m*sum((X*theta - y));

&nbsp;&nbsp;temp1 = theta(2) - alpha/m*(X*theta - y)'*X(:,2);

&nbsp;&nbsp;  theta(1) = temp0;

&nbsp;&nbsp;  theta(2) = temp1;

Then we feed these theta values into our cost function calc.

Now in the case of more than 2 parameters the calc looks like this:

for iter = 1:num_iters # num_iters = 100

&nbsp;&nbsp; delta = ((theta'*X' - y')*X)';

&nbsp;&nbsp; theta = theta - alpha/m*delta;

Then we feed these theta values into our cost function calc.
