ERROR 1:
========
> logresult <- glm(Loan_Status~. -Loan_ID, data=train, family=binomial)
Warning message:
glm.fit: algorithm did not converge 


Solution:
=========
set maxit =100 to get convergence.
logresult <- glm(Loan_Status~. -Loan_ID, data=train, family=binomial,maxit =100)
