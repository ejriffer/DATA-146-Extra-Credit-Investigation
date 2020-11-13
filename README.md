# DATA 146 Extra Credit Investigation

Emily Riffer

## Introduction

The data that was explored in this report was a household survey from the West African country Liberia. It describes the demographic composition of the country with data that describes the location, size, weath, gender, age, and education of the people. There are 48,218 data points, each with the six characteristics listed above. For the location column there are 15 unique responses, listed as numbers from 1 to 15. The size column has 25 unique responses, ranging from 1 to 53. The wealth column has 5 unique responses, listed as numbers from 1 to 5 where 1 was the lowest wealth class and 5 was the highest. The gender column had two unique responses 1 and 2. The education column has 6 unique answers, 0, 1, 2, 3, 8, and 9, skipping 4-7, where 0 was no education and 9 was the highest. The age column has ages ranging from 0 to 99.

Below are histograms that show the distribution of the responses for each column of the data table. 

[Location Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/1#issue-741061576)

[Size Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/2#issue-741106944)

[Age Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/4#issue-741109446)

[Gender Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/5#issue-741109792)

[Wealth Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/6#issue-741110116)

[Education Histogram]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/3#issue-741109148)

The purpose of this report is to analyze this data and see if any classification models can be used to accurately predict what the education level of a given person is based on their responses in the other columns. Before any classification models were run on the data it was first split into testing and training groups using the sklearn train_test_split library, where the 50% of the data was used as training and the other 50% used as a testing set. A random state of 146 was used to ensure results could be repeated. The classification models that were run include Logistic Regression, kNN, Decision Tree Classifier, and Random Forest Classifier. The results were standardized using MinMaxScaler, RobustScaler, StandardScaler, and Normalizer all from sklearn's preprocessing library. 

## Logistic Regression

The first classification run on the data was a Logistic Regression model and the accuracy of this model was 57.21%. The mean squared error (mse) of running a logistic regression with no scaler was 1.06. Then different scaling techniques were used on the data to see if the accuracy of the Logistic regression model could be improved. First MinMaxScaler from sklearn was used, and the accuracy only improved by 0.02% to 57.23%, and the use did not improve at all. Then RobustScaler and StandardScaler were used and both caused no improvement in the model’s accuracy or in the mse. The only scaling technique that caused a distinct improvement in the model’s accuracy was Normalizer. Normalizer compresses all of the data point to the unit vector, between -1 and 1. After Normalizing the data the accuracy of the model was improved to 64.7%. The mse of using Normalizer improved to 0.77. So, of all the Logistic Regressions run, using Normalizer produced the best model at 64.7%. 

## kNN

The next classification model run on the data was a kNN model. A range of values of k were tested, as seen in the graph below and the value k = 30 had the highest test accuracy at 68.5%. The mse for k = 30 was 0.68. After finding an optimal k value, then the data was standardized with the 4 standardization techniques used previously. For the kNN model all standardizers performed worse than no standardization. The MinMaxScaler performed the best of the scalers, however, having an accuracy of 64.6% and a mse of 0.82. The RobustScaler and StandardScaler both performed almost as well, with accuracies of 64.1% each, both with mses of 0.83. The Normalizer performed the worst, with an accuracy of 61.5% and a mse of 0.88. 

So, the best kNN model was with no scaler, at 68.5%, which outperforms the best Logistic Regression model by almost 4%. 

[kNN Graph]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/7#issue-741755847)

## Decision Tree Classifier

The next classification model run on the data was a Decision Tree Classifier model. A range of values for max depth and min sample split were tested, and the values of max depth = 7 and min sample split = 4 had the highest test accuracy at 71.8% and a mse of 0.63 After finding these optimal values the data was then standardized using the 4 standardization techniques used for Logistic Regression and kNN. MinMaxScaler, RobustScaler, and StandardScaler all performed just under the Decision Tree with no standardization, all coming in with accuracies of 71.1% and mses of 0.64. The Normalizer performed the worst, with an accuracy of 67.3% and a mse of 0.70. 

So the best Decision Tree model was with no scaler at 71.8%, which outperforms the best kNN and Logistic Regression models. 

## Random Forest Classifier

The last classifier model run on the data was a Random Forest Classifier model. A range of values for max depth, min sample split, and the number of trees were tested, and the values of number of trees = 50, max depth = 9, and min sample split = 4 had the highest test accuracy at 72.5% and a mse of 0.61. After finding these optimal values the data was then standardized using the 4 standardization techniques used for Logistic Regression, kNN, and Decision Tree Classifier. MinMaxScaler, RobustScaler, and StandardScaler all performed as well as the Random Forest Classifier with no standardization at 72.5%, with a mse of 0.61 as well. The Normalizer performed the worst at 69.1% accuracy with a mse of 0.67. 

So the best Random Forest Classifier, rounding out to 2 decimal points was the RoubustScaler at 72.47%, which outperforms the best Decision Tree, kNN, and Logistic Regression models. 

## Conclusion

Comparing all of the classification models run on this data the most accurate was the Random Forest Classifier at 72.47%. So, based on the location, wealth, gender, age, and size of the individual this model will accurately predict their education level 72.47% of the time. Throughout this report the accuracy improved, but there are most likely different models, or models with different parameters that can improve upon the best accuracy found here.

[Final Comparison]!(https://github.com/ejriffer/DATA-146-Extra-Credit-Investigation/issues/8#issue-741765851)
