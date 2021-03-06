---
layout: page
title: "Q137723: NET2182 and NET3546 Errors Appear After LAN Manager 2.2c Setup"
permalink: /kb/137/Q137723/
---

## Q137723: NET2182 and NET3546 Errors Appear After LAN Manager 2.2c Setup

{% raw %}

	Article: Q137723
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- Microsoft LAN Manager, version 2.2c 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you successfully install LAN Manager 2.2c client software from the Windows
	NT Server 3.5 or 3.51 compact disc and restart the client computer, the
	following two error messages appear:
	
	  NET2182: The workstation has already been started
	
	  NET3546: Error running C:\LANMAN.DOS\NETPROG\NETWKSTA.EXE
	
	Whether or not this error occurs depends on your computer configuration.
	
	The protocol installed during LAN Manager Setup may bind successfully to the
	network interface card (NIC) driver, but the NET START WORKSTATION command in
	AUTOEXEC.BAT fails with the following message:
	
	  The WORKSTATION service is not started.
	  Is it OK to start it? (Y/N) [Y]:
	
	If you answer Yes, the error messages above appear again.
	
	
	CAUSE
	=====
	
	The LAN Manager 2.2c client Setup program in the \CLIENTS\LANMAN\DISKS directory
	on the Windows NT Server 3.5 and 3.51 compact disc places the NET START
	WORKSTATION statement at the end of the AUTOEXEC.BAT file. This causes problems
	with the Microsoft CD-ROM Extension (MSCDEX.EXE) file because it is not
	network-aware.
	
	RESOLUTION
	==========
	
	To correct this problem:
	
	1. Use a text editor to modify the client computer's AUTOEXEC.BAT.
	
	2. Place the MSCDEX.EXE line after the NET START WORKSTATION line.
	
	3. Save AUTOEXEC.BAT and quit the editor.
	
	4. Reboot the client computer.
	
	Additional query words: prodnt 2.20c disk
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbLanManSearch kbLanMan220c
	
	=============================================================================
	

{% endraw %}
