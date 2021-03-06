---
layout: page
title: "Q262519: FIX: SQLSetCursorName Fails Without ANSI Quoted Identifiers"
permalink: /kb/262/Q262519/
---

## Q262519: FIX: SQLSetCursorName Fails Without ANSI Quoted Identifiers

{% raw %}

	Article: Q262519
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 2.1,3.7,7.0
	Operating System(s): 
	Keyword(s): kbMDAC kbODBC210bug kbSQLServ700 kbGrpDSVCDB kbDSupport kbGrpDSODBC kbODBC370bug
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SQL Server version 7.0 
	- Microsoft Open Database Connectivity, version 2.1 
	- Microsoft ODBC Driver for SQL Server, version 3.7 
	-------------------------------------------------------------------------------
	
	BUG #: 56244 (SQLBUG_70)
	
	SYMPTOMS
	========
	
	When you try to use a data source name (DSN) entry that does not have the Use
	ANSI Quoted Identifiers option selected to try to set a cursor name (through the
	use of the SQLSetCursorName API), the following error message appears:
	
	  "[Microsoft][ODBC SQL Server Driver]Invalid Cursor Name"
	
	To work around this problem, select the Use ANSI Quoted Identifiers option in the
	DSN. For additional information on ODBC, please refer to the platform SDK and
	MSDN documentation.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem has been corrected in U.S. Service Pack
	3 for Microsoft SQL Server version 7.0. For information about how to download
	and install the latest SQL Server Service Pack, see the following Microsoft Web
	site:
	
	  http://support.microsoft.com/view/dev.asp?ID=hl&pg=sql.asp
	
	For more information, contact your primary support provider.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Behavior in 32-bit ODBC Test (Odbcte32.exe)
	------------------------------------------------------------------
	
	1. Create a DSN to connect to Microsoft SQL Server.
	
	2. Clear the Use Ansi Quoted Identifiers option in the DSN.
	
	3. Within ODBC Test, select Full Connect and choose the DSN that you modified in
	  step 2.
	
	4. From the Stmt menu, choose SQLSetCursorName. In the SQLSetCursorName dialog
	  box, specify any cursor name (such as "Cl").
	
	5. Click ok. The error message will appear.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbMDAC kbODBC210bug kbSQLServ700 kbGrpDSVCDB kbDSupport kbGrpDSODBC kbODBC370bug 
	Technology        : kbSQLServSearch kbAudDeveloper kbSQLServ700 kbODBCSearch kbODBCSQLServ370 kbODBC210
	Version           : :2.1,3.7,7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
