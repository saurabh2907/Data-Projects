New Table = 
VAR NumRows = 2  -- Adjust for the number of rows to add
VAR CompanyList = 
  GENERATESERIES(1, NumRows)
VAR SalesList = 
  SUMX(
    CompanyList,
    CALCULATE(SUM('YourTable'[Sales]), EARLIER('YourTable'[Company])))
RETURN
  VAR Combined = 
    CONCATENATEX(
      CompanyList,
      CALCULATE(FIRSTNONBLANK('YourTable'[Company],1), EARLIER('YourTable'[Company]))
      ," + ")
  RETURN
  UNION(
    'YourTable',
    SELECTCOLUMNS(
      GENERATESERIES(ROWS('YourTable') + 1, 1),
      "Company", Combined,
      "Sales", SUMX(SalesList,[Sales])
    )
  )
