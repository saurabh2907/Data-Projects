Industry CAGR New = 
VAR _Month = YEAR(MAX(DimDate_CAGR[Date])) * 12 + MONTH(MAX(DimDate_CAGR[Date]))
VAR _Month_Last = _Month - [Count_Slicer]
VAR _Current = CALCULATE(SUM('CAGR Data1'[Value_C]), FILTER(DimDate_CAGR, YEAR(DimDate_CAGR[Date]) * 12 + MONTH(DimDate_CAGR[Date]) = _Month))
VAR _Last = CALCULATE(SUM('CAGR Data1'[Value_C]), FILTER(DimDate_CAGR, YEAR(DimDate_CAGR[Date]) * 12 + MONTH(DimDate_CAGR[Date]) = _Month_Last))
VAR _Current_TM = CALCULATE(SUM('CAGR Data1'[Value_Till_Month]), FILTER(DimDate_CAGR, YEAR(DimDate_CAGR[Date]) * 12 + MONTH(DimDate_CAGR[Date]) = _Month))
VAR _Last_TM = CALCULATE(SUM('CAGR Data1'[Value_Till_Month]), FILTER(DimDate_CAGR, YEAR(DimDate_CAGR[Date]) * 12 + MONTH(DimDate_CAGR[Date]) = _Month_Last))
VAR Result = DIVIDE(_Current, _Last)^DIVIDE(1, [Count_Slicer] - 1) - 1
RETURN
Result
