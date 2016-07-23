

Can not handle categorical predictors with more than 53 categories.
==================================================================
Error in randomForest.default(m, y, ...) : 
  Can not handle categorical predictors with more than 53 categories.


solutions:
==========
1) check str(train)

'data.frame':	614 obs. of  20 variables:
 $ Loan_Status          : Factor w/ 2 levels "N","Y": 2 1 2 2 2 2 2 1 2 1 ...
 $ Loan_ID              : Factor w/ 981 levels "LP001015","LP001022",..: 368 369 370 371 372 373 374 375 376 377 ...
 $ Gender               : Factor w/ 3 levels "1","2","3": 3 3 3 3 3 3 3 3 3 3 ...
 $ Married              : int  1 2 2 2 1 2 2 2 2 2 ...
 $ Dependents           : Factor w/ 5 levels "1","2","3","4",..: 2 3 2 2 2 4 2 5 4 3 ...
 $ Education            : Factor w/ 2 levels "Graduate","Not Graduate": 1 1 1 2 1 1 2 1 1 1 ...
 $ Self_Employed        : Factor w/ 3 levels "1","2","3": 2 2 3 2 2 3 2 2 2 2 ...
 $ ApplicantIncome      : int  5849 4583 3000 2583 6000 5417 2333 3036 4006 12841 ...
 $ CoapplicantIncome    : num  0 1508 0 2358 0 ...
 $ LoanAmount           : num  136 128 66 120 141 267 95 158 168 349 ...
 $ Loan_Amount_Term     : num  360 360 360 360 360 360 360 360 360 360 ...
 $ Credit_History       : num  1 1 1 1 1 1 1 0 1 1 ...
 $ Property_Area        : Factor w/ 3 levels "Rural","Semiurban",..: 3 1 3 3 3 3 3 2 3 2 ...
 $ Gender_imp           : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
 $ Self_Employed_imp    : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
 $ Married_imp          : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
 $ Credit_History_imp   : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
 $ Loan_Amount_Term_imp : logi  FALSE FALSE FALSE FALSE FALSE FALSE ...
 $ LoanAmount_imp       : logi  TRUE FALSE FALSE FALSE FALSE FALSE ...
 $ CoapplicantIncome_imp: logi  FALSE FALSE FALSE FALSE FALSE FALSE ...

As you can see Loan_id become factor which is like unique a primary key column so change to integer 
with below fixed my issue. !!!!
train$Loan_ID= as.character(train$Loan_ID)
test$Loan_ID= as.character(test$Loan_ID)


2.ERROR   unused argument (Loan_Status:Property_Area)
=====================================================

This error occurs when using dplyr

Solution:
============
To check this error check ?select or help(select) which are the packages loaded 
As you can see from below output it try to use MASS and dplyr package and hence result
in collision of method in both package.

SO solution restart the session R and then remove MASS if not needed or use package specific
call like test<-dplyr::select(test,Loan_Status:Property_Area)


output
======
Help on topic 'select' was found in the following packages:

Ridge Regression
(in package MASS in library C:/Program Files/R/R-3.2.3/library)
Select/rename variables by name.
(in package dplyr in library C:/Users/admin/Documents/R/win-library/3.2)



ERROR 3: KNN Imputation
=======================
Warning messages:
1: In kNN_work(data, variable, metric, k, dist_var, weights, numFun,  :
  Nothing to impute, because no NA are present (also after using makeNA)
2: In kNN_work(data, variable, metric, k, dist_var, weights, numFun,  :
  The following TRUE/FALSE imputation status variables will be updated: Gender_imp , Self_Employed_imp , Married_imp , Credit_History_imp , Loan_Amount_Term_imp , LoanAmount_imp , CoapplicantIncome_imp

solution:
=========
this occurs if you run r 2 times since if it is null value already computed , if you run again
shows above error. so restart R and try.


ERROR :NA/NAN/INF -NAs introduced by coercion:
=============================================
Error in randomForest.default(m, y, ...) : 
  NA/NaN/Inf in foreign function call (arg 1)

Solutions:
==========

Reason random forest needs 

In general,there are 2 main reasons you get this error message:

1.If the data frame contains a character vector column instead of factors. Just convert your character column to a factor
2.If the data contains bad values, applying random forest will also generate this error.

In my class Loan_id cannot be changed to factor since it is unique - if in case changed "Can not handle categorical predictors with more than 53 categories will be shown" hence removed Loan_id from the formula fixed !!! 

str(train)
str(test)
set.seed(615)
train$Loan_ID= as.character(train$Loan_ID)
test$Loan_ID= as.character(test$Loan_ID)
formula<-Loan_Status ~ Gender+Married+Dependents+Education+ 
  Self_Employed+ApplicantIncome +CoapplicantIncome+LoanAmount+
  Loan_Amount_Term+Credit_History+Property_Area
fit <- randomForest(as.factor(Loan_Status) ~ . -(Loan_ID), data=train,importance=TRUE, ntree=500)

print(fit)
pred=predict(fit,test)
test$Loan_Status=pred

ERROR - Type of predictors in new data do not match that of the training data.
===============================================================================
Error in predict.randomForest(fit, test1) : 
  New factor levels not present in the training data
  Type of predictors in new data do not match that of the training data.
  Reason is if the factor in train does not match test issue occurs as in my case you can see 
  Manager_Joining_Designation- 9 in train vs 7 in test
  Applicant_Qualification -12 vs 9
  
   str(train)
   ===========
'data.frame':	9527 obs. of  23 variables:
 $ Applicant_Gender           : Factor w/ 3 levels "","F","M": 3 3 3 3 3 3 3 3 3 3 ...
 $ Applicant_Marital_Status   : Factor w/ 5 levels "","D","M","S",..: 3 4 3 4 3 4 3 3 3 3 ...
 $ Applicant_Occupation       : Factor w/ 6 levels "","Business",..: 3 3 2 4 3 3 2 4 2 3 ...
 $ Applicant_Qualification    : Factor w/ 12 levels "","Associate / Fellow of Institute of Chartered Accountans of India",..: 9 8 8 8 8 8 8 8 9 8 ...
 $ Manager_Joining_Designation: Factor w/ 9 levels "","Level 1","Level 2",..: 2 2 2 2 2 2 2 2 2 2 ...
 $ Manager_Current_Designation: Factor w/ 6 levels "","Level 1","Level 2",..: 3 3 2 4 2 2 2 2 3 4 ...
 $ Manager_Status             : Factor w/ 3 levels "","Confirmation",..: 2 2 2 2 2 2 2 2 2 2 ...
 $ Manager_Gender             : Factor w/ 3 levels "","F","M": 3 3 3 2 3 3 3 3 3 3 ...
 
 
 
 
 $ Business_Sourced           : Factor w/ 2 levels "0","1": 1 2 1 1 1 2 2 1 2 2 ...
> str(test)
===========
'data.frame':	5045 obs. of  23 variables:
 $ Business_Sourced           : Factor w/ 1 level "0": 1 1 1 1 1 1 1 1 1 1 ...
 $ Applicant_Gender           : Factor w/ 3 levels "","F","M": 3 3 3 3 3 3 3 3 3 3 ...
 $ Applicant_Marital_Status   : Factor w/ 5 levels "","D","M","S",..: 4 3 4 4 4 4 3 4 3 4 ...
 $ Applicant_Occupation       : Factor w/ 6 levels "","Business",..: 4 4 1 4 1 1 1 4 3 1 ...
 $ Applicant_Qualification    : Factor w/ 9 levels "","Associate / Fellow of Institute of Chartered Accountans of India",..: 6 6 6 6 7 5 6 5 6 6 ...
 $ Manager_Joining_Designation: Factor w/ 7 levels "","Level 1","Level 2",..: 2 2 1 1 3 3 3 3 3 4 ...
 $ Manager_Current_Designation: Factor w/ 6 levels "","Level 1","Level 2",..: 2 2 1 1 3 3 3 3 3 4 ...
 $ Manager_Status             : Factor w/ 3 levels "","Confirmation",..: 3 3 1 1 2 3 2 3 3 3 ...
 $ Manager_Gender             : Factor w/ 3 levels "","F","M": 2 3 1 1 3 3 3 3 3 3 ...


  
  Solution:
  =========
  changed all factor in test matching to train
levels(test$Applicant_Gender) <- levels(train$Applicant_Gender)
levels(test$Applicant_Marital_Status) <- levels(train$Applicant_Marital_Status)
levels(test$Applicant_Occupation) <- levels(train$Applicant_Occupation)
levels(test$Manager_Joining_Designation) <- levels(train$Manager_Joining_Designation)
levels(test$Manager_Current_Designation) <- levels(train$Manager_Current_Designation)


worked!!!
