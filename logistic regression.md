ERROR 1:
========
> logresult <- glm(Loan_Status~. -Loan_ID, data=train, family=binomial)
Warning message:
glm.fit: algorithm did not converge 


Solution:
=========
set maxit =100 to get convergence.
logresult <- glm(Loan_Status~. -Loan_ID, data=train, family=binomial,maxit =100)


ERROR 2:
========
logresult <- glm(Loan_Status~. -Loan_ID, data=train, family=binomial,maxit =100)
> pred=predict(logresult,test)
Error in model.frame.default(Terms, newdata, na.action = na.action, xlev = object$xlevels) : 
  factor Loan_ID has new levels LP001015, LP001022, LP001031, LP001035, LP001051, LP001054, LP001055, LP001056, LP001059, LP001067, LP001078, LP001082, LP001083, LP001094, LP001096, LP001099, LP001105, LP001107, LP001108, LP001115, LP001121, LP001124, LP001128, LP001135, LP001149, LP001153, LP001163, LP001169, LP001174, LP001176, LP001177, LP001183, LP001185, LP001187, LP001190, LP001203, LP001208, LP001210, LP001211, LP001219, LP001220, LP001221, LP001226, LP001230, LP001231, LP001232, LP001237, LP001242, LP001268, LP001270, LP001284, LP001287, LP001291, LP001298, LP001312, LP001313, LP001317, LP001321, LP001323, LP001324, LP001332, LP001335, LP001338, LP001347, LP001348, LP001351, LP001352, LP001358, LP001359, LP001361, LP001366, LP001368, LP001375, LP001380, LP001386, LP001400, LP001407, LP001413, LP001415, LP001419, LP001420, LP001428, LP001445, LP001446, LP001450, LP001452, LP001455, LP001466, LP001471, LP001472, LP001475, LP001483, LP001486, LP001490, LP001496, LP001499, 


Solution:
==========

IF I try with Loan_ID ,you can see result with all Loan_ID(LP001015...)   since it excepts factor values only while  in predict statement.
Call:  glm(formula = Loan_Status ~ ., family = binomial, data = train, 
    maxit = 100)

Coefficients:
           (Intercept)         Loan_IDLP001003         Loan_IDLP001005         Loan_IDLP001006         Loan_IDLP001008  
            -2.857e+01               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001011         Loan_IDLP001013         Loan_IDLP001014         Loan_IDLP001018         Loan_IDLP001020  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       ..............          ...............         ...............        ................          ..............
       Loan_IDLP002979         Loan_IDLP002983         Loan_IDLP002984         Loan_IDLP002990                 Gender2  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12                      NA  
               Gender3                 Married             Dependents2             Dependents3             Dependents4  
                    NA                      NA                      NA                      NA                      NA  
           Dependents5   EducationNot Graduate          Self_Employed2          Self_Employed3         ApplicantIncome  
                    NA                      NA                      NA                      NA                      NA  
     CoapplicantIncome              LoanAmount        Loan_Amount_Term          Credit_History  Property_AreaSemiurban  
                    NA                      NA                      NA                      NA                      NA  
    Property_AreaUrban  
                    NA  




If i try without Loan_ID

Call:
glm(formula = Loan_Status ~ . - Loan_ID, family = binomial, data = train, 
    maxit = 100)

Deviance Residuals: 
       Min          1Q      Median          3Q         Max  
-8.861e-07  -8.861e-07  -8.861e-07  -8.861e-07  -8.861e-07  

Coefficients:
                         Estimate Std. Error z value Pr(>|z|)
(Intercept)            -2.857e+01  5.269e+05       0        1
Gender2                -1.747e-14  2.914e+05       0        1
Gender3                 2.417e-15  2.760e+05       0        1
Married                -2.229e-14  9.266e+04       0        1
Dependents2             1.461e-14  2.605e+05       0        1
Dependents3            -9.830e-15  2.701e+05       0        1
Dependents4            -3.799e-15  2.701e+05       0        1
Dependents5             2.900e-15  2.885e+05       0        1
EducationNot Graduate  -3.685e-15  9.788e+04       0        1
Self_Employed2          1.375e-14  1.782e+05       0        1
Self_Employed3          3.142e-15  2.037e+05       0        1
ApplicantIncome        -5.336e-19  8.267e+00       0        1
CoapplicantIncome      -1.598e-18  1.438e+01       0        1
LoanAmount              2.511e-17  6.108e+02       0        1
Loan_Amount_Term        1.776e-17  6.248e+02       0        1
Credit_History          1.420e-14  1.104e+05       0        1
Property_AreaSemiurban  6.294e-15  9.755e+04       0        1
Property_AreaUrban      2.275e-14  1.010e+05       0        1


SOLUTION 1:
===========

logresult <- glm(Loan_Status~., data=train[,!colnames(train) %in% c("Loan_ID")], family=binomial,maxit =100)

#logresult <- glm(Loan_Status~.-(Loan_ID), data=train, family=binomial)#not working
logresult <- glm(Loan_Status~., data=train[,!colnames(train) %in% c("Loan_ID")], family=binomial,maxit =100)#working.
pred=predict(logresult,test ,type="response")
test$Loan_Status=pred

