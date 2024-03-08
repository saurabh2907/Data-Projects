import pandas as pd
import numpy as np

# Assuming df is your DataFrame and '_003_Age_banding_Summary[Vertical]' is the column you want to use for conditions
conditions = [
    df['_003_Age_banding_Summary[Vertical]'] == "AXIS BANK",
    df['_003_Age_banding_Summary[Vertical]'] == "AXIS BANK (BRANCH)",
    df['_003_Age_banding_Summary[Vertical]'] == "AXIS BANK (RETAIL)",
    df['_003_Age_banding_Summary[Vertical]'] == "Axis Vertial Center",
    df['_003_Age_banding_Summary[Vertical]'] == "BANDHAN BANK"
]

choices = [
    "Axis Bank",
    "Axis Bank",
    "Axis Bank",
    "Axis Bank",
    "Bandhan Bank"
]

df['Axis_Bandhan_Vertical'] = np.select(conditions, choices, default='')

# Displaying the DataFrame with the 'Axis_Bandhan_Vertical' column
print(df)
