---
layout: page
title: "Q147551: Serial Mouse Fails With CalComp Digitizer"
permalink: /kb/147/Q147551/
---

## Q147551: Serial Mouse Fails With CalComp Digitizer

{% raw %}

	Article: Q147551
	Product(s): Microsoft Windows NT
	Version(s): 3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you install the CalComp Wintab32 Digitizer Services and Driver version 3.2
	for Windows NT 3.51, a serial mouse does not work and the following system
	events are logged in the Event Viewer:
	
	  Event ID: 3
	  Source: Serial
	  Description: User configuration data for parameter COM2 overriding firmware
	  configuration data.
	
	  Event ID: 11
	  Source: Serial
	  Description: The hardware resources for COMx are already in use by another
	  device.
	
	  Event ID: 22
	  Source:Serial
	  Description: A conflict has been detected between two drivers which claimed
	  two overlapping Io port regions. Driver ccntdrv, with device
	  <\Device\PointerPort0.Translated>, claimed an IO port range with
	  starting address in data address 0x28 and 0x2c, and length in data address
	  0x30.
	
	  Event ID: 22
	  Source:Serial
	  Description: A conflict has been detected between two drivers which claimed
	  two overlapping Io port regions. Driver Serial, with device
	  <\Device\Serial1.Translated>, claimed an IO port range with starting
	  address in data address 0x28 and 0x2c, and length in data address 0x30.
	
	  Event ID: 24
	  Source: Serial
	  Description: A conflict has been detected between two drivers which claimed
	  equivalent IRQs. Driver CCNTDRV, with device
	  <\Device\PointerPort0.Translated>, claimed an interrupt with Level in
	  data address 0x28, vector in data address 0x2c and Affinity in data address
	  0x30.
	
	  Event ID: 24
	  Source: Serial
	  Description: A conflict has been detected between two drivers which claimed
	  equivalent IRQs. Driver Serial, with device
	  <\Device\Serial2.Translated>, claimed an interrupt with Level in data
	  address 0x28, vector in data address 0x2c and Affinity in data address 0x30.
	
	NOTE: The COM ports, IRQ and addresses in system events mentioned above will vary
	depending on the system configuration.
	
	RESOLUTION
	==========
	
	The system events that appear in the Event Viewer are by design.
	
	To correct the problem with the serial mouse:
	
	1. Make sure that the Calcomp Digitizer drivers are installed by following the
	  instructions included with the Calcomp drivers. Turn the digitizer power off
	  and verify that the digitizer tablet is properly connected to the computer.
	
	2. Verify that the settings of the serial mouse, the digitizer, and other
	  hardware peripherals. Make sure that each device is using a unique IRQ, COM
	  port and Base I/O port address. In Windows NT, run Control Panel Ports and
	  select the COM port. Click Settings and then click Advanced to view the IRQ
	  and Base I/O Port Address settings.
	
	If there are no resource conflicts, proceed to step 3. If you have detected
	resource conflicts (especially with the digitizer), contact Calcomp Technical
	Support at (800) 458-5888 and see the following articles in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q112584
	  TITLE : Error Messages Caused by Incorrect Serial Port Configuration
	
	  ARTICLE-ID: Q137584
	  TITLE : CalComp Digitizer Fails on Windows NT 3.51
	
	1. In Control Panel Devices, verify that Serial has started.
	
	2. In Control Panel Devices, select Sermouse and click Startup. For Startup
	  Type, select System. Click OK and quit Control Panel.
	
	3. Shut down and restart Windows NT.
	
	The third-party products discussed here are manufactured by Calcomp, a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: prodnt Cal Comp digitize
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : 3.51
	
	=============================================================================
	

{% endraw %}
