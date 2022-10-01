# What drives the price of a car

# Deliverables

The Jupyter notebook is available here:
[Jupyter Notebook](https://github.com/hossamfattah/mlmodule17/blob/46a4d4cecbfe8efb29bf9d67eafd256ce591672e/MyWorkF.ipynb)


# Discussion
I read the dataset and started to explore it. I used info() to see what columns and data types is each column

 No   Column     Non-Null Count  Dtype 
---  ------     --------------  ----- 
 0   age        4521 non-null   int64 

 1   job        4521 non-null   object

 2   marital    4521 non-null   object

 3   education  4521 non-null   object

 4   default    4521 non-null   object

 5   balance    4521 non-null   int64 

 6   housing    4521 non-null   object

 7   loan       4521 non-null   object

 8   contact    4521 non-null   object

 9   day        4521 non-null   int64 

 10  month      4521 non-null   object

 11  duration   4521 non-null   int64 

 12  campaign   4521 non-null   int64 

 13  pdays      4521 non-null   int64 

 14  previous   4521 non-null   int64 

 15  poutcome   4521 non-null   object

 16  y          4521 non-null   int64 
 


This is by price:

I plotted the count plot of bank loan decision (Yes is 1 and No is 0)
![Screenshot](./images/image01.png)

Then I used logistic regression with best parameter C=0.01

              precision    recall  f1-score   support

       False       0.90      0.99      0.94      1006
        True       0.61      0.15      0.24       125

    accuracy                           0.90      1131
   macro avg       0.76      0.57      0.59      1131
weighted avg       0.87      0.90      0.87      1131

Elapsed during training: 0.01s
Accuracy score is:  0.90

![Screenshot](./images/image02.png)


Then I used DecisionTreeClassifier with best parameter criterion='gini',max_depth = 20


              precision    recall  f1-score   support

          No       1.00      1.00      1.00      1006
         Yes       1.00      0.98      0.99       125

    accuracy                           1.00      1131
   macro avg       1.00      0.99      0.99      1131
weighted avg       1.00      1.00      1.00      1131

Elapsed during training: 0.02s
Accuracy score: 0.9973s

![Screenshot](./images/image03.png)


Then I used K-NeighborsClassifierssifier with best parameter n_neighbors=13


              precision    recall  f1-score   support

          No       0.90      0.98      0.94      1006
         Yes       0.43      0.14      0.22       125

    accuracy                           0.88      1131
   macro avg       0.67      0.56      0.58      1131
weighted avg       0.85      0.88      0.86      1131

Elapsed during training: 0.01s
Accuracy score: 0.8842s

![Screenshot](./images/image04.png)


Then I used supported vectors with best parameter kernel='rbf'


          No       0.89      1.00      0.94      1006
         Yes       0.00      0.00      0.00       125

    accuracy                           0.89      1131
   macro avg       0.44      0.50      0.47      1131
weighted avg       0.79      0.89      0.84      1131

Elapsed during training: 0.17s
Accuracy score: 0.8886s

![Screenshot](./images/image05.png)



# Conclusions 
The classification goal is to predict if the client will subscribe (yes/no) a term deposit (variable y). 
Decision tree classifier is found to provide the best accuracy of 0.99 with depth of 13.