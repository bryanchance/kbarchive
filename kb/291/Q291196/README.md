---
layout: page
title: "Q291196: BDC Running WINS May Log Event Error 3096"
permalink: /kb/291/Q291196/
---

## Q291196: BDC Running WINS May Log Event Error 3096

{% raw %}

	Article: Q291196
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork w2000wins kbWINS
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If a backup domain controller (BDC) is running Windows Internet Name Service
	(WINS), the following event error may be logged when you start the BDC:
	
	  Event ID: 3096
	  Source: Net Logon
	  The Windows NT Domain Controller for this domain could not be located.
	
	Approximately 30 seconds after the startup process is complete, the BDC is once
	again accessible.
	
	CAUSE
	=====
	
	This problem occurs because WINS is starting too late in the process for name
	resolution to occur.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this problem, edit the registry and create a dependency for WINS in
	the Net Logon service:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the DependOnService value under the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\
	
	3. On the Edit menu, click Multi String, type "Wins" (without the quotation
	  marks) to add it to the list of dependencies, and then click OK.
	
	4. Quit Registry Editor.
	
	5. Restart the computer.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbnetwork w2000wins kbWINS 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
