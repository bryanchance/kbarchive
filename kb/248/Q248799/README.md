---
layout: page
title: "Q248799: HOWTO: Insert NULL Data with ODBC API Functions"
permalink: /kb/248/Q248799/
---

## Q248799: HOWTO: Insert NULL Data with ODBC API Functions

{% raw %}

	Article: Q248799
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 3.5,3.51,3.7,6.5,7.0
	Operating System(s): 
	Keyword(s): kbODBC kbSQLServ650 kbSQLServ700 kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC210 kbMDAC250
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, versions 3.5, 3.51 
	- Microsoft SQL Server versions 6.5, 7.0 
	- Microsoft ODBC Driver for SQL Server, version 3.7 
	- Microsoft Data Access Components versions 2.1, 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Using ODBC API functions such as SQLBindParameter and SQLExecDirect you can
	execute an INSERT statement and you can insert data into any backend database.
	Using ODBC API functions you can also insert null data into a particular column
	of a table, if the column allows nulls.
	
	This article demonstrates how you can programmatically insert NULL data into a
	database using ODBC API functions.
	
	MORE INFORMATION
	================
	
	The StrLen_or_IndPtr argument of the SQLBindParameter function (the last
	argument of that function) points to a buffer that contains one of the following
	when you call SQLExecute or SQLExecDirect:
	
	- SQL_NTS. The parameter value is a null-terminated string.
	
	- SQL_NULL_DATA. The parameter value is NULL.
	
	- SQL_DEFAULT_PARAM. A procedure that uses the default value of a parameter,
	  rather than a value retrieved from the application.
	
	- The result of the SQL_LEN_DATA_AT_EXEC(length) macro. The data for the
	  parameter is sent with SQLPutData.
	
	- SQL_DATA_AT_EXEC. The data for the parameter is sent with SQLPutData.
	
	When the STRLen_or_IndPtr argument contains SQL_NULL_DATA, you can insert null
	data in the corresponding column by calling SQLExecDirect or SQLExecute.
	
	Following is a code example that has been tested with SQL Server 7.0. This code
	works with any other database, but you may have to change the data type in the
	SQLBindParameter accordingly.
	
	  #include <windows.h>
	  #include <stdio.h>
	  #include <sql.h>
	  #include <sqlext.h>
	
	  int main(int argc, char* argv[])
	  {
	  	SQLCHAR*			theDiagState = new SQLCHAR[50];
	
	  	SQLINTEGER			theNativeState;
	  	SQLCHAR*			theMessageText  = new SQLCHAR[255];
	
	  	SQLSMALLINT			iOutputNo;
	
	  	SQLHENV		m_SQLEnvironment;
	  	SQLHDBC		m_SQLConnection;
	  	SQLHSTMT	m_SQLStatement;
	
	  	SQLRETURN			iReturn;
	  	DWORD				returnValue = 0;
	  	DWORD				returnValue1 = 0;
	  	long				lBufLength = sizeof(returnValue);
	  	long				lBufLength1 = sizeof(returnValue1);
	
	  	SQLCHAR  theNumeric2[50];
	  	SQLINTEGER cbNumeric, cbNumeric2;
	  	strcpy((char*)theNumeric2, "5.9");
	
	  	//Connect
	  	//Allocate Environment Handle
	  	iReturn = SQLAllocHandle(SQL_HANDLE_ENV,SQL_NULL_HANDLE,&m_SQLEnvironment);
	
	  	//Set environment to ODBC_3
	  	iReturn = SQLSetEnvAttr(m_SQLEnvironment,SQL_ATTR_ODBC_VERSION,(SQLPOINTER) SQL_OV_ODBC3,0);
	
	  	//Allocate connection handle
	  	iReturn = SQLAllocHandle(SQL_HANDLE_DBC,m_SQLEnvironment,&m_SQLConnection);
	
	  	//Connect to the database.
	  	//In this example we have used the following
	  	//Pubs as the DSN name
	  	//sa is the login name without a password
	  	//CHANGE THE DSN NAME HERE along with the length of the DSN.
	  	
	  	iReturn = SQLConnect(m_SQLConnection,(SQLCHAR*) "Pubs",4,(SQLCHAR*)"sa",2,(SQLCHAR*)"",0);
	  	if (iReturn != SQL_ERROR)
	  	{
	  	
	  		//Run Query
	  		//Allocate the statement handle
	  		iReturn = SQLAllocHandle(SQL_HANDLE_STMT,m_SQLConnection,&m_SQLStatement);
	
	  		//If you want to insert NULL data, the last parameter of SQLBindParameter should contain SQL_NULL_DATA
	  		cbNumeric = SQL_NULL_DATA;
	  		cbNumeric2 = SQL_NTS;
	
	  		//Sending Null Data
	  		iReturn = SQLBindParameter(m_SQLStatement,1,SQL_PARAM_INPUT,SQL_C_NUMERIC,SQL_NUMERIC,13,6,NULL,0,&cbNumeric);  	
	  		if (iReturn != SQL_SUCCESS)
	  		{
	  			SQLGetDiagRec(SQL_HANDLE_STMT,m_SQLStatement,1,theDiagState,&theNativeState,theMessageText,100,&iOutputNo);
	  		}
	  	
	  	
	  		//Sending nonNull Data
	  		iReturn = SQLBindParameter(m_SQLStatement,2,SQL_PARAM_INPUT,SQL_C_CHAR,SQL_NUMERIC,13,6,theNumeric2,0,&cbNumeric2);  
	  		if (iReturn != SQL_SUCCESS)
	  		{
	  			SQLGetDiagRec(SQL_HANDLE_STMT,m_SQLStatement,1,theDiagState,&theNativeState,theMessageText,100,&iOutputNo);
	  		}
	
	  		//Execute the statement to insert a null and a non-null value to the table.
	  		//CHANGE THE TABLE/COLUMN NAME HERE.
	  		//In this case we have used a table called TestNULL in SQL Server 7.0 with two fields
	  		//theNumber1 : Numeric Field that allows NULL data (Length =13, Precision = 28, Scale=6)
	  		//theNumber2 : Numeric that does not allow NULL data (Length =13, Precision = 28, Scale=6)
	  		iReturn = SQLExecDirect(m_SQLStatement,(SQLCHAR*) "Insert Into TestNull (theNumber1,theNumber2) Values (?,?)",SQL_NTS);
	  		if (iReturn != SQL_SUCCESS)
	  		{
	  			SQLGetDiagRec(SQL_HANDLE_STMT,m_SQLStatement,1,theDiagState,&theNativeState,theMessageText,100,&iOutputNo);
	
	  		}
	
	  		//DISCONNECT
	  		iReturn = SQLFreeHandle(SQL_HANDLE_STMT,m_SQLStatement);
	  		iReturn = SQLDisconnect(m_SQLConnection);
	  		iReturn = SQLFreeHandle(SQL_HANDLE_DBC,m_SQLConnection);
	  		iReturn = SQLFreeHandle(SQL_HANDLE_ENV,m_SQLEnvironment);
	
	  		m_SQLStatement = NULL;
	  		m_SQLConnection = NULL;
	  		m_SQLEnvironment = NULL;
	  	}
	  	else
	  	{
	  		//If it fails to connect theMessageText contains the reason for failure
	  		SQLGetDiagRec(SQL_HANDLE_DBC,m_SQLConnection,1,theDiagState,&theNativeState,theMessageText,100,&iOutputNo);
	
	  	}
	
	  	delete theMessageText; 
	  	delete theDiagState;
	  	return 1;
	  }
	
	When you execute the preceding program, it inserts a NULL value in the first
	column and 5.9 in the second column.
	
	REFERENCES
	==========
	
	For additional information on inserting NULL data, click the article numbers
	below to view the articles in the Microsoft Knowledge Base:
	
	  Q260310 HOWTO: Insert Null Data with OLE DB SDK Interfaces
	
	  Q260900 HOWTO: Insert NULL Data with OLE DB Consumer Templates
	
	Additional query words:
	
	======================================================================
	Keywords          : kbODBC kbSQLServ650 kbSQLServ700 kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC210 kbMDAC250 kbMDAC260 kbmdac270 
	Technology        : kbSQLServSearch kbAudDeveloper kbSQLServ700 kbSQLServ650 kbODBCSearch kbMDACSearch kbMDAC210 kbMDAC250 kbMDAC260 kbODBCSQLServ370 kbODBC350 kbODBC351 kbMDAC270
	Version           : :3.5,3.51,3.7,6.5,7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
