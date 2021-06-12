# Marketing_Campaign_Effectiveness_Prediction
Problem Description The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed. The classification goal is to predict if the client will subscribe a term deposit (variable y).

Data Description

Input variables:

#Bank Client data:

1. age (numeric)
2. job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')

3. marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)

4. education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')

5. default: has credit in default? (categorical: 'no','yes','unknown')

6. housing: has housing loan? (categorical: 'no','yes','unknown')

7. loan: has personal loan? (categorical: 'no','yes','unknown')

8. Related with the last contact of the current campaign:

9. contact: contact communication type (categorical: 'cellular','telephone')

10. month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')

11. day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')

12. duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

Other attributes:
1. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

2. pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)

3. previous: number of contacts performed before this campaign and for this client (numeric)

4. poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')

5. Social and economic context attributes

6. emp.var.rate: employment variation rate - quarterly indicator (numeric)

7. cons.price.idx: consumer price index - monthly indicator (numeric)

8. cons.conf.idx: consumer confidence index - monthly indicator (numeric)

9. euribor3m: euribor 3 month rate - daily indicator (numeric)

10. nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):

y - has the client subscribed a term deposit? (binary: 'yes','no')



#Hypothesis:
1. Most of the people who would deny a Term Deposit would be younger age

2. Blue Collar jobs reject opening a Term Deposit the most where as Students and Old People say yes.

3. Higher education will lead to higher numbers of TD

4. Credit defaulters will never say yes.

5. Loan defaulters will not say yes.

6. Festive seasons will see the most amount of acceptance.

7. People with housing loan will not say yes.

8. Non-cellular contacts will be rejected.

9. Higher balance will say yes.

10. People who have yes to TD before will say yes again.

11. Lower previous days will result in higher TD.

#Feature Engineering- 

1. Age- Converted Age to four bins : struggling, stable, about to retire and counting last breaths
2. Jobs- Made three categories for jobs : category 1- service jobs, category 2- blue collar, category 3- businessmen

One hot encoding-
Performed one hot encoding on the following columns:
1. Marital status
2. Age Category
3. Jobs category 
4. outcome
5. Contacted Before
6. Credit Default
7. Loan Default
8. Education 
9. Housing Loan

#Nan Value Imputation- KNN imputer

#Outlier Removal-Multivariate Isolation Forest 

#Scaling- Scaled column balance by MinmaxScaler

#Feature Selection- ExtraTreesClassifier. Chose the 15 most important features by taking the highest Gini Scores with highest information gain

#Oversampling- Used SMOTE to oversample the minority class by using the method of KNN to place synthetic minority class data in between half the distance of two other minority class data points

#Model Selection-
1. Logistic Regression - This is predictive classification analysis method that is used to determine the relationship of a dichotomous variable and one or more nominal, ordinal, interval or ratio-level independent variables.
2. Decision Tree Classifier- Decision trees are predictive analysis methods that mimic human decision making abilities to predict the class of the given dataset, it comapares the values of the root node with the real dataset and based on comparison, follows the branch and jumps to the next node.
3. XGBoost Classifier- It is an optimized GBM that is designed to be highly efficient and flexible.  XGBoost Decision Trees learn from weak learners and become strong learners with global minima error by leveraging gradient descent. Parallely it utilises regularization to prevent over complication of the model

#Scores- 
F1- Score-- F1 score leverages both Precision and Recall Scores. This is done to prevent misclassification of customers to prevent losing on customers and also to not lose money.
LR Model- 65%
Decision Tree- 70%
XGBoost- 83%

