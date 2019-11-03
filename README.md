# Titanic Competition Kaggle
## Abstract

### What is that we're trying to solve?

The sinking of the Titanic is one of the most infamous shipwrecks in history. On April 15, 1912, during her maiden voyage, the Titanic sank after colliding with an iceberg, killing 1502 out of 2224 passengers and crew. 

One of the reasons that the shipwreck led to such loss of life was that there were not enough lifeboats for the passengers and crew. Although there was some element of luck involved in surviving the sinking, _some groups of people were more likely to survive than others, such as women, children, and the upper-class._

In this task, we complete the analysis of what sorts of people were likely to survive by applying the tools of machine learning to predict which passengers survived the tragedy.

### How did we approach the problem? 

There were the main stages in how we solved this problem:

1. Data Summarization. 
2. Data Preprocessing.
3. Feature Engineering.
4. Try out algorithms that we felt would be a good fit to this problem. 
5. Compare and try to improve accuracies by repeating Step 3 and Step 4 to find the model with the best accuracy.

Based on our analysis, the best accuracy was achieved by using the Random Forest Classifier.

### Data Summary and EDA:

##### Intro:

We performed extensive data analysis to get a better idea about the data. We looked at the summaries of the data at various levels like - Class level, Sex level, Class-Sex level, and the NamePrefix (which is a derived variable from the Name) level. 

Some of the observations that we saw are:

1. Survival in the female is higher than male.
2. Survival rate for class1 is higher than survival rate in class2 which in turn is higher than the survival rate in class3.
3. We also notice that in general the age of people in class1 is greater than the age of people in class2 which is greater than the age of people in class3.

We also looked at interaction of variables for survivals and non-survivals and made some interesting plots in R.

[![text](https://raw.githubusercontent.com/anicksaha/blob/master/stat5302/Titanic_Charts.png)](https://github.com/anicksaha/blob/blob/master/stat5302/Titanic_Charts.png)

##### What preprocessing did we do?

1. We checked for NULL values in each column and noticed that there are a number of null values Cabin, Age and Fare.
2. In order to imute the null vaules in Fare, we use linear interpolation since the number of null vaules is very small.
3. For imputing age, we took the mean of the age column. 
4. Due to the large number of null values in the cabin column, we decide to drop it.
5 We also drop the ticket column because it does not seem to have any relation with survival

##### What sort of Feaure Engineering were done?
1. We created the feature FamilySize to denote the number of people travelling together by adding SibSp and Parch.
2. The feature IsAlone was created to denote if a passenger is travelling alone or not
3. The feature Title is extracted from the Name attribute and the rare titles were mapped to more general ones. After this, the name column is dropped.
4. For the remaining feateures we performed label encoding for the categoriacal variables

### Different models that were tried:
We tried the following models with the same proprocessed data:
1. Logistic regression
2. SVM
3. AdaBoost Classifier
4. XGBoost Classifier
5. ExtraTrees Classifier
6. GradientBoosting Classifier
7. GaussianNB Classifier
8. Random Forest Classifer

##### How did each model fair?
* For each of the models, we calculated the accuracy in terms of the training dataset. 
* Amongst all the models, RandomForest classifier and ExtraTrees classifier gave the greterst accuracy valus. 
* Of these two, the Random Forest Classifier performed better on the Test dataset (Kaggle submission score) and hence generalized better!

### The model that won out heart - Random Forest!

Random Forest is a supervised learning algorithm. The forest it builds, is an ensemble of Decision Trees, most of the time trained with the “bagging” method. 

To say it in simple words: Random forest builds multiple decision trees and merges the rules together to get a more accurate Decision Tree. 

One of the big problems in machine learning is overfitting, but most of the time this won’t happen that easy to a random forest classifier. That’s because if there are enough trees in the forest, the classifier won’t overfit the model. The complex models we used like SVM don't work well with this data because of the low number of training samples available while a random forest being a very simple yet powerful model did a better job and turned out to be a better fit for the low number of traning samples.

### Conclusion:

Future work: 

* We can try different __imputation methods__ like - Groupwise means, medians, etc.
* We can try __ensembling different models__ and make a more robust model that generalizes better.
*  We can try to think of a way to use 'ticket_number' and other dropped columns. 

