---
layout: page
title: "Q120015: Windows NT RAS: X.25 Script for Sita Group Network Services"
permalink: /kb/120/Q120015/
---

## Q120015: Windows NT RAS: X.25 Script for Sita Group Network Services

{% raw %}

	Article: Q120015
	Product(s): Microsoft Windows NT
	Version(s): 3.10
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	3.10
	
	WINDOWS
	
	kbnetwork kb3rdparty
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes a script that allows Windows NT Remote Access Service
	(RAS) clients to connect to a Microsoft Windows NT RAS server equipped with an
	Eicon card over the Sita Group Network X.25 service. Sita Group Network is also
	known as Scitor, Inc.
	
	NOTES:
	
	  This script has only been tested at 9600 baud without compression
	  enabled.
	
	  This script does NOT work with RAS for Windows for Workgroups (WfWG)
	  version 3.11. However, there is a SWITCH.INF script available for RAS
	  for WfWG. For information on that, please see the following article in
	  the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q120014
	  TITLE : WFW 3.11 RAS: X.25 Script for Sita Group Network Services
	
	
	MORE INFORMATION
	================
	
	Follow these steps to build and install the new script:
	
	1. Make a backup copy of your existing PAD.INF file in your
	  %SYSTEMROOT%\SYSTEM32\RAS subdirectory by copying it to a new filename.
	
	2. Load the existing PAD.INF into Notepad and append the script below to the
	  file and save it. Quit Notepad.
	
	3. Start RAS, select the entry for the Sita X.25 provider in the phonebook list.
	
	4. Choose the Edit button.
	
	5. If you don't see an X.25 button, choose the Advanced button, and then choose
	  the X.25 button.
	
	6. In the PAD Type field, select Sita Group Network.
	
	7. Contact your system administrator if you don't know any of the following
	  information:
	
	  a. In the X.121 Address field, enter the x.121 address of your RAS server.
	
	  b. In the User Data field, enter the NUI number (usually in the format of "NUI
	  xxxxxxxx" where the "xxxxxxxx" needs to be replaced by numbers).
	
	  c. In the "Facilities" field, enter the user's password.
	
	8. Choose the OK button.
	
	9. Choose the Modem button. Select the appropriate baud rate up to 9600 bps and
	  select Enable Hardware Flow Control and Enable Modem Error Control.
	
	  NOTE: Modem compression is not recommended unless software compression is not
	  available, however, this script has not been tested with any kind of
	  compression enabled. Leave the Enter Modem Commands Manually check box clear
	  and choose OK and then choose OK again to return to the Remote Access
	  program.
	
	Remote Access is now ready to use this script and dial the server.
	
	Following is the script to be appended to the PAD.INF file:
	
	-------------------------- Beginning of Script ---------------------------
	
	;---------------------------------------------------------------------
	[SITA Group Network]
	
	; Disclaimer:
	; This script has been provided for customer convenience, but has NOT been
	; fully verified to work under all circumstances. Microsoft makes NO
	; guarantees as to the performance of this script. Please contact Microsoft
	; PSS Windows NT support if you have problems or questions.
	;
	; PLEASE SEE COMMENTS BELOW REGARDING USAGE OF THE "User Data:"
	; and "Facilities:" FIELDS IN RAS WHEN USING THIS SITA SCRIPT.
	
	DEFAULTOFF=
	MAXCARRIERBPS=9600
	MAXCONNECTBPS=9600
	
	COMMAND=...<cr>
	OK=<match>"SITA NETWORK:"
	
	; Enter your NUI number in the Remote Access program's X.25 Settings
	"User Data:" field.
	COMMAND=<UserData><cr>
	OK=<ignore>
	
	; Enter your x.25 password in the Remote Access program's X.25
	Settings "Facilities:" field.
	COMMAND=<Facilities><cr>
	OK=<match>"active"
	ERROR_DIAGNOSTICS=<cr><lf><cr><lf><lf><Diagnostics>
	ERROR_DIAGNOSTICS=<lf><cr><lf><Diagnostics>
	
	COMMAND=PROF 6<cr>
	NoResponse
	
	COMMAND=
	NoResponse
	
	COMMAND=SET 2:1<cr>
	OK=<ignore>
	
	COMMAND=
	NoResponse
	
	COMMAND=SET 4:1,6:1,16:0,17:0,18:0,19:0,21:0<cr>
	OK=<ignore>
	
	COMMAND=
	NoResponse
	
	COMMAND=SET 118:0,119:0,120:0<cr>
	OK=<ignore>
	
	COMMAND=PAR?<cr>
	OK=<ignore>
	
	COMMAND=SET 2:0<cr>
	NoResponse
	
	COMMAND=
	NoResponse
	
	COMMAND=<x25address><cr>
	CONNECT=<match>"connected"
	;CONNECT=<ignore>
	ERROR_DIAGNOSTICS=<cr><lf><cr><lf><lf><Diagnostics>
	ERROR_DIAGNOSTICS=<lf><cr><lf><Diagnostics>
	
	----------------------------- End of Script ------------------------------
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: prodnt 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW310 kbWinNTSsearch kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.10
	
	=============================================================================
	

{% endraw %}
