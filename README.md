Overrun(%) =
VAR __PAR_Condition = Sub_Segment = "PAR"
VAR __Overrun_PAR = 
    DIVIDE(
        SUM(Premium_Dump[ANP]) * AVERAGE(Premium_Dump[Allowable]),
        SUM(Premium_Dump[IRNB])
    ) - (
        AVERAGE(Premium_Dump[Direct\Expense]) + 
        AVERAGE(Premium_Dump[Allocated Expense]) + 
        AVERAGE(Premium_Dump[RnR]) + 
        AVERAGE(Premium_Dump[Variable Expense])
    ) * (1 - 0.06)

VAR __Overrun_Other = 
    DIVIDE(
        SUM(Premium_Dump[ANP]) * AVERAGE(Premium_Dump[Allowable]),
        SUM(Premium_Dump[IRNB])
    ) - (
        AVERAGE(Premium_Dump[Direct\Expense]) + 
        AVERAGE(Premium_Dump[Allocated Expense]) + 
        AVERAGE(Premium_Dump[RnR]) + 
        AVERAGE(Premium_Dump[Variable Expense])
    ) * 0.1 * (1 - 0.085)

RETURN
    IF(__PAR_Condition, __Overrun_PAR, __Overrun_Other)
