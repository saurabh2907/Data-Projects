Overrun% = IF ( SELECTEDVALUE ( 'Sub Segment'[Sub_Segment] ) <> "PAR",
 DIVIDE ( SUM ( Premium_Dump[ANP] ) * AVERAGE ( Premium_Dump[Allowable] ), SUM ( Premium_Dump[IRNB] ) ) - ( AVERAGE ( Premium_Dump[Direct\Expense] ) + AVERAGE ( Premium_Dump[Allocated Expense] ) + AVERAGE ( Premium_Dump[RnR] ) + AVERAGE ( Premium_Dump[Variable Expense] ) ) * ( 1 - 0.06 ), IF (SELECTEDVALUE ( 'Sub Segment'[Sub_Segment] ) = "PAR",

DIVIDE ( SUM ( Premium_Dump[ANP] ) * AVERAGE ( Premium_Dump[Allowable] ), SUM ( Premium_Dump[IRNB] ) ) - ( AVERAGE ( Premium_Dump[Direct\Expense] ) + AVERAGE ( Premium_Dump[Allocated Expense] ) + AVERAGE ( Premium_Dump[RnR] ) + AVERAGE ( Premium_Dump[Variable Expense] ) ) * 0.1 * ( 1 - 0.085 ),BLANK() ))
