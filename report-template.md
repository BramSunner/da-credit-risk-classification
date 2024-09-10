# Module 12 Report Template

## Overview of the Analysis

Using a dataset of historical lending activity, this project's focus was to identify the creditworthiness of borrowers.  
This dataset contained the following data columns: loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks, total_debt.  
As well as the label column: loan_status (where a value of 0 indicates a healthy loan and a value of 1 indicates an unhealthy loan).  

My goal was to build a supervised learning model that can predict the status of a loan given the data columns for the prediction.  
To begin this process, I read in the data and isolated the features from the label.  
After the isolation, I created a training and testing dataset using SKLearn's train_test_split.  
Then, I created a Logistic Regression model and fit it to the datasets.  
I tasked the model with predicting outcomes on both the training and testing data and then created both a confusion matrix and a classification report for both.  
Afterwards, I ran the dataset through various other models to see if I could improve upon the metrics for predicting creditworthiness.  

## Results

* Logistic Regression:
  * Precision: 0: 1.00 / 1: 0.87 -- Model has overfit the 0 cases and misses predictions of 1.
  * Recall:    0: 1.00 / 1: 0.89 -- Model has overfit the 0 cases and predicts 0 instead of 1 often.
  * F1-Score:  0: 1.00 / 1: 0.88 -- Shown again, the model has overfit for 0 cases and has a perfect f1 score there yet fails in the 1 cases.
  * Accuracy:  0.99 -- Overall, the model does not miss too many predictions but the problem is imbalanced so this score means nothing.
 
* Light Gradient Boosting Machine
  * Precision: 0: 1.00 / 1: 0.87 -- LGBM overpredicts positive outcomes.
  * Recall:    0: 1.00 / 1: 0.99 -- Recall is great across the board.
  * F1-Score:  0: 1.00 / 1: 0.93 -- F1 dips for positive outcomes due to low precision.
  * Accuracy:  1.00 -- This score is meaningless because of the imbalanced problem.

## Summary

The logistic regression model failed to produce correct predictions within an acceptable limit.  
It appears that it overfit to identify negative outcomes yet still failed to achieve success in predicting them.  
The metrics for the model are not great and I would not recommend productionalizing the model.  
Improvements that can be made would be using PCA to eliminate the issue of collinearity in the dataset before fitting the model.  
Another improvement is to use an alternative sampling technique to avoid overfitting the data.  
Even if preference is given to predicting either positive or negative outcomes, this model would not be good for that.  

The LGBM model did considerably better than the logistic regression model but still leaves a lot to be desired.  
Recall score was much, much higher meaning that if the point was to not have false positives then this could be a potential model to use.  
However, with the precision still at 0.87 and the scope of this project being to consider creditworthiness of an individual, I would not use the model.  
I would be interested to see if using PCA, alternative sampling techniques, or scaling the data would help this model improve its performance.  
I do see the potential with this model, but I would not productionalize it as is.

