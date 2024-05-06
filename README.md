import pandas as pd
import pyodbc
from datetime import datetime

# Function to read data from Excel and append it to SQL Server
def append_excel_to_sql(excel_file, server, database, table, username, password):
    # Read Excel file into a DataFrame
    df = pd.read_excel(excel_file)
    
    # Connect to SQL Server
    conn = pyodbc.connect('DRIVER={SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
    cursor = conn.cursor()
    
    # Append data to SQL Server table
    for index, row in df.iterrows():
        values = tuple(row)
        cursor.execute("INSERT INTO " + table + " VALUES (" + ",".join(["?" for _ in values]) + ")", values)
    
    # Commit changes and close connection
    conn.commit()
    conn.close()
    print("Data appended to SQL Server at", datetime.now())

# Define file paths and database connection details
excel_file = 'data.xlsx'
server = 'your_server'
database = 'your_database'
table = 'your_table'
username = 'your_username'
password = 'your_password'

# Call the function to append data to SQL Server
append_excel_to_sql(excel_file, server, database, table, username, password)


ProgrammingError: ('42000', '[42000] [Microsoft][ODBC SQL Server Driver][SQL Server]The incoming tabular data stream (TDS) remote procedure call (RPC) protocol stream is incorrect. Parameter 4 (""): The supplied value is not a valid instance of data type float. Check the source data for invalid values. An example of an invalid value is data of numeric type with scale greater than precision. (8023) (SQLExecDirectW)')

