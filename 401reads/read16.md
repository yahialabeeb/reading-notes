# Machine Learning 
* Machine learning is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.
## Machine Learning ≠ Algorithms
* biggest misconceptions about machine learning

* Machine learning is a comprehensive approach to solving problems and individual algorithms are only one piece of the puzzle. The rest of the puzzle is how you apply them the right way.

## What makes machine learning so special?
* the computer must be able to learn patterns that it's not explicitly programmed to identify.

## A set of basic questions about the dataset should be answered 

- How many observations do I have?
- How many features?
- What are the data types of my features? Are they numeric? Categorical?
- Do I have a target variable?
## Ways to analyse data
1. Plot Numerical Distributions 
2. plot Categorical Distributions
3. Plot Segmentations

## Data cleaning
* Data cleaning is one those things that everyone does but no one really talks about.

## Why Data Cleaning  

Because of Better data beats fancier algorithms as known garbage in gets you garbage out

##
* Remove Unwanted observations
* Fix Structural Errors
* Filter Unwanted Outliers
* Handle Missing Data
  - Missing categorical data
  - Missing numeric data

## Feature Engineering?
* Feature engineering is about creating new input features from your existing ones.

* Infuse Domain Knowledge
* Create Interaction Features
* Combine Sparse Classes
* Add Dummy Variables
* Remove Unused Features


## Pick ML Algorithms?
### Linear Regression is Flawed
1. It's prone to overfit with many input features.
1. It cannot easily express non-linear relationships.

### Regularization 
* It is a technique used to prevent overfitting by artificially penalizing model coefficients.

1. It can discourage large coefficients (by dampening them).
2. It can also remove features entirely (by setting their coefficients to 0).
3. The "strength" of the penalty is tunable. (More on this tomorrow...)

- Regularized Regression Algos
  - Lasso Regression
  - Ridge Regression
  - Elastic-Net
- Decision Tree Algos
- Tree Ensembles
   - Bagging
   - Boosting
   - Random forests
   - Boosted trees

## model training 

- Split Dataset
- Hyperparameters

  - Model parameters are learned attributes that define individual models.

  - Hyperparameters express "higher-level" structural settings for algorithms.

- Validation 
- Fit and Tune Models
- Select best Model
  - performance
  - robustness
  - consistency
  - win condition