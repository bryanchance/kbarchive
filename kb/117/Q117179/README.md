---
layout: page
title: "Q117179: Running WFWG TCP/IP (WFWTCP) with Workgroup Add-On for MS-DOS"
permalink: /kb/117/Q117179/
---

## Q117179: Running WFWG TCP/IP (WFWTCP) with Workgroup Add-On for MS-DOS

{% raw %}

	Article: Q117179
	Product(s): Microsoft Access Distribution Kit
	Version(s): MS-DOS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Workgroup Add-On for MS-DOS, version 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The real-mode Microsoft TCP/IP protocol (WFWTCP) was designed to allow TCP/IP
	services for Windows for Workgroups. However, you can use the steps below to
	successfully install WFWTCP on a Workgroup Add-On for MS-DOS installation.
	
	For information about obtaining the WFWTCP files, query on the following words in
	the Microsoft Knowledge Base:
	
	  wfwtcp and tcp/ip and obtain
	
	
	MORE INFORMATION
	================
	
	1. Run Setup from the Workgroups Add-On for MS-DOS directory.
	
	2. Choose Change Network Configuration and then Add Protocol. Select Other
	  Protocol and provide the path to the expanded WFWTCP files.
	
	3. Follow the prompts to install the protocol and then reboot the machine. If
	  you are running MS-DOS 6.0 or 6.2, choose the F5 key when the "Starting
	  MS-DOS..." prompt appears to prevent loading any files in the CONFIG.SYS and
	  AUTOEXEC.BAT files. If you are running a version of MS-DOS earlier than 6.0,
	  perform a clean boot, loading COMMAND.COM only.
	
	4. The WFWTCP installation creates the following default setup in the
	  PROTOCOL.INI file:
	
	     [TCPIP]
	     BINDINGS=(Network interface card [NIC] driver)
	     LANABASE=(First free LANA)
	
	  Use a text editor to modify this section using the following example:
	
	     [TCPIP]
	     DefaultGateway0=(Whatever is assigned to this gateway)
	     SubNetMask0=(Your default setting)
	     IPAddress0=(IP Address assigned to this machine)
	     NBSessions=6 (6 is the default setting)
	     NetFiles=(Path for the WFWTCP files)
	     DriverName=TCPIP$
	     BINDINGS=(NIC driver, for example, BINDINGS=MS$EE16 for the Intel
	              EtherExpress 16 network card)
	     LANABASE=0 (Zero if TCP/IP is set as the default protocol; it can be
	                1, 2, and so forth if TCP/IP is installed as an additional
	                protocol.)
	
	5. Restore the original CONFIG.SYS and AUTOEXEC.BAT files and then reboot your
	  system again. TCP/IP should now be successfully installed.
	
	NOTE: when using the net start command, the following error message occurs if a
	period is included in an IP address. Use the space character instead of the
	period character in an IP address.
	
	  PRO0008E Invalid Decimal Digit in PROTOCOL.INI file
	
	Additional query words: wgao ping dos level protocol
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311DOS
	Version           : MS-DOS:3.11
	
	=============================================================================
	

{% endraw %}
