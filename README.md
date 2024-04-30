New Table = 
VAR NumRows = 2  -- Adjust for the number of rows to add
VAR CompanyList = 
  GENERATESERIES(1, NumRows)
VAR SalesList = 
  SUMX(
    CompanyList,
    CALCULATE(SUM('YourTable'[Sales])))
RETURN
  VAR Combined = 
    CONCATENATEX(
      CompanyList,
      FIRSTNONBLANK('YourTable'[Company], 1)
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
