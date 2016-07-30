ISSUE:
======

colSums(is.na(X_train))

str(X_train)
head(X_train)
X_train<-X_train[,":="(Hospital_ID =as.numeric(Hospital_ID),
                       District_ID= as.numeric(District_ID),
                       Instrument_ID=as.numeric( Instrument_ID),
                       Revenue = as.numeric(Revenue),
                       Buy_or_not=as.numeric(Buy_or_not),
                       YearEndTotal=NULL,
                       Annual_Projected_Revenue =NULL
)]
OUTPUT:
=======

 colSums(is.na(X_train))
             Hospital_ID              District_ID            Instrument_ID             YearEndTotal Annual_Projected_Revenue 
                       0                        0                        0                        0                        0 
                 Revenue               Buy_or_not 
                       0                        0 
> X_train<-X_train[,":="(Hospital_ID =as.numeric(Hospital_ID),
+                        District_ID= as.numeric(District_ID),
+                        Instrument_ID=as.numeric( Instrument_ID),
+                        Revenue = as.numeric(Revenue),
+                        Buy_or_not=as.numeric(Buy_or_not),
+                        YearEndTotal=NULL,
+                        Annual_Projected_Revenue =NULL
+ )]
Warning messages:
1: In eval(expr, envir, enclos) : NAs introduced by coercion
2: In eval(expr, envir, enclos) : NAs introduced by coercion
3: In eval(expr, envir, enclos) : NAs introduced by coercion

see above output eventhough all columns have no NA columns but apply numeric to char vector is
not allowed since some char vector may be say id so apply factor and then apply numeric as below.

SOlution:
=========
issue occur when converting to char vector to numeric vector. since 
all character vector cannot be given diff number dummy variable hence apply factor
and then apply numeric above issue will gets corrected.
see below now it is working 

colSums(is.na(X_train))
str(X_train)
head(X_train)
X_train<-X_train[,":="(Hospital_ID =as.numeric(as.factor(Hospital_ID)),
                       District_ID= as.numeric(as.factor(District_ID)),
                       Instrument_ID=as.numeric(as.factor( Instrument_ID)),
                       Revenue = as.numeric(Revenue),
                       Buy_or_not=as.numeric(Buy_or_not),
                       YearEndTotal=NULL,
                       Annual_Projected_Revenue =NULL
)]
str(X_train)

