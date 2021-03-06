---
layout: page
title: "Q177932: INFO: How to Disable LMHOSTS Lookup During an Unattended Install"
permalink: /kb/177/Q177932/
---

## Q177932: INFO: How to Disable LMHOSTS Lookup During an Unattended Install

{% raw %}

	Article: Q177932
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbOPK kbSBK
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	NetBIOS name resolution using the LMHOSTS file is enabled by default during
	Windows NT installation. You may want to configure Windows NT unattended Setup
	so that LMHOSTS lookup is disabled. This article describes how to disable
	LMHOSTS lookup during a Windows NT 4.0 unattended Setup.
	
	MORE INFORMATION
	================
	
	To disable LMHOSTS lookup during unattended Setup, follow these steps:
	
	1. Create a new share on a network server and then copy the I386 folder (or
	  appropriate platform folder) from the Windows NT 4.0 CD-ROM to the new share.
	
	2. Using any text editor (such as Notepad), add the following entry to the
	  [Unattended] section of the Unattend.txt file:
	
	        OEMPreinstall = Yes
	
	3. Save and then close the Unattend.txt file.
	
	4. Create a new folder named $OEM$ in the share you created in step 1.
	
	5. In the $OEM$ folder, create a file with the following entries. Save the file
	  as <filename>.reg, where <filename> is your choice of names (for
	  example, Mychange.reg):
	
	        REGEDIT4
	
	        [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NetBT\Parameters]
	        "EnableLMHOSTS"=dword:00000000
	
	6. In the $OEM$ folder, create a file named Cmdlines.txt. This file should
	  contain the following entries, including the quotation marks surrounding the
	  entry
	
	        [Commands]
	        "Regedit.exe /s .\<filename>.reg"
	
	  where <filename> is the name of the registry file you created in the
	  previous step.
	
	7. Copy the Regedit.exe file from the share you created in step 1 to the $OEM$
	  folder.
	
	8. Run Windows NT 4.0 Setup in Unattended mode using the Unattend.txt file. For
	  example, use the following command
	
	  "winnt /u:unattend.txt /s:<sourcefiles>" (without the quotation marks)
	
	  where <sourcefiles> is the location of the shared folder you created in
	  step 1.
	
	For additional information about parameters for the Unattend.txt file, please see
	the following article in the Microsoft Knowledge Base:
	
	Q155197 Unattended Setup Parameters for Unattend.txt File
	
	Additional query words: unc tcpip wins Unattended Setup
	
	======================================================================
	Keywords          : kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
