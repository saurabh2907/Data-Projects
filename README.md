import pandas as pd
import numpy as np

# Assuming PAR is your DataFrame

# Calculate the sum of Direct Expense, Allocated Expense, RnR, and Variable Expense
PAR['Total_Expenses'] = PAR['Direct\Expense'].fillna(0) + PAR['Allocated Expense'].fillna(0) + PAR['RnR'].fillna(0) + PAR['Variable Expense'].fillna(0)

# Calculate Overrun with handling zero division
PAR['Overrun'] = np.where(
    PAR['IRNB'] != 0,
    (((PAR['ANP'] * PAR['Allowable']) / PAR['IRNB']) - PAR['Total_Expenses']) * 0.1 * (1 - 0.085),
    0
)
