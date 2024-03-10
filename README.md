Last_Month_NBMX = 
  CALCULATE(
    [NBM Selected],
    DATESBETWEEN(
      DimDate[Date],
      DATE(YEAR(TODAY()), MONTH(TODAY())-1, 1),
      EOMONTH(DATE(YEAR(TODAY()), MONTH(TODAY())-1), 0)
    )
  )
