---
layout: page
title: "Q247150: XADM: Registry Error Message When Performing Soft Recovery"
permalink: /kb/247/Q247150/
---

## Q247150: XADM: Registry Error Message When Performing Soft Recovery

{% raw %}

	Article: Q247150
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kbenv exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Immediately after you run the eseutil /r command with a defined switch (for
	example, /ds or /is), the following error message may be displayed at the
	command prompt:
	
	  Microsoft(R) Windows NT(TM) Server Database Utilities Version 5.5 Copyright
	  (C) Microsoft Corporation 1991-1999. All Rights Reserved.
	
	  Error encountered accessing registry keys/values for specified Exchange
	  Store.
	
	  Exchange registry key access was denied, use default setting...
	
	  Initiating RECOVERY mode...
	  Log files: <current directory>
	  System files: <current directory>
	
	  Performing soft recovery...
	
	Although soft recovery may appear to run successfully and complete with an
	"Operation completed successfully" message, information in the log files may not
	be applied to the database.
	
	CAUSE
	=====
	
	This behavior occurs because the Windows NT account you are logged on as does
	not have Full Control permissions on the registry key that contains the path to
	the log files.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	Give the currently logged on Windows NT account Full Control permissions on the
	appropriate registry key:
	
	- If you run the eseutil /r /ds command, check the permissions on the following
	  registry key:
	
	  HKEY_LOCAL_MACHINE\System\CCS\Services\MSExchangeDS\Parameters
	
	- If you run the eseutil /r /is command, check the permissions on the following
	  registry key:
	
	  HKEY_LOCAL_MACHINE\System\CCS\Services\MSExchangeIS\ParametersSystem
	
	WORKAROUND
	==========
	
	If you are unable to assign the proper registry permissions, you can specify the
	log files and the system files locations at run time. For example, to run soft
	recovery on the information store database(s) when the log files are located in
	the <x>:\Exchsrvr\Mdbdata folder and the Edb.chk file is located in the
	<y>:\Exchsrvr\Mdbdata folder, run the following command:
	
	  eseutil /r /lX:\exchsrvr\mdbdata /sY:\exchsrvr\mdbdata
	
	You do not need to specify the location of the database(s) because the location
	of the database(s) is read from each log file during recovery.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Hardware          : ALPHA MIPS PPC x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
