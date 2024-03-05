=IF(AND(Y106="R"),IF(A106=1129,2090,IF(A106=1134,2094,IF(A106=1131,2092,IF(A106=1156,2095,IF(A106=1224,2098,A106))))),IF(AND(Y106="G"),IF(A106=1118,2096,IF(A106=1105,2097,A106))))


import pandas as pd

def calculate_new_spcode(row):
    if row['Ret/Grp'] == "R":
        if row['SPCODE'] == 1129:
            return 2090
        elif row['SPCODE'] == 1134:
            return 2094
        elif row['SPCODE'] == 1131:
            return 2092
        elif row['SPCODE'] == 1156:
            return 2095
        elif row['SPCODE'] == 1224:
            return 2098
        else:
            return row['SPCODE']
    elif row['Ret/Grp'] == "G":
        if row['SPCODE'] == 1118:
            return 2096
        elif row['SPCODE'] == 1105:
            return 2097
        else:
            return row['SPCODE']
    else:
        return row['SPCODE']

# Assuming you have a DataFrame named df with columns 'Ret/Grp' and 'SPCODE'
df['New_SPCode1'] = df.apply(calculate_new_spcode, axis=1)
