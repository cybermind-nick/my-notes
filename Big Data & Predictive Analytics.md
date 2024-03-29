## Jan 17, 2024
### Tutorial 1

Exercise 1: Assume you toss a fair coin and four times in a row and record the number of heads. You represent the number of heads with the random variable X. Answer the following questions:
a) What is the type of random variable X?
b) Which probability distribution could be used to model this situation accurately
c) Write down the sample space for this event
d) Using python, determine the probability of getting 0, 1, 2, 3, 4 heads. Represent this probability distribution with the help of a table and a graph Analyze your results
e) Repeat your work for different values of n and p

### Personal NOTE
In Binomial distribution, *__n__* is the number of 'rounds' to play. ie, the number of times a choice can be made. WHILE __*p*___ is the probability that our random variable of choice (e.g get a head on a coin toss, so RV X = p(head)).

## 22 Jan, 2024 (Lecture)
__Kaggle! Kaggle!! Kaggle!!!__
We use Inferential statistics here a lot, especially to build the models

### Hist and Bar
Histograms are for numerical data, bar charts are for categorical data

## 29 Jan, 2024 (Simulations, Confidence Intervals, Hypothesis Testing)

CMF & CDF shine here

CDF -> Discrete
CMF -> Continuous

### Note:
Always normalise your AOC (Area under curve) to get an accurate probability (for continuous probabilities of the form P(X < x) | P(X > x) etc)
To normalize is to equate the AOC to 1.

We always use a normal distribution (z-distribution) for confidence intervals (confidence levels) because we use normal distributions for ___sampling distributions___


### Hypothesis Testing
H0 and H1

H0 is called the Null Hypothesis
H1 is called the alternative hypothesis

Null Hypothesis is the statement of no change. It assets that there is no difference in a value after an event has occurred. ie, it points to a specific value, (=) is invoked

Alternate hypothesis is a statement of change. It points to an inequality (!=) and can also be expressed to as a value being greater than (>) or less than (<) a value after an event has occurred

A good example is to say that there is no difference in performance of employees after a training (H0 - Null Hypothesis), while the alternate hypothesis (H1) is to asset that there is a difference/change in performance. In this case, we expect it to be greater


## Note
We use the z-test when the std_dev is known and the sample size is signifcant and we use the t-test when we do not know the std_dev and the sample size is small

## 5 Feb, 2024
### Data Cleaning and Transformation

This two step process is typically just called ___DATA MUNGING___ 
It is an iterative process

Business Understanding -> Data Understanding $->$ Data Preparation $->$ Modelling $->$ Evaluation $->$ Deployment $->$ (Back to step 1 as needed)

### Correlation
Measures how much two (or more variables) are related to each other. Sometimes, the relationship is well-defined, sometimes, it's a lot more obscure
We have:
- Postive correlation. As y 
- Negative correlation

The value of correlation is in range(-1,1) ie
$-1 \le x \le 1$ 
if x == 0, there is no correllation
if x == 1, there is perfect positive correlation
if x == -1, there is perfect negative correlation

We have: High, Low, and Average correlation

Correlation of RV $X \space and \space Y$ 
$$corr(X,Y) = \frac{cov(X,Y)}{\sqrt{{\sum_{i=1}^n}(x_i - \bar{x})^2}  {\sqrt{{\sum_{i=1}^n}(y_i - \bar{y})^2}}}$$
This essentially just means their covariance divided by the product of their standard deviations

Incase I'm wondering, covariance is calculated thus
$$cov(x,y) = \sum_{i=1}^n(x_i-\bar{x})(y_i - \bar{y})$$
### To Note: 
Correlation ***IS NOT*** Causation

Causation basically says that one event causes another event to occur or at least affects its occurence

Correlation only implies a relation between two things.
All causal events are correlated, but not all correlation is causation

#### Spurious correlation
This refers to a connection between two variables that appear to be correlated but are actually not
### Feature Selection
When building a model, all the features of a dataset may not be import, drop them. The variables (ie, columns) that are left over are the ___features___ 

Feature selection is the procedure used to find the subset of features (ie, variables) of a dataset that produces a model for the dataset.
This is done using different techniques, amongst which Correlation is an important one

#### Good Features
Good features are variables that are not really correlated with each other, but are highly correlated with the outcome we want.

If two features are highly correlated with each other, it is a good idea to remove one of them

A good rule of thumb for the feature to example ratio is
$$Number\space of\space Examples = Number\space of\space features \times
10$$

We have two types of feature selection
- Supervised selection
- Unsupervised selection

We learn the features of a variable this way
Supervised learning has a ___target variable___ while Unsupervised selection

#### The Key Idea
The key Idea behind feature selection is ___Dimensionality Reduction___  (so WTF is dimensionality reduction?)

### Outliers
If an outlier is not a natural variation (a genuine outlier) get rid of it
#### Methods
##### Descriptive methods
- Standard Deviation method
- Interquartile range method

###### Standard Deviation
This is basically going to use the z-score (because the z-score and filter out the edges of the curve that falls outside the confidence interval)

###### Interquartile range
Check the range of the 1st quartile and 4th quartile

### Feature Scaling
Feature scaling is a method used to normalize the range of independent variables or features of data

__Why?__ It helps if all the features of a data are in the same scale (typically between 0 and 1)



## 12 Feb, 2024 (Lecture)
### Linear Regression (Model Building begins here!!!)

#### What is Regression
A regression is a statistical technique that aims at estimating the relationship between a dependent variable and a set of independent variables
#### What is it used for
For predictions on continuous variables

The square in the cost function is the secret that makes gradient descent work (BECAUSE ITS DIFFERENTIABLE!!!)
$$J(\theta_0, \theta_1) = \frac{1}{2m}\sum_{i=0}^m(h_\theta(x^{(i)}) - y^{(i)})^2$$
The goal of this is to get the minimum value of this cost function. We use gradient descent here through differentiation
$$goal = minimize\space J(\theta_0, \theta_1)$$
#### Polynomial Regression
We will explore what happens when we choose a higher degree polynomial
##### What happens?
In curve fitting, if done well, it will always be better than a basic linear curve
###### Problem
A common problem with using very high degree polynomials is __overfitting__ 
When overfitting, the SSE value is typically $0$ or very close to it

## 26 Feb, 2024
### Random Forests
Can be used for both classification and regression, but is used predominantly for classification. It depends on Decision tree algorithms under the hood

#### Facts to note
- Leaves of the random tree are the labels (ie, y-value) of a Decision tree.
- It's good to note that some attributes can be repeated if they are part of a subtree
- In random forests, we do not need to perform feature selection. This is baked into it's architecture/ how it works.

#### Constructing a decision tree
Labelled data is used to construct a decision tree

The best attribute to use is one that can divide your data into decision sections cleanly, ie, it has a high correlation with the root node. Preferably we can use it to even arrive at an answer or it gets us to the leave nodes in as few steps as possible (Just like a binary tree).

A good heuristic to use is to measure the ___information gain___ upon selecting a feature/node. This is basically saying, choose the feature that removes the most entropy from the tree on each step. Super cool.

#### Building a Decision Tree
1. Start with a root node, say S
2. Find the best attribute to assign to S (based on the criteria discussed in Constructing a decision tree)
3. Divide S into subsets that contain possible values for the best attribute (Basically a double recursion call that encapsulates the second step)
4. Generate the decision tree node, which contains the best attribute
5. Recursively make new decision trees using the subsets of the datasets created in step 3
6. Continue this until there are no more classifications to make (ie, we arrive at all leaf nodes)

