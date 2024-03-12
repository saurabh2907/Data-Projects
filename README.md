Last3MAvg = 
VAR SelectedMonthName = SELECTEDVALUE(Month_Name_Slicer[Month_Name])
VAR SelectedYearName = SELECTEDVALUE('FY Year'[FY Year])
VAR CurrentMonthNo = IF( SelectedMonthName = "APR", 1, IF(SelectedMonthName = "MAY", 2, IF(SelectedMonthName = "JUN", 3, IF(SelectedMonthName = "JUL", 4, IF(SelectedMonthName = "AUG", 5, IF(SelectedMonthName = "SEP", 6, IF(SelectedMonthName = "OCT", 7, IF(SelectedMonthName = "NOV", 8, IF(SelectedMonthName = "DEC", 9, IF(SelectedMonthName = "JAN", 10, IF(SelectedMonthName = "FEB", 11, 12)))))))))))

VAR CurrentYear = IF(SelectedYearName = "FY-22", 2022, IF(SelectedYearName = "FY-23", 2023, IF(SelectedYearName = "FY-24", 2024)))
VAR CurrentMonth = EOMONTH(DATE(CurrentYear, MONTH(CurrentMonthNo), 1), 0) 

RETURN CurrentMonth
