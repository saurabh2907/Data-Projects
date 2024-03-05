=IF(AND(Y106="R",A106<1100),IF(A106+1100=1129,2090,IF(A106+1100=1134,2094,IF(A106+1100=1131,2092,IF(A106+1100=1156,2095,IF(A106+1100=1224,2098,A106+1100))))),IF(AND(Y106="G",A106<1100),IF(A106+1100=1118,2096,IF(A106+1100=1105,2097,A106+1100))))
where Y106 = Ret/Grp, A106 = SPCODE



import pandas as pd

def calculate_new_spcode(row):
    if row['Ret/Grp'] == "R" and row['SPCODE'] < 1100:
        if row['SPCODE'] + 1100 == 1129:
            return 2090
        elif row['SPCODE'] + 1100 == 1134:
            return 2094
        elif row['SPCODE'] + 1100 == 1131:
            return 2092
        elif row['SPCODE'] + 1100 == 1156:
            return 2095
        elif row['SPCODE'] + 1100 == 1224:
            return 2098
        else:
            return row['SPCODE'] + 1100
    elif row['Ret/Grp'] == "G" and row['SPCODE'] < 1100:
        if row['SPCODE'] + 1100 == 1118:
            return 2096
        elif row['SPCODE'] + 1100 == 1105:
            return 2097
        else:
            return row['SPCODE'] + 1100
    else:
        return row['SPCODE']

# Assuming you have a DataFrame named df with columns 'Ret/Grp' and 'SPCODE'
df['New_SPCode1'] = df.apply(calculate_new_spcode, axis=1)
