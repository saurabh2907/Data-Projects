Last_3_Month_Average = 
VAR CurrentMonth = EOMONTH(TODAY(),-1)
VAR Last3Months =
    DATESINPERIOD(DimDate[Date],CurrentMonth,-3,MONTH)
VAR Avg_3_Months = AVERAGEX(FILTER(ALL(DimDate), DimDate[Date] IN Last3Months),[NBM Selected])
    RETURN
    DIVIDE([NBM Selected], Avg_3_Months) -1



Selected value ANP_Prev_Month = 
VAR SelectedMonthName = SELECTEDVALUE(Month_Name_Slicer[Month_Name]) 
VAR PreviousMonthNo =  IF(SelectedMonthName = "APR", 1, IF(SelectedMonthName = "MAY", 2, IF(SelectedMonthName = "JUN", 3, IF(SelectedMonthName = "JUL", 4, IF(SelectedMonthName = "AUG", 5, IF(SelectedMonthName = "SEP", 6, IF(SelectedMonthName = "OCT", 7, IF(SelectedMonthName = "NOV", 8,
 IF(SelectedMonthName = "DEC", 9, IF(SelectedMonthName = "JAN", 10, IF(SelectedMonthName = "FEB", 11,
 12))))))))))) -1

 RETURN CALCULATE( [Total Value ANP], FILTER(DimDate,DimDate[Month No] = PreviousMonthNo ))
