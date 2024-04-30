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
  VAR FilteredData = 
    FILTER(
      ALL('YourTable'),
      [ColumnToFilter] = CALCULATE(
        PREVIOUSVALUE('YourTable'[ColumnToReference]),
         EARLIER('YourTable'[RowNumber]) = 1
      )
    )
  RETURN
  UNION(
    FilteredData,
    SELECTCOLUMNS(
      GENERATESERIES(COUNTROWS(FilteredData) + 1, COUNTROWS(FilteredData) + 1),
      "Company", CONCATENATEX(FirstTwoCompanies, "+" , EARLIER(FilteredData[Company])),
      "Sales", SUM(FirstTwoSales)
    )
  )
