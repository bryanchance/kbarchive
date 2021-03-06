---
layout: page
title: "Q58330: Location of Enhanced Mode Temporary Swap Files"
permalink: /kb/058/Q58330/
---

## Q58330: Location of Enhanced Mode Temporary Swap Files

{% raw %}

	Article: Q58330
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The filename used for temporary virtual memory swap files under Microsoft
	Windows 3.0 enhanced mode is WIN386.SWP. The location to which paging occurs
	must meet the following parameters:
	
	- The directory must not have a DOS read-only attribute.
	
	- You must have create and write access if on a network.
	
	MORE INFORMATION
	================
	
	WIN386.SWP is created in a location determined by the following factors:
	
	- If no PagingDrive= setting is present in the SYSTEM.INI, the file is created
	  in the startup location of WIN.COM.
	
	  On a network, users should have their own copies of WIN.COM, SYSTEM.INI, and
	  WIN.INI in their own directories. Note that paging to a network drive, while
	  certainly possible, is extremely slow and is not recommended.
	
	- If a PagingDrive=<drive letter> setting is present in the [386Enh]
	  section of the SYSTEM.INI file, the swap file is created in the ROOT
	  directory of the specified drive. An example of setting the paging drive to a
	  local drive D: would be PagingDrive=D:
	
	  Note that on Novell networks, because they are not MS-NET redirector
	  compatible, the root of a network drive is the root of the server. DO NOT set
	  PagingDrive= to a Novell network drive. If you do so, and multiple users run
	  Windows 3.00 enhanced mode, they will crash because they will delete each
	  other's swap files, all created in the root directory of the server.
	
	  There is currently no way to specify a directory on the PagingDrive=
	  parameter.
	
	Additional query words: 3.00 3.0 3.0a 3.00a win30 winmem
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
