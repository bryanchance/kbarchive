---
layout: page
title: "Q69880: LAN Manager Troubleshooting Guide"
permalink: /kb/069/Q69880/
---

## Q69880: LAN Manager Troubleshooting Guide

{% raw %}

	Article: Q69880
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-FEB-2002
	
	SUMMARY
	=======
	
	
	This guide is a general starting place for resolution of common problems
	encountered when setting up LAN Manager for the first time or changing to a new
	configuration. Most problems or errors found with LAN Manager can be placed in
	one of the first three categories listed below. Common solutions for each
	category are listed at the end of this article.
	
	MORE INFORMATION
	================
	
	CATEGORIES
	----------
	
	a. Incorrect Hardware Configuration
	
	b. Incorrect Software Setup
	
	c. Lack of Server Resources (Software or Hardware)
	
	d. Other
	
	SIMPLE TESTS
	------------
	
	Four easy tests to narrow down the problem into one of these categories are:
	
	1. Check Server Error Log
	
	  Check the server error log for information on what might be causing a problem.
	  Most resource problems (e.g. lack of memory or disk space) will produce
	  errors in the log (category C).
	
	2. Net Send Test
	
	  This test checks the connection between the server and workstation. After
	  starting the server and a workstation, verify that you can send a message
	  from a workstation to the server (net send <computername> message). If
	  this test fails you may have an incorrect hardware configuration (category
	  A). This test is not applicable for DOS Basic workstations.
	
	3. Loopback Driver Test
	
	  This test will allow you to distinguish between hardware and software problems
	  on the server. It can only be used for errors in starting up the server or
	  services. This test does not work for connection problems between machines.
	
	  If appropriate, replace the specific card driver and protocol stack with the
	  "loopback driver" using the setup program. Reboot the server and attempt to
	  reproduce the problem. If you are still having the same error, the problem is
	  most likely related to the software (category B). If the problem goes away,
	  most likely it was a hardware configuration problem (category A).
	
	4. Diagnostic Programs
	
	  Use network card manufacturer's diagnostic programs to check for hardware
	  problems (category A).
	
	COMMON SOLUTIONS
	----------------
	
	a. Incorrect Hardware Configuration
	
	  1. Interrupt, I/O address, base address, or DMA channel conflicts may exist
	     between the network card and another device. Use a manual or a diagnostic
	     program to determine the current setting. Change the setting so that it is
	     different from other devices.
	
	  2. The physical network connection could be incomplete, or there is a problem
	     with the local network cable plant. Use diagnostic programs or equipment
	     to troubleshoot the local cable plant.
	
	  3. A memory conflict may exist. Since DOS LAN Manager is a memory-resident
	     program, it may be in conflict with other programs which stay resident in
	     memory. Check for TSRs or unneeded device drivers. Remove all unnecessary
	     lines in AUTOEXEC.BAT and CONFIG.SYS.
	
	b. Incorrect Software Setup
	
	  1. The MAC driver may not be configured correctly (etherlink II is an example
	     of a MAC driver). Check the section in the Network Device Driver Guide for
	     your driver. Verify that all of the parameters in protocol.ini match your
	     card configuration. Make sure the driver is listed as being compatible
	     with the card you are using.
	
	  2. Machines on the network may not be using the same protocol stack. Check to
	     make sure that the protocol stacks match on the two machines that are
	     trying to communicate (netbeui is an example of a protocol stack).
	
	  3. Inter-Process Communication (IPC$) may not be shared on the server. This
	     is a common problem for share-level security servers. IPC$ is
	     automatically shared for user-level security servers. Share IPC$ on the
	     server.
	
	c. Lack of Server Resources (Software or Hardware)
	
	  1. The server may run out of resources if too much cache is allocated. Adjust
	     the amount of cache allocated for the server in config.sys.
	
	  2. The server may run out of NetBIOS sessions, NCBs, or names. See p.19 of
	     the LAN Manager Network Device Driver Guide to adjust these parameters.
	
	  3. The server may not have enough physical memory. See p.7 of the
	     installation guide for memory requirements. Add memory to the server if
	     necessary.
	
	d. Other
	
	  1. Try going back to a configuration that is as generic as possible. Use the
	     setup program to save the configuration and only make necessary changes.
	     Otherwise, use the defaults.
	
	  2. Check the LAN Manager Manuals. The LAN Manager Administration Guide has
	     very good descriptions of how to set up your LAN. Chapter 4 on security is
	     particularly useful if you are having trouble setting up your server and
	     domain.
	
	Additional query words: 2.00 2.10 2.10a 2.20
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
