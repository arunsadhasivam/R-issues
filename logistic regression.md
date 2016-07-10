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

IF I try all you can see LoanID showing all values since it excepts factor values only in prediction.
Call:  glm(formula = Loan_Status ~ ., family = binomial, data = train, 
    maxit = 100)

Coefficients:
           (Intercept)         Loan_IDLP001003         Loan_IDLP001005         Loan_IDLP001006         Loan_IDLP001008  
            -2.857e+01               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001011         Loan_IDLP001013         Loan_IDLP001014         Loan_IDLP001018         Loan_IDLP001020  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001024         Loan_IDLP001027         Loan_IDLP001028         Loan_IDLP001029         Loan_IDLP001030  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001032         Loan_IDLP001034         Loan_IDLP001036         Loan_IDLP001038         Loan_IDLP001041  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001043         Loan_IDLP001046         Loan_IDLP001047         Loan_IDLP001050         Loan_IDLP001052  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001066         Loan_IDLP001068         Loan_IDLP001073         Loan_IDLP001086         Loan_IDLP001087  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001091         Loan_IDLP001095         Loan_IDLP001097         Loan_IDLP001098         Loan_IDLP001100  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001106         Loan_IDLP001109         Loan_IDLP001112         Loan_IDLP001114         Loan_IDLP001116  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001119         Loan_IDLP001120         Loan_IDLP001123         Loan_IDLP001131         Loan_IDLP001136  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001137         Loan_IDLP001138         Loan_IDLP001144         Loan_IDLP001146         Loan_IDLP001151  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001155         Loan_IDLP001157         Loan_IDLP001164         Loan_IDLP001179         Loan_IDLP001186  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001194         Loan_IDLP001195         Loan_IDLP001197         Loan_IDLP001198         Loan_IDLP001199  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001205         Loan_IDLP001206         Loan_IDLP001207         Loan_IDLP001213         Loan_IDLP001222  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001225         Loan_IDLP001228         Loan_IDLP001233         Loan_IDLP001238         Loan_IDLP001241  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001243         Loan_IDLP001245         Loan_IDLP001248         Loan_IDLP001250         Loan_IDLP001253  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001255         Loan_IDLP001256         Loan_IDLP001259         Loan_IDLP001263         Loan_IDLP001264  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001265         Loan_IDLP001266         Loan_IDLP001267         Loan_IDLP001273         Loan_IDLP001275  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001279         Loan_IDLP001280         Loan_IDLP001282         Loan_IDLP001289         Loan_IDLP001310  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001316         Loan_IDLP001318         Loan_IDLP001319         Loan_IDLP001322         Loan_IDLP001325  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001326         Loan_IDLP001327         Loan_IDLP001333         Loan_IDLP001334         Loan_IDLP001343  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001345         Loan_IDLP001349         Loan_IDLP001350         Loan_IDLP001356         Loan_IDLP001357  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001367         Loan_IDLP001369         Loan_IDLP001370         Loan_IDLP001379         Loan_IDLP001384  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001385         Loan_IDLP001387         Loan_IDLP001391         Loan_IDLP001392         Loan_IDLP001398  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001401         Loan_IDLP001404         Loan_IDLP001405         Loan_IDLP001421         Loan_IDLP001422  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001426         Loan_IDLP001430         Loan_IDLP001431         Loan_IDLP001432         Loan_IDLP001439  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001443         Loan_IDLP001448         Loan_IDLP001449         Loan_IDLP001451         Loan_IDLP001465  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001469         Loan_IDLP001473         Loan_IDLP001478         Loan_IDLP001482         Loan_IDLP001487  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001488         Loan_IDLP001489         Loan_IDLP001491         Loan_IDLP001492         Loan_IDLP001493  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001497         Loan_IDLP001498         Loan_IDLP001504         Loan_IDLP001507         Loan_IDLP001508  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001514         Loan_IDLP001516         Loan_IDLP001518         Loan_IDLP001519         Loan_IDLP001520  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001528         Loan_IDLP001529         Loan_IDLP001531         Loan_IDLP001532         Loan_IDLP001535  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001536         Loan_IDLP001541         Loan_IDLP001543         Loan_IDLP001546         Loan_IDLP001552  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001560         Loan_IDLP001562         Loan_IDLP001565         Loan_IDLP001570         Loan_IDLP001572  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001574         Loan_IDLP001577         Loan_IDLP001578         Loan_IDLP001579         Loan_IDLP001580  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001581         Loan_IDLP001585         Loan_IDLP001586         Loan_IDLP001594         Loan_IDLP001603  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001606         Loan_IDLP001608         Loan_IDLP001610         Loan_IDLP001616         Loan_IDLP001630  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001633         Loan_IDLP001634         Loan_IDLP001636         Loan_IDLP001637         Loan_IDLP001639  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001640         Loan_IDLP001641         Loan_IDLP001643         Loan_IDLP001644         Loan_IDLP001647  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001653         Loan_IDLP001656         Loan_IDLP001657         Loan_IDLP001658         Loan_IDLP001664  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001665         Loan_IDLP001666         Loan_IDLP001669         Loan_IDLP001671         Loan_IDLP001673  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001674         Loan_IDLP001677         Loan_IDLP001682         Loan_IDLP001688         Loan_IDLP001691  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001692         Loan_IDLP001693         Loan_IDLP001698         Loan_IDLP001699         Loan_IDLP001702  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001708         Loan_IDLP001711         Loan_IDLP001713         Loan_IDLP001715         Loan_IDLP001716  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001720         Loan_IDLP001722         Loan_IDLP001726         Loan_IDLP001732         Loan_IDLP001734  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001736         Loan_IDLP001743         Loan_IDLP001744         Loan_IDLP001749         Loan_IDLP001750  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001751         Loan_IDLP001754         Loan_IDLP001758         Loan_IDLP001760         Loan_IDLP001761  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001765         Loan_IDLP001768         Loan_IDLP001770         Loan_IDLP001776         Loan_IDLP001778  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001784         Loan_IDLP001786         Loan_IDLP001788         Loan_IDLP001790         Loan_IDLP001792  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001798         Loan_IDLP001800         Loan_IDLP001806         Loan_IDLP001807         Loan_IDLP001811  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001813         Loan_IDLP001814         Loan_IDLP001819         Loan_IDLP001824         Loan_IDLP001825  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001835         Loan_IDLP001836         Loan_IDLP001841         Loan_IDLP001843         Loan_IDLP001844  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001846         Loan_IDLP001849         Loan_IDLP001854         Loan_IDLP001859         Loan_IDLP001864  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001865         Loan_IDLP001868         Loan_IDLP001870         Loan_IDLP001871         Loan_IDLP001872  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001875         Loan_IDLP001877         Loan_IDLP001882         Loan_IDLP001883         Loan_IDLP001884  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001888         Loan_IDLP001891         Loan_IDLP001892         Loan_IDLP001894         Loan_IDLP001896  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001900         Loan_IDLP001903         Loan_IDLP001904         Loan_IDLP001907         Loan_IDLP001908  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001910         Loan_IDLP001914         Loan_IDLP001915         Loan_IDLP001917         Loan_IDLP001922  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001924         Loan_IDLP001925         Loan_IDLP001926         Loan_IDLP001931         Loan_IDLP001935  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001936         Loan_IDLP001938         Loan_IDLP001940         Loan_IDLP001945         Loan_IDLP001947  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001949         Loan_IDLP001953         Loan_IDLP001954         Loan_IDLP001955         Loan_IDLP001963  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001964         Loan_IDLP001972         Loan_IDLP001974         Loan_IDLP001977         Loan_IDLP001978  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP001990         Loan_IDLP001993         Loan_IDLP001994         Loan_IDLP001996         Loan_IDLP001998  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002002         Loan_IDLP002004         Loan_IDLP002006         Loan_IDLP002008         Loan_IDLP002024  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002031         Loan_IDLP002035         Loan_IDLP002036         Loan_IDLP002043         Loan_IDLP002050  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002051         Loan_IDLP002053         Loan_IDLP002054         Loan_IDLP002055         Loan_IDLP002065  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002067         Loan_IDLP002068         Loan_IDLP002082         Loan_IDLP002086         Loan_IDLP002087  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002097         Loan_IDLP002098         Loan_IDLP002100         Loan_IDLP002101         Loan_IDLP002103  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002106         Loan_IDLP002110         Loan_IDLP002112         Loan_IDLP002113         Loan_IDLP002114  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002115         Loan_IDLP002116         Loan_IDLP002119         Loan_IDLP002126         Loan_IDLP002128  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002129         Loan_IDLP002130         Loan_IDLP002131         Loan_IDLP002137         Loan_IDLP002138  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002139         Loan_IDLP002140         Loan_IDLP002141         Loan_IDLP002142         Loan_IDLP002143  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002144         Loan_IDLP002149         Loan_IDLP002151         Loan_IDLP002158         Loan_IDLP002160  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002161         Loan_IDLP002170         Loan_IDLP002175         Loan_IDLP002178         Loan_IDLP002180  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002181         Loan_IDLP002187         Loan_IDLP002188         Loan_IDLP002190         Loan_IDLP002191  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002194         Loan_IDLP002197         Loan_IDLP002201         Loan_IDLP002205         Loan_IDLP002209  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002211         Loan_IDLP002219         Loan_IDLP002223         Loan_IDLP002224         Loan_IDLP002225  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002226         Loan_IDLP002229         Loan_IDLP002231         Loan_IDLP002234         Loan_IDLP002236  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002237         Loan_IDLP002239         Loan_IDLP002243         Loan_IDLP002244         Loan_IDLP002250  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002255         Loan_IDLP002262         Loan_IDLP002263         Loan_IDLP002265         Loan_IDLP002266  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002272         Loan_IDLP002277         Loan_IDLP002281         Loan_IDLP002284         Loan_IDLP002287  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002288         Loan_IDLP002296         Loan_IDLP002297         Loan_IDLP002300         Loan_IDLP002301  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002305         Loan_IDLP002308         Loan_IDLP002314         Loan_IDLP002315         Loan_IDLP002317  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002318         Loan_IDLP002319         Loan_IDLP002328         Loan_IDLP002332         Loan_IDLP002335  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002337         Loan_IDLP002341         Loan_IDLP002342         Loan_IDLP002345         Loan_IDLP002347  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002348         Loan_IDLP002357         Loan_IDLP002361         Loan_IDLP002362         Loan_IDLP002364  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002366         Loan_IDLP002367         Loan_IDLP002368         Loan_IDLP002369         Loan_IDLP002370  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002377         Loan_IDLP002379         Loan_IDLP002386         Loan_IDLP002387         Loan_IDLP002390  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002393         Loan_IDLP002398         Loan_IDLP002401         Loan_IDLP002403         Loan_IDLP002407  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002408         Loan_IDLP002409         Loan_IDLP002418         Loan_IDLP002422         Loan_IDLP002424  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002429         Loan_IDLP002434         Loan_IDLP002435         Loan_IDLP002443         Loan_IDLP002444  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002446         Loan_IDLP002447         Loan_IDLP002448         Loan_IDLP002449         Loan_IDLP002453  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002455         Loan_IDLP002459         Loan_IDLP002467         Loan_IDLP002472         Loan_IDLP002473  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002478         Loan_IDLP002484         Loan_IDLP002487         Loan_IDLP002489         Loan_IDLP002493  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002494         Loan_IDLP002500         Loan_IDLP002501         Loan_IDLP002502         Loan_IDLP002505  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002515         Loan_IDLP002517         Loan_IDLP002519         Loan_IDLP002522         Loan_IDLP002524  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002527         Loan_IDLP002529         Loan_IDLP002530         Loan_IDLP002531         Loan_IDLP002533  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002534         Loan_IDLP002536         Loan_IDLP002537         Loan_IDLP002541         Loan_IDLP002543  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002544         Loan_IDLP002545         Loan_IDLP002547         Loan_IDLP002555         Loan_IDLP002556  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002560         Loan_IDLP002562         Loan_IDLP002571         Loan_IDLP002582         Loan_IDLP002585  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002586         Loan_IDLP002587         Loan_IDLP002588         Loan_IDLP002600         Loan_IDLP002602  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002603         Loan_IDLP002606         Loan_IDLP002615         Loan_IDLP002618         Loan_IDLP002619  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002622         Loan_IDLP002624         Loan_IDLP002625         Loan_IDLP002626         Loan_IDLP002634  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002637         Loan_IDLP002640         Loan_IDLP002643         Loan_IDLP002648         Loan_IDLP002652  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002659         Loan_IDLP002670         Loan_IDLP002682         Loan_IDLP002683         Loan_IDLP002684  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002689         Loan_IDLP002690         Loan_IDLP002692         Loan_IDLP002693         Loan_IDLP002697  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002699         Loan_IDLP002705         Loan_IDLP002706         Loan_IDLP002714         Loan_IDLP002716  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002717         Loan_IDLP002720         Loan_IDLP002723         Loan_IDLP002729         Loan_IDLP002731  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002732         Loan_IDLP002734         Loan_IDLP002738         Loan_IDLP002739         Loan_IDLP002740  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002741         Loan_IDLP002743         Loan_IDLP002753         Loan_IDLP002755         Loan_IDLP002757  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002767         Loan_IDLP002768         Loan_IDLP002772         Loan_IDLP002776         Loan_IDLP002777  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002778         Loan_IDLP002784         Loan_IDLP002785         Loan_IDLP002788         Loan_IDLP002789  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002792         Loan_IDLP002794         Loan_IDLP002795         Loan_IDLP002798         Loan_IDLP002804  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002807         Loan_IDLP002813         Loan_IDLP002820         Loan_IDLP002821         Loan_IDLP002832  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002833         Loan_IDLP002836         Loan_IDLP002837         Loan_IDLP002840         Loan_IDLP002841  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002842         Loan_IDLP002847         Loan_IDLP002855         Loan_IDLP002862         Loan_IDLP002863  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002868         Loan_IDLP002872         Loan_IDLP002874         Loan_IDLP002877         Loan_IDLP002888  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002892         Loan_IDLP002893         Loan_IDLP002894         Loan_IDLP002898         Loan_IDLP002911  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002912         Loan_IDLP002916         Loan_IDLP002917         Loan_IDLP002925         Loan_IDLP002926  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002928         Loan_IDLP002931         Loan_IDLP002933         Loan_IDLP002936         Loan_IDLP002938  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002940         Loan_IDLP002941         Loan_IDLP002943         Loan_IDLP002945         Loan_IDLP002948  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002949         Loan_IDLP002950         Loan_IDLP002953         Loan_IDLP002958         Loan_IDLP002959  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
       Loan_IDLP002960         Loan_IDLP002961         Loan_IDLP002964         Loan_IDLP002974         Loan_IDLP002978  
             8.127e-12               8.127e-12               8.127e-12               8.127e-12               8.127e-12  
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

