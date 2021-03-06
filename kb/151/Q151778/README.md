---
layout: page
title: "Q151778: Huge Downlevel Print Job Causes File Cache to Grow"
permalink: /kb/151/Q151778/
---

## Q151778: Huge Downlevel Print Job Causes File Cache to Grow

{% raw %}

	Article: Q151778
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbprint kbWinNT400sp4fix kbPrinting
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When a downlevel client sends a huge print job to a Windows NT printer shared on
	the Microsoft Windows Network, the file cache on the server grows near to the
	size of physical memory.
	
	NOTE: Downlevel clients include LAN Manager 2.x clients for MS-DOS and OS/2,
	MS-DOS Microsoft Network Client 3.0, Windows for Workgroups 3.x, and Windows 95.
	A Windows NT computer can also be a downlevel client when it has a local driver
	installed and prints to the printer share.
	
	If you examine performance counters while this happens, you notice the counter
	for the file cache (Memory: Cache Bytes) is very high while the process working
	sets decline (Process: Working Set, instance _Total).
	
	CAUSE
	=====
	
	When the server service opens downlevel spool files it does not use the flag
	FILE_FLAG_SEQUENTIAL_SCAN. Therefore, Cache Manager increases the file cache
	when data is read or written since it expects the application to need it again.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	Additional query words: 4.00 prodnt
	
	======================================================================
	Keywords          : kbprint kbWinNT400sp4fix kbPrinting 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
