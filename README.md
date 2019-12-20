# machine_learning

Summary of Process and  Findings:

I reviewed the data, dropped nulls and then dropped all the columns, except for disposition and the four flag columns.  Any KBO that was flagged should be negative and any KBO that isn't flagged could be confirmed.

Next, I split the data into train and test groups and then used MinMaxScaler to standardize the data (confirmed feature values to a range between 0 - 1).  I fit and transformed the data and then trained the model using Support Vector Machine to determine the maximum margin of distinction between groupings.

SVC / SVM results
Training Data Score: 0.7514486123818237
Testing Data Score: 0.7502287282708143

Next Hyperparameter Tuning was used with GridSearchCV to determine C (1, 5, 10, 15, 20) and gamma variables (0.0001, 0.001, 0.01, 0.1, 1.0).  FItting the training data resulted in: 

{'C': 1, 'gamma': 0.0001}
0.7514486123818237

Making predictions on the test data resulted in:

           precision    recall  f1-score   support

    positive       0.00      0.00      0.00       528
   candidate       0.51      0.97      0.67       568
    negative       0.98      1.00      0.99      1090

    accuracy                           0.75      2186
   macro avg       0.50      0.66      0.55      2186
weighted avg       0.62      0.75      0.67      2186

The SVM model resulted in around 75% accuracy in making predictions.

The Hyperparameter Tuning resulted in around 75% with C = 1 and gamma = 0.0001.

Precision is the ratio of the correctly positive labeled items to all actually positive.
Recall is the ratio of the correctly positive labeled compared to all positive in reality.
F1 Score considers both precision and recall. It is the harmonic mean(average) of the precision and recall.

Based on weighed averages of Hyperparameter Tuning being even lower, I recommend using the simplier method of SVM.
