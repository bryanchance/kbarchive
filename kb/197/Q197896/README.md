---
layout: page
title: "Q197896: Uptomp.exe Requires Access to the Txtsetup.sif File"
permalink: /kb/197/Q197896/
---

## Q197896: Uptomp.exe Requires Access to the Txtsetup.sif File

{% raw %}

	Article: Q197896
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-FEB-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Windows NT Server 4.0 Resource Kit includes a utility called Uptomp.exe.
	This utility allows users to upgrade from a single processor system to a
	multiprocessor system without reinstalling the base Windows NT operating
	system.
	
	An updated .inf file (Uptomp.inf) for Uptomp.exe has been posted to Microsoft's
	FTP site:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/reskit/nt40/uptomp
	
	This updated Uptomp.inf file needs to replace the one that ships with the
	Resource Kit. Copy the updated Uptomp.inf file from the FTP server to the same
	directory as the Uptomp.exe program. The Uptomp.exe program also requires access
	to a file called Txtsetup.sif. This article describes steps to properly
	configure a computer to run Uptomp.exe so that all files are in the correct
	directory.
	
	MORE INFORMATION
	================
	
	After placing the updated Uptomp.inf file in the same directory as the
	Uptomp.exe program, it is necessary to find and copy the Txtsetup.sif file to
	the same directory as well.
	
	The Txtsetup.sif file is needed to display the names and descriptions of the
	different hardware abstraction layers (HALs) available under Windows NT Server.
	This file is accessed when Uptomp.exe searches for a list of HALs prior to
	upgrading the computer.
	
	The Txtsetup.sif file is located under the I386 folder or the Alpha folder on the
	Windows NT installation media. This file needs to be copied to both the folder
	containing Service Pack 3 files (for the appropriate platform) and the directory
	containing the Uptommp.exe program.
	
	After this file is copied, you can proceed to run Uptomp.exe to upgrade from a
	single processor to multiprocessor system.
	
	Uptomp.exe will produce the following dialog box:
	
	  Verify the path to the new Multiprocessor HAL DLL files and select the
	  correct HAL for this machine, then collect OK to continue.
	
	Point the Uptomp.exe application to the folder of the latest service pack you are
	running. For example, if you are running Windows NT Server 4.0, Service Pack 4,
	point the UPTOMP utility to read the list of HALs from the Service Pack 4
	installation folder. This folder will need to be copied to a hard drive to place
	the Txtsetup.sif file in the installation folder.
	
	After this is completed, Uptomp.exe will copy the necessary files and prompt the
	user to restart.
	
	Please note that Microsoft does not directly support the development of the
	Windows NT Resource Kit utilities. It is highly recommended that a complete
	backup of the system be performed prior to attempting the steps outlined in this
	article.
	
	REFERENCES
	==========
	
	For more detailed information on which files are replaced when performing a
	single processor to multi processor upgrade, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q156358 How to Manually Add Support for a Second Processor
	
	Additional query words: processor upgrade mutli uni multi-processor
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400xsearch kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400xsearch kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
