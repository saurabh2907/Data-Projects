import pandas as pd
import numpy as np

# Assuming df is your DataFrame and 'Banding' is the column you want to use for conditions
conditions = [
    df['Banding'] == "001_0 to 1 Lakh",
    df['Banding'] == "002_1 to 2 Lakhs",
    df['Banding'] == "003_2 to 2.5 Lakh",
    df['Banding'] == "004_2.5 to 5 Lakh",
    df['Banding'] == "005_above 5 Lakh"
]

choices = [
    "0-1 Lakh",
    "1-2 Lakh",
    "2-2.5 Lakh",
    "2.5 to 5 Lakh",
    "Above 5 Lakh"
]

df['Ticket Size'] = np.select(conditions, choices, default='')

# Displaying the DataFrame with the 'Ticket Size' column
print(df)
