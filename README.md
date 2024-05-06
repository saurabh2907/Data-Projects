DatabaseError: Execution failed on sql 'SELECT name FROM sqlite_master WHERE type='table' AND name=?;': ('42S02', "[42S02] [Microsoft][ODBC SQL Server Driver][SQL Server]Invalid object name 'sqlite_master'. (208) (SQLExecDirectW); [42S02] [Microsoft][ODBC SQL Server Driver][SQL Server]Statement(s) could not be prepared. (8180)")


df.to_sql(name='Vintage_Mapper',con=Finconnection, if_exists='append', index=False)
