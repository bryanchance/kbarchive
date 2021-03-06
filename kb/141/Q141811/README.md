---
layout: page
title: "Q141811: BUG: Problems w/ ODBC 32-bit Thunking Installer DLL in Win32s"
permalink: /kb/141/Q141811/
---

## Q141811: BUG: Problems w/ ODBC 32-bit Thunking Installer DLL in Win32s

{% raw %}

	Article: Q141811
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:2.10
	Operating System(s): 
	Keyword(s): kbBug kbISS
	Last Modified: 27-JUL-2001
	
	2.10.2401
	WINDOWS
	kbinterop kbprg kbbug2.10
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 2.10 
	-------------------------------------------------------------------------------
	
	BUG#: 3187 (ODBCSDK2)
	
	SYMPTOMS
	========
	
	When 32-bit ODBC applications that call the Installer API (ODBCCP32.DLL) are run
	under the Win32s subsystem in a Windows for Workgroups (WFW) version 3.11
	environment, the following error occurs:
	
	  Initialization of a DLL failed, the process is terminating abnormally, cannot
	  run program, unexpected error: 21.
	
	WORKAROUND
	==========
	
	The application will run successfully if ODBCCP32.DLL is replaced with the
	version of the DLL file from the ODBC 2.0 components (these components ship with
	Visual C++ 2.0).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in ODBCCP32.DLL (Thunking DLL)
	version 2.10.2401. We are researching this problem and will post new information
	here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	To reproduce this problem:
	
	Build the following program to create a 32-bit EXE file (Add ODBC32.LIB and
	ODBCCP32.LIB to the link libraries in projectsettings):
	
	  #include <windows.h>
	  #include <sql.h>
	  #include <sqlext.h>
	  #include <odbcinst.h>
	
	  int WINAPI WinMain(HINSTANCE hinst,HINSTANCE pinst,LPSTR szCmd,int nShow)
	  {
	     if (SQLConfigDataSource(NULL,ODBC_ADD_DSN,
	        "SQL Server","DSN=Oof\0Server=Oof\0\0"))
	     {
	        MessageBox(NULL,"SQLConfigDataSource succeeded",
	           "SQLConfigDataSource",MB_OK);
	     }
	     else
	     {
	        MessageBox(NULL,"SQLConfigDataSource failed",
	           "SQLConfigDataSource",MB_OK);
	     }
	     return 0;
	  }
	
	Install the Win32s subsystem from the Win32 SDK on a WFW 3.11 computer. Run the
	program on Win32s with the ODBC 2.10a or 2.10b components (these ship with VC++
	2.1,2.2, and 4.0). It will fail to load with a message that a DLL could not load
	or something similar (depends on the version of Win32s).
	
	Additional query words: 2.10.2401 Thunking DLL
	
	======================================================================
	Keywords          : kbBug kbISS 
	Technology        : kbAudDeveloper kbODBCSearch
	Version           : WINDOWS:2.10
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
