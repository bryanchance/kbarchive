---
layout: page
title: "Q112991: Printer Pools under Windows NT"
permalink: /kb/112/Q112991/
---

## Q112991: Printer Pools under Windows NT

{% raw %}

	Article: Q112991
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 3.51
	Operating System(s): 
	Keyword(s): kbprint kbPrinting
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows NT allows you to create a pool of printing devices on a print server and
	make them appear as one printing device. This type of setup might be used in a
	high-volume environment where it is not practical to have to wait long periods
	of time for an individual print job. Keep in mind that under Windows NT, a
	printer is a software interface between an application and a printing device,
	and the instrument that prints is referred to as a printing device.
	
	MORE INFORMATION
	================
	
	When a printer pool is created, multiple printing devices are connected to a
	single print server and behave as a single printing device. When a document is
	printed by a user, the first available printing device in the printer pool
	prints the job. The printing devices in the pool should be identical to ensure
	printing consistency.
	
	To create a printer pool:
	
	1. From the Print Manager window, choose the Printers icon or the printer window
	  for the printer you want to create a pool with.
	
	2. From the Printer menu, choose Properties.
	
	3. In the Printer Properties dialog box, choose the Details button.
	
	4. In the Printer Details dialog box, select port names from the Print To
	  Additional Ports dialog box that correspond to the ports where you have
	  connected printers.
	
	To add (or change) the port name:
	
	1. In the Printer Properties dialog box, select Network Printer in the Print To
	  dialog box.
	
	2. In the Print Destinations dialog box, select Local Port.
	
	3. Type the name of the port you want to add in the Enter A Port Name dialog box
	  (this can include redirected ports to shared printers), and then choose the
	  OK button. (This is when the administrator should assign unique, descriptive
	  names.)
	
	After the printer pool is set up, it appears to the users as a single printing
	device. The owner of the printer pool should specify unique port names for each
	printing device because this is the only indicator to the user which printing
	device a print job is being printed to.
	
	A printer pool is most useful if all of the printing devices are in the same
	geographic location. If the user has to wander around from location to location
	to find a print job, a printer pool is probably not a good use of available
	resources.
	
	Because the user never knows which printing device in the pool will print a
	particular job, it does not make sense to have different types or models of
	printers pooled together. Even something as simple as a different default print
	tray or less RAM in one printing device in the pool may have adverse effects on
	a particular print job.
	
	When you define a printer pool, it is best to define the fastest printing device
	first because the print spooler checks the available sources in the order they
	were created.
	
	Additional query words: prodnt spool printpool
	======================================================================
	Keywords          : kbprint kbPrinting 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1 3.5 3.51
	
	=============================================================================
	

{% endraw %}
