# Neural Network Charity Analysis

## Overview
The purpose of this analysis is to determine if a binary classifier can be created that will predict whether applicants will be successful or not when funded by Alphabet Soup.

### Resources:
- Data: charity_data.csv
- VS Code, Jupyter Notebook
- Packages: SciKitLearn, tensorflow, pandas

## Results 

### Data Preprocessing

**What variable(s) are considered the target(s) for your model?**

The target for this model is whether or not the non-profit will be successful.  In the dataset, the column name is: "IS_SUCCESSFUL".

**What variable(s) are considered to be the features for your model?**

This dataset included all of the following features:
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested

**What variable(s) are neither targets nor features, and should be removed from the input data?**

EIN and NAME columns were just for identification and were dropped before splitting or scaling the data.

### Compiling, Training, and Evaluating the Model

**How many neurons, layers, and activation functions did you select for your neural network model, and why?**

I experimented with a variety of different combinations, but found that two hidden layers was sufficient to get 72.5% accuracy.  In my final run, my first hidden layer had 100 neurons, and my second hidden layer had 75 neurons.  Increasing to three hidden layers did not improve accuracy (likely due to overfitting of data).  I also experimented with many different activation functions, but had the highest accuracy with relu and sigmoid.

**Were you able to achieve the target model performance?**

Unfortunately, I was not able to exceed 75% accuracy on test data.  

**What steps did you take to try and increase model performance?**

I documented a total of six optimization runs.  My changes and results are in the table below:

| Optimization | Changes                                 | Results                               |
| -----------  | -----------                             | -----------------
| 1            | Changed activation function to tanh     | did not make a significant difference |
| 2   | dropped `SPECIAL_CONSIDERATIONS` and `STATUS` and `USE_CASE`       | no change, so I left them out |
| 3   | increased nodes to first hidden layer        | no significant change |
| 4   | adjusted binning levels for classification_counts        | made accuracy worse |
| 5   | dropped income amount        | made accuracy much worse |
| 6   | added a third hidden layer        | made accuracy worse |

*Upon investigating the data, there were only 27 instances where `SPECIAL_CONSIDERATIONS` had an alternate value, and only 5 instances where `STATUS` had an alternate value, so I felt those features were irrelevant and should be dropped even though accuracy did not change.

## Summary

I am disappointed that I was not able to achieve 75% accuracy with a deep learning model.  I considered increasing the amount of epochs significantly, but the amount of time it took for each run became prohibitive.  As an investigation, I tried classifying the data using a RandomForest classifier (see below) and got a very similar, albeit slightly lower, accuracy.  Because of the ease of using and running a RandomForest classifier, I would recommend the model be used, if a more efficient deep learning model cannot be found.

![](
