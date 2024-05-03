Growth_Amt%_MTD = 
VAR Actual = [DatesMTD_Amt_Actual_RTL]
VAR PY = [PY Value Amt_Actual_MTD]
RETURN
IF(OR(ISBLANK(Actual),ISBLANK(PY)), "NA",
DIVIDE(Actual,PY,0) -1
)
