


ERROR:
=======
X_train<-X_train[,":="(Hospital_ID = as.factor(as.numeric(as.factor(Hospital_ID))),
                       District_ID= as.factor(as.numeric(as.factor(District_ID))),
                       Instrument_ID=as.factor(as.numeric(as.factor( Instrument_ID))),
                       Revenue = as.numeric(Revenue),
                       Buy_or_not=as.numeric(Buy_or_not),
                       YearEndTotal=NULL,
                       Annual_Projected_Revenue =NULL
)]
str(X_train)
X_revenue<-X_train[,-4]
str(X_train)
str(X_revenue)


OUTPUT:
=======

> str(X_train)
Classes ‘data.table’ and 'data.frame':	8231 obs. of  5 variables:
 $ Hospital_ID  : Factor w/ 1580 levels "1","2","3","4",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ District_ID  : Factor w/ 53 levels "1","2","3","4",..: 4 4 4 11 12 12 12 12 33 33 ...
 $ Instrument_ID: Factor w/ 15 levels "1","2","3","4",..: 5 6 7 5 5 6 9 10 5 6 ...
 $ Revenue      : num  -23577 647096 280031 10335 35171 ...
 $ Buy_or_not   : num  0 1 1 1 1 0 0 1 0 0 ...
 - attr(*, ".internal.selfref")=<externalptr> 
> X_revenue<-X_train[ ,Revenue:=NULL]
> str(X_train)
Classes ‘data.table’ and 'data.frame':	8231 obs. of  4 variables:
 $ Hospital_ID  : Factor w/ 1580 levels "1","2","3","4",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ District_ID  : Factor w/ 53 levels "1","2","3","4",..: 4 4 4 11 12 12 12 12 33 33 ...
 $ Instrument_ID: Factor w/ 15 levels "1","2","3","4",..: 5 6 7 5 5 6 9 10 5 6 ...
 $ Buy_or_not   : num  0 1 1 1 1 0 0 1 0 0 ...
 - attr(*, ".internal.selfref")=<externalptr> 
> str(X_revenue)
Classes ‘data.table’ and 'data.frame':	8231 obs. of  4 variables:
 $ Hospital_ID  : Factor w/ 1580 levels "1","2","3","4",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ District_ID  : Factor w/ 53 levels "1","2","3","4",..: 4 4 4 11 12 12 12 12 33 33 ...
 $ Instrument_ID: Factor w/ 15 levels "1","2","3","4",..: 5 6 7 5 5 6 9 10 5 6 ...
 $ Buy_or_not   : num  0 1 1 1 1 0 0 1 0 0 ...
 - attr(*, ".internal.selfref")=<externalptr> 

see removing X_train and assign to X_revenue removes X_train also.

when need X-train to predict buy_or_not and Revenue . so need of removing buy_or_not when predicting buy_or_not
and removing revenue when predicting revenue.
X_revenue<-X_train[ ,Revenue:=NULL] not working
remove values in X_train also like object reference.

Solutions:
==========

str(X_train)
str(X_test)
conver to data.frame and then remove and convert back to data.table.
X_revenue<-data.frame(X_train)
X_revenue<-X_revenue[,-4]
#X_revenue<-X_train[ ,Revenue:=NULL] not working
X_revenue<-data.table(X_revenue)
str(X_revenue)
