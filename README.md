# Inductive-conformal-prediction for Regression
Implementation of Inductive conformal prediction with Lasso regression model on diabetes dataset. The dataset is split into train data and test data, and lasso model is trained with train data and makes predictions on test data. The inductive conformal predictor gives a prediction intervals, in which the true label value lies with a specific confidence,based on the significance level specified by the user.

## Dataset
The diabetes dataset consists of 10 features, which can be used to predict a quantitative measure of disease progression one year after baseline. The features are AGE, SEX, BMI, BP, S1, S2, S3, S4, S5, S6(S1-S6:-Blood serum levels).

## Lasso Regression
L1 regularisation, which penalises the absolute values of the coefficients, is applied in the linear regression technique known as Lasso regression (Least Absolute Shrinkage and Selection Operator). As a result, feature selection is successfully carried out, with certain coefficients ending up absolutely zero. The Lasso objective function adds a penalty proportionate to the total of the absolute values of the coefficients to the least squares loss. The regularisation parameter λ determines how harsh the penalty is. With a small adjustment to λ Lasso can improve prediction accuracy and interpretability while striking a compromise between a well-fitting model and simplicity.
#### Parameter selection
The hyper parameter(⍺) for lasso regression is caluculated using cross validation and grid search. Here we consider a range of values for ⍺, and then select the ⍺ that yields best cross validation score for the model.

## Inductive conformal preduction
* Inductive conformal prediction (ICP) provides valid prediction intervals or sets, quantifying uncertainty. It splits the dataset into a training set and a calibration set. The training set is again divided divided into training set proper and calibration set, and the model is trained on training set proper. The non conformity scores of the calibration set samples are caluculated by the taking the absolute value of difference between predicted value and true value, and then these non conformity scores are arranged in ascending order.
* If the size of calibration set is n, then we caluclate k=[(1-∑)(n+1)], here k is the ceiling value of (1-∑)(n+1) and ∑ is the significance level.
* if the sequence of non conformity scores is C(1)<C(2)<......<C(n), Then the prediction interval for test sample is [y-C(k),y+C(k)], where y is predicted value by the model.

## Program
* To use this program, you need to have Python installed on your machine. You can install the required dependencies using pip.
* The libraries required are sklearn and numpy
#### Input 
* The inductive conformal predictor takes the significance level(∑) as input.
#### Output
* The program gives length of prediction sets, prediction intervals on test samples and test error rate at given significance level as output

## References
Papadopoulos, H., Kostas Proedrou, Vovk, V. and Gammerman, A. (2002). Inductive Confidence Machines for Regression. pp.345–356. doi: https://doi.org/10.1007/3-540-36755-1_29.
