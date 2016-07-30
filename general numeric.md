
X_train<-X_train[,":="(Hospital_ID =as.numeric(as.factor(Hospital_ID)),
                     District_ID= as.numeric(as.factor(District_ID)),
                     Instrument_ID=as.numeric(as.factor( Instrument_ID)),
                     Revenue = as.numeric(as.factor(Revenue)),
                     Buy_or_not=as.numeric(as.factor(Buy_or_not)),
                     YearEndTotal=NULL,
                     Annual_Projected_Revenue =NULL
)]


Classes ‘data.table’ and 'data.frame':	8231 obs. of  5 variables:
 $ Hospital_ID  : num  1 1 1 1 1 1 1 1 1 1 ...
 $ District_ID  : num  4 4 4 11 12 12 12 12 33 33 ...
 $ Instrument_ID: num  5 6 7 5 5 6 9 10 5 6 ...
 $ Revenue      : num  1302 7675 7530 5187 6310 ...
 $ Buy_or_not   : num  0 1 1 1 1 0 0 1 0 0 ...
 - attr(*, ".internal.selfref")=<externalptr> 
> head(X_train)
   Hospital_ID District_ID Instrument_ID Revenue Buy_or_not
1:           1           4             5    1302          0
2:           1           4             6    7675          2
3:           1           4             7    7530          2
4:           1          11             5    5187          2
5:           1          12             5    6310          2
6:           1          12             6     601          0

see buy_or_not is changed to 2:

Solution:
=========
dont change existic numeric to factor ,since apply factor() to numeric  will re-factor to again and
change 0-1 and 1-2 
X_train<-X_train[,":="(Hospital_ID =as.numeric(as.factor(Hospital_ID)),
                     District_ID= as.numeric(as.factor(District_ID)),
                     Instrument_ID=as.numeric(as.factor( Instrument_ID)),
                     Revenue = as.numeric(Revenue),
                     Buy_or_not=as.numeric(Buy_or_not),
                     YearEndTotal=NULL,
                     Annual_Projected_Revenue =NULL
)]

Revenue = as.numeric(Revenue),
Buy_or_not=as.numeric(Buy_or_not),
