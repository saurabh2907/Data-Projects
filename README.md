Last_Month_NBMX = VAR
  SelectedMonthName = SELECTEDVALUE('SlicerMonth'[Month Name])  ;; Replace 'SlicerMonth' with your slicer table name
  RelatedDate = RELATED('DimDate'[Date], DimDate[Month Name], SelectedMonthName)
RETURN
  CALCULATE(
    [NBM Selected],
    DimDate[Month No] = MONTH(RelatedDate) - 1
  )
