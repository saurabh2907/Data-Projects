New Table = 
VAR NumRows = 2  -- Adjust for the number of rows to add
VAR FirstTwoCompanies = 
  VAR FilteredTable = 
    FILTER('YourTable', EARLIER('YourTable'[RowNumber]) <= NumRows)
  RETURN
    DISTINCT(FilteredTable[Company])
VAR FirstTwoSales = 
  SUMX(
    FirstTwoCompanies,
    CALCULATE(SUM('YourTable'[Sales]), 'YourTable'[Company] = EARLIER([Company]))
  )
RETURN
  UNION(
    'YourTable',
    SELECTCOLUMNS(
      GENERATESERIES(COUNTROWS('YourTable') + 1, COUNTROWS('YourTable') + 1),
      "Company", CONCATENATEX(FirstTwoCompanies, "+" , EARLIER('YourTable'[Company])),
      "Sales", SUM(FirstTwoSales)
    )
  )
