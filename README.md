DatabaseError: Execution failed on sql: select * FROM [FinDB].[dbo].[Vintage_Mapper] 
('01000', '[01000] [Microsoft][ODBC SQL Server Driver][DBNETLIB]ConnectionWrite (send()). (10054) (SQLExecDirectW); [01000] [Microsoft][ODBC SQL Server Driver][DBNETLIB]General network error. Check your network documentation. (11)')
unable to rollback

df2 = pd.read_sql_query(f"""select * FROM [FinDB].[dbo].[Vintage_Mapper] """, con=Finconnection)
