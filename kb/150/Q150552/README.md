---
layout: page
title: "Q150552: HOWTO: How To Avoid the ODBC Login Dialog when Using MFC"
permalink: /kb/150/Q150552/
---

## Q150552: HOWTO: How To Avoid the ODBC Login Dialog when Using MFC

{% raw %}

	Article: Q150552
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:2.5; winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbDatabase kbMFC kbODBC kbVC kbGrpDSVCDB kbDSupport kbMDAC250
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.5, 151, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, when you use the MFC ODBC database classes to connect to a
	datasource, ODBC invokes a login dialog box that allows the user to type in any
	necessary information, such as a password, to log in.
	
	With Visual C++ 4.2, use the CDatabase::OpenEx() method to connect to an ODBC
	datasource with MFC. Inside CDatabase::Connect(), which is called by
	CDatabase::OpenEx(), is a call to the ODBC API function, SQLDriverConnect, that
	does the work to connect.
	
	With versions of Visual C++ earlier than 4.2, use the CDatabase::Open() method to
	connect to an ODBC datasource with MFC. Inside CDatabase::Open() is a call to
	the ODBC API function, SQLDriverConnect, that does the work to connect.
	
	The last parameter to SQLDriverConnect is a flag indicating whether the ODBC
	Driver Manager or driver should prompt for more connection information. MFC uses
	the SQL_DRIVER_COMPLETE flag that instructs ODBC to invoke a login dialog if you
	do not supply a connect string with all of the information necessary to make a
	connection.
	
	Occasionally it is preferable to suppress ODBC from creating a dialog by calling
	SQLDriverConnect and passing SQL_DRIVER_NOPROMPT as the last parameter. The
	SQL_DRIVER_NOPROMPT flag instructs ODBC to connect with the information passed
	in the connect string. If the connection string does not contain enough
	information to connect to the data source, the call to SQLDriverConnect()
	returns a value of SQL_ERROR.
	
	With Visual C++ 4.2, specify the CDatabase::noOdbcDialog option as the second
	argument to CDatabase::OpenEx(). This will cause CDatabase::OpenEx() to call
	SQLDriverConnect with the SQL_DRIVER_NOPROMPT flag.
	
	To accomplish this behavior using the MFC database classes included with versions
	of Visual C++ before 4.2, you need to derive a new class from CDatabase and
	override CDatabase::Open().
	
	Copy the code for CDatabase::Open() from the MFC source file Dbcore.cpp. Then
	change the call to SQLDriverConnect by replacing SQL_DRIVER_COMPLETE with
	SQL_DRIVER_NOPROMPT.
	
	The second parameter in SQLDriverConnect is a window handle. You need to pass
	NULL for this.
	
	Also, add a check for a return value of SQL_ERROR.
	
	MORE INFORMATION
	================
	
	Sample code for Visual C++ 4.2 can be found in the online documentation for
	CDatabase::OpenEx().
	
	Sample Code
	-----------
	
	     // The code provided here works with MFC 4.1.
	     // Code to work with other versions of MFC before 4.2 will be very
	     // similar. You just need to copy the source for CDatabase::Open() from
	     // Dbcore.cpp, make the changes described in this article, and then
	     // determine which file specific definitions and header files to add
	     // to your .cpp file.
	
	     // MyDataBase.h
	     // Derive a class from CDatabase
	
	     class CMyDatabase : public CDatabase
	     {
	       public:
	
	       Open(LPCTSTR lpszDSN, BOOL bExclusive = FALSE,
	            BOOL bReadonly = FALSE, LPCTSTR lpszConnect = "ODBC;",
	            BOOL bUseCursorLib = TRUE);
	     };
	
	     //MyDataBase.cpp
	     #include "stdafx.h"
	     #include <afxpriv.h>
	     #include <afxdisp.h>
	
	     #include "MyDataBase.h"
	
	     // This line of code is borrowed from Dbcore.cpp
	     static const TCHAR szODBC[] = _T("ODBC;");
	
	     // These two lines are borrowed from Afximpl.h
	     // determine number of elements in an array (not bytes)
	     #define _countof(array) (sizeof(array)/sizeof(array[0]))
	
	     BOOL CMyDatabase::Open(LPCTSTR lpszDSN, BOOL bExclusive,
	       BOOL bReadonly, LPCTSTR lpszConnect, BOOL bUseCursorLib)
	     {
	       UCHAR szConnectOutput[MAX_CONNECT_LEN];
	
	     #ifdef _68K_
	       if(nClassObject == 0)
	       AfxThrowDBException(AFX_SQL_ERROR_ODBC_LOAD_FAILED, NULL,
	                           SQL_NULL_HSTMT);
	     #endif
	
	     ASSERT_VALID(this);
	     ASSERT(lpszDSN == NULL || AfxIsValidString(lpszDSN));
	     ASSERT(lpszConnect == NULL || AfxIsValidString(lpszConnect));
	
	     // Exclusive access not supported.
	     ASSERT(!bExclusive);
	     UNUSED(bExclusive);  // unused in release builds
	
	     m_bUpdatable = !bReadonly;
	
	     TRY
	     {
	     if (lpszConnect != NULL)
	       m_strConnect = lpszConnect;
	
	     // For Visual Basic & Microsoft Access compatibility, use the
	     // "ODBC;" (or "odbc;") prefix to the connect string
	     if (_tcsnicmp(m_strConnect, szODBC, lstrlen(szODBC)) != 0)
	     {
	       TRACE0("Error: Missing 'ODBC' prefix on connect string.\n");
	       return FALSE;
	     }
	
	     // Strip "ODBC;"
	     m_strConnect = m_strConnect.Right(m_strConnect.GetLength()
	                      - lstrlen(szODBC));
	
	     if (lpszDSN != NULL && lstrlen(lpszDSN) != 0)
	       {
	         // Append "DSN=" lpszDSN
	         m_strConnect += ";DSN=";
	          m_strConnect += lpszDSN;
	        }
	
	          AllocConnect();
	
	          RETCODE nRetCode;
	          // Turn on cursor lib support
	          if (bUseCursorLib)
	          {
	            AFX_SQL_SYNC(::SQLSetConnectOption(m_hdbc,
	                SQL_ODBC_CURSORS, SQL_CUR_USE_ODBC));
	              // With cursor library added records immediately in result set
	              m_bIncRecordCountOnAdd = TRUE;
	            }
	
	            HWND hWndTop;
	            CWnd* pWnd = CWnd::GetSafeOwner(NULL, &hWndTop);
	            if (pWnd == NULL)
	              pWnd = CWnd::GetDesktopWindow();
	            ASSERT_VALID(pWnd);
	
	            SWORD nResult;
	     #ifndef _MAC
	            USES_CONVERSION;
	
	        // Code before it was changed:
	        //    AFX_SQL_SYNC(::SQLDriverConnect(m_hdbc, pWnd->m_hWnd,
	        //      (UCHAR*)T2A((LPCTSTR)m_strConnect), SQL_NTS,
	        //      szConnectOutput, _countof(szConnectOutput),
	        //      &nResult, SQL_DRIVER_COMPLETE));
	
	            AFX_SQL_SYNC(::SQLDriverConnect(m_hdbc, NULL,
	              (UCHAR*)(const char*)m_strConnect, SQL_NTS,
	              szConnectOutput, _countof(szConnectOutput),
	              &nResult, SQL_DRIVER_NOPROMPT));
	
	     #else
	         AFX_SQL_SYNC(::SQLDriverConnect(m_hdbc, GetWrapperWindow
	              (pWnd->m_hWnd), (UCHAR*)(const char*)m_strConnect, SQL_NTS,
	              szConnectOutput, _countof(szConnectOutput),
	              &nResult, SQL_DRIVER_COMPLETE));
	
	     #endif
	         if (hWndTop != NULL)
	           ::EnableWindow(hWndTop, TRUE);
	
	         // Code before it was changed:
	          //    if (nRetCode == SQL_NO_DATA_FOUND)
	         // Now need to check for SQL_ERROR too
	         if ((nRetCode == SQL_NO_DATA_FOUND) || (nRetCode == SQL_ERROR))
	         {
	           Free();
	           return FALSE;
	         }
	
	         if (!Check(nRetCode))
	         {
	     #ifdef _DEBUG
	         if (pWnd->m_hWnd == NULL)
	            TRACE0("Error: No default window (AfxGetApp()->m_pMainWnd) for
	        SQLDriverConnect.\n");
	     #endif
	           ThrowDBException(nRetCode);
	         }
	
	         // Connect strings must have "ODBC;"
	         m_strConnect = szODBC;
	         // Save connect string returned from ODBC
	      m_strConnect += (char*)szConnectOutput;
	
	         SWORD nAPIConformance;
	         AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_ODBC_API_CONFORMANCE,
	           &nAPIConformance, sizeof(nAPIConformance), &nResult));
	         if (!Check(nRetCode))
	           ThrowDBException(nRetCode);
	
	         if (nAPIConformance < SQL_OAC_LEVEL1)
	           ThrowDBException(AFX_SQL_ERROR_API_CONFORMANCE);
	
	         SWORD nSQLConformance;
	         AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_ODBC_SQL_CONFORMANCE,
	           &nSQLConformance, sizeof(nSQLConformance), &nResult));
	         if (!Check(nRetCode))
	           ThrowDBException(nRetCode);
	
	         if (nSQLConformance < SQL_OSC_MINIMUM)
	           ThrowDBException(AFX_SQL_ERROR_SQL_CONFORMANCE);
	
	         AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_CURSOR_COMMIT_BEHAVIOR,
	           &m_nCursorCommitBehavior, sizeof(m_nCursorCommitBehavior),
	           &nResult));
	         if (!Check(nRetCode))
	           m_nCursorCommitBehavior = SQL_ERROR;
	
	         AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_CURSOR_ROLLBACK_BEHAVIOR,
	           &m_nCursorRollbackBehavior, sizeof(m_nCursorRollbackBehavior),
	           &nResult));
	        if (!Check(nRetCode))
	          m_nCursorRollbackBehavior = SQL_ERROR;
	
	        UDWORD dwGetDataExtensions;
	        AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_GETDATA_EXTENSIONS,
	          &dwGetDataExtensions, sizeof(dwGetDataExtensions),
	          &nResult));
	        if (!Check(nRetCode))
	          dwGetDataExtensions = 0;
	        if (dwGetDataExtensions & SQL_GD_BOUND)
	          m_dwUpdateOptions = AFX_SQL_GDBOUND;
	        else
	          m_dwUpdateOptions = 0;
	
	        // Set required transaction support for CRecordset cursors
	        if ((m_nCursorCommitBehavior == SQL_CB_PRESERVE) &&
	          (m_nCursorRollbackBehavior == SQL_CB_PRESERVE))
	          m_bTransactions = TRUE;
	
	        if (m_bUpdatable)
	        {
	          // Make sure data source is Updatable
	          char szReadOnly[10];
	          AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_DATA_SOURCE_READ_ONLY,
	            szReadOnly, _countof(szReadOnly), &nResult));
	          if (Check(nRetCode) && nResult == 1)
	            m_bUpdatable = !(lstrcmpA(szReadOnly, "Y") == 0);
	          else
	            m_bUpdatable = FALSE;
	     #ifdef _DEBUG
	           if (!m_bUpdatable && (afxTraceFlags & traceDatabase))
	             TRACE0("Warning: data source is readonly.\n");
	     #endif
	         }
	         else
	         {
	           // Make data source is Updatable
	           AFX_SQL_SYNC(::SQLSetConnectOption(m_hdbc,
	             SQL_ACCESS_MODE, SQL_MODE_READ_ONLY));
	         }
	
	         char szIDQuoteChar[2];
	         AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_IDENTIFIER_QUOTE_CHAR,
	           szIDQuoteChar, _countof(szIDQuoteChar), &nResult));
	         if (Check(nRetCode) && nResult == 1)
	           m_chIDQuoteChar = szIDQuoteChar[0];
	         else
	           m_chIDQuoteChar = ' ';
	
	     #ifdef _DEBUG
	         if (afxTraceFlags & traceDatabase)
	         {
	           char szInfo[64];
	           AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_DBMS_NAME,
	             szInfo, _countof(szInfo), &nResult));
	           if (Check(nRetCode))
	           {
	             CString strInfo = szInfo;
	             TRACE1("DBMS: %s\n", strInfo);
	             AFX_SQL_SYNC(::SQLGetInfo(m_hdbc, SQL_DBMS_VER,
	               szInfo, _countof(szInfo), &nResult));
	             if (Check(nRetCode))
	             {
	               strInfo = szInfo;
	               TRACE1(", Version: %s\n", strInfo);
	             }
	           }
	         }
	     #endif
	       }
	       CATCH_ALL(e)
	       {
	         Free();
	         THROW_LAST();
	       }
	       END_CATCH_ALL
	
	       return TRUE;
	     }
	
	REFERENCES
	==========
	
	Class Library Reference for CDatabase::OpenEx member function.
	
	Additional query words: 1.50 1.51 1.52 2.00 2.10 2.20 4.00 4.10 4.20
	
	======================================================================
	Keywords          : kbcode kbDatabase kbMFC kbODBC kbVC kbGrpDSVCDB kbDSupport kbMDAC250 
	Technology        : kbAudDeveloper kbMFC
	Version           : WINDOWS:2.5; winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
