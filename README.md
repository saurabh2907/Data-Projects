Industry CAGR New =
    VAR _FY =
        IF(NOT ISFILTERED(DimDate_CAGR[Date])&&SELECTEDVALUE(CAGR_Metric[CAGR_Cond])="Full FY",
        "FY-"&RIGHT(YEAR(EOMONTH(MAX(DimDate_CAGR[Date]),0))-1,2),MAX(DimDate_CAGR[FY Year C]))
    VAR _FY_Last =
        IF(NOT ISFILTERED(DimDate_CAGR[Date])&&SELECTEDVALUE(CAGR_Metric[CAGR_Cond])="Full FY","FY-"&RIGHT(YEAR(EOMONTH(MAX(DimDate_CAGR[Date]),(-[Count_Slicer]*12)+1)),2),"FY-"&RIGHT(YEAR(EOMONTH(MAX(DimDate_CAGR[Date]),(-[Count_Slicer]*12)+1))+1,2))
    VAR _Current = CALCULATE(SUM('CAGR Data1'[Value_C]),
                   FILTER(DimDate_CAGR,DimDate_CAGR[FY Year C]=_FY))
    VAR _Last = CALCULATE(SUM('CAGR Data1'[Value_C]),
                FILTER(DimDate_CAGR,DimDate_CAGR[FY Year C]=_FY_Last))
    VAR _Current_TM = CALCULATE(SUM('CAGR Data1'[Value_Till_Month]),
                      FILTER(DimDate_CAGR,DimDate_CAGR[FY Year C]=_FY))
    VAR _Last_TM = CALCULATE(SUM('CAGR Data1'[Value_Till_Month]),
                   FILTER(DimDate_CAGR,DimDate_CAGR[FY Year C]=_FY_Last))
    VAR Result = IF(SELECTEDVALUE(CAGR_Metric[CAGR_Cond])="Full FY",
    DIVIDE(_Current,_Last)^DIVIDE(1,[Count_Slicer]-1)-1,
    DIVIDE(_Current_TM,_Last_TM)^DIVIDE(1,[Count_Slicer]-1)-1)
 
    Return
    Result
