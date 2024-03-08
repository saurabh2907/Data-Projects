import pandas as pd
import numpy as np

# Assuming df is your DataFrame and '_003_Age_banding_Summary[PREM_FREQ]' is the column you want to use for conditions
conditions = [
    df['_003_Age_banding_Summary[PREM_FREQ]'] == "1",
    df['_003_Age_banding_Summary[PREM_FREQ]'] == "4",
    df['_003_Age_banding_Summary[PREM_FREQ]'] == "2",
    df['_003_Age_banding_Summary[PREM_FREQ]'] == "12",
    df['_003_Age_banding_Summary[PREM_FREQ]'] == "0"
]

choices = [
    '\u200B\u200B\u200B\u200B\u200BYearly',
    '\u200B\u200B\u200B\u200BQuaterly',
    '\u200B\u200B\u200BHalf-Yearly',
    '\u200B\u200BMonthly',
    '\u200BSP'
]

df['Premium Frequency'] = np.select(conditions, choices, default='')

# Displaying the DataFrame with the 'Premium Frequency' column
print(df)
