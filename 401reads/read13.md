# Linear regression in Python 

## Scikit-learn 
* It is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction.
* import linear regression from sci-kit learn module

### Important functions 

lm.fit() -> fits a linear model

lm.predict() -> Predict Y using the linear model with estimated coefficients

lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.

### Predicting 

* using lm.predict.  

* To check error mean squared error is used.
* If the mean squared error has increased. So this shows that feature is not a good predictor of target

### Training and validation data sets

* In practice you wont implement linear regression on the entire data set, you will have to split the data sets into training and test data sets.

### How to do train-test split
* Scikit learn provides a function called train_test_split 
### Residual Plots
Residual plots are a good way to visualize the errors in your data