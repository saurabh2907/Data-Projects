def Rev_SP_Code(row):
    if row['NewSPCode1'].isnull():
        return row['NewSPCode2']
    else:
        return row['NewSPCode1']
    
raw_nbm_db['Rev_SP_Code'] = raw_nbm_db.apply(Rev_SP_Code, axis=1)

