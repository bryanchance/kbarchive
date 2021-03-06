---
layout: page
title: "Q189188: SMS: Miperf.bat - Add MIF File Counters to Performance Monitor"
permalink: /kb/189/Q189188/
---

## Q189188: SMS: Miperf.bat - Add MIF File Counters to Performance Monitor

{% raw %}

	Article: Q189188
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsmsUtil smsutil
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Miperf.bat, a utility that is available in the Microsoft BackOffice Resource
	Kit, adds a new set of counters to Performance Monitor. These counters monitor
	the number of MIF files being processed by the Dataloader. The name of the new
	Performance Monitor object is SMS_MIFS. For a definition of the counters, see
	the Explain text in Performance Monitor. MIPERF must be run on the computer that
	is running the Systems Management Server site services.
	
	MORE INFORMATION
	================
	
	Usage Notes
	-----------
	
	The New MIFs counter can only be displayed by using the Performance Monitor in
	Windows NT Server or Windows NT Workstation, version 4.0 or later. Total MIFs
	counter works with any Performance Monitor.
	
	The Total MIFs value is stored once per server, which means that when you first
	open a counter for Total MIFs, it starts at 0 and counts up. If you start a
	second instance of Performance Monitor, it starts with the number that was last
	shown in the first instance of Performance Monitor. If you close all instances
	of Performance Monitor and then start the Total MIFs counter, it starts at 0
	again.
	
	The counters work by reading the log file. If you turn off tracing for the
	Dataloader, the counters no longer work.
	
	Some MIF files (such as User Group MIF files) contain multiple MIF files per
	file; that is, if you have 100 user groups, the Dataloader reports 100 machines
	processed while it processes this MIF file. The counter then shows this as 100
	MIF files processed.
	
	Despite these limitations, this counter presents a reasonable view of the
	performance of the Dataloader if it is used over a several day period.
	
	Removing MIPERF
	---------------
	
	To remove this software, run the following command:
	
	     unlodctr SMS_Mifs
	
	Unlodctr is provided with Windows NT Server.
	
	NOTE: Do not simply delete the registry keys. Doing so may cause you to lose
	other Performance Monitor counters.
	
	Runs on Alpha, MIPS, and x86.
	
	Files Required for MIPERF
	-------------------------
	
	  Miperf.dll
	  Smsperf.dll
	
	The following files are required to install the SMS_MIFS counter, but can safely
	be removed after installation:
	
	  Miperf.bat
	  Mictrnm.h
	  Mi.ini
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsmsUtil smsutil 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
