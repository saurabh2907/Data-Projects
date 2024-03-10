Last_Month_NBMX = VAR
  SelectedMonthName = SELECTEDVALUE('SlicerMonth'[Month Name])  ; Replace 'SlicerMonth' with your slicer table name
RETURN
  SWITCH(
    TRUE,
    SelectedMonthName = "April", 3,  ; Previous month for April is March (3)
    SelectedMonthName = "May", 4,  ; Previous month for May is April (4)
    SelectedMonthName = "June", 5,  ; Previous month for June is May (5)
    TRUE  ; Handle other selections (optional)
  ) - 1
  VAR
    PreviousMonthNo = SWITCH(Result)  ; Result from SWITCH above
  RETURN
    CALCULATE(
      [NBM Selected],
      DimDate[Month No] = PreviousMonthNo
    )
