---
layout: page
title: "Q80001: WRQ Inc. Reflection Network Series and MS-DOS"
permalink: /kb/080/Q80001/
---

## Q80001: WRQ Inc. Reflection Network Series and MS-DOS

{% raw %}

	Article: Q80001
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Walker Richer & Quinn (WRQ) has confirmed that their Reflection Network
	Series version 1.11 and 2.0 products are compatible with MS-DOS versions 5.0 and
	later, but require certain caveats when loading the network software into upper
	memory using EMM386.EXE.
	
	
	MORE INFORMATION
	================
	
	The Reflection Network Series version 1.11 includes the following software:
	
	  The 3000 Connection - To HP3000 hosts
	  The LAT Connection - To DEC VAX hosts
	  The TCP Connection - To tcp/ip systems
	  The Telnet Connection - Works with third party tcp/ip stacks
	
	The Reflection Network Series (except Telnet Connection) use the multiprotocol
	Network Driver Interface Specification (NDIS) to allow simultaneous connection
	to hosts using different protocols. They normally require the following files
	loaded into the CONFIG.SYS file:
	
	  device=c:\wrqnet\protman.dos
	  device=c:\wrqnet\macwd.dos
	
	(the above line varies according to network card)
	
	  device=c:\wrqnet\wrqtcp.sys
	
	(LAT Connection does not use WRQTCP.SYS).
	
	The following should be included in the AUTOEXEC.BAT file:
	
	  c:\wrqnet\rndiseth /stacks:6
	  c:\wrqnet\rndiseth /u
	  c:\wrqnet\netbind
	  c:\wrqnet\rndiseth /stacks:6
	
	WRQ recommends you do the following when using MS-DOS 5.0 and later EMM386.EXE
	and their Reflection Network Series programs.
	
	1. PROTMAN.DOS MUST be loaded before HIMEM.SYS and EMM386.EXE in the CONFIG.SYS
	  file as follows:
	
	     device=[path]\protman.dos
	     device=[path]\himem.sys
	     device=[path]\emm386.exe
	
	2. In most circumstances, the device drivers can be loaded into the upper memory
	  area (UMA), but if there are problems, Walker Richer & Quinn recommends
	  loading them in conventional memory.
	
	3. Do NOT load RNDISETH high.
	
	4. NETBIND is not a terminate-and-stay-resident (TSR) program. It merely
	  performs a function then terminates, so there is no need to load it high.
	
	5. Make sure to exclude the range of memory used by the EtherNet card when
	  allocating upper memory. This is required when using the Western Digital card
	  in particular. The start of the range can be found in the PROTOCOL.INI with
	  the WRQ network directory. For example, if the network card was using 16K at
	  address memory segment CC00, EMM386.EXE would be installed as follows:
	
	     device=c:\dos\emm386.exe x=CC00-CFFF
	
	6. Edit the STARTNET.BAT file in the WRQ network directory to add LOADHIGH
	  statements to the network drivers.
	
	The products included here are manufactured by Walker Rich & Quinn, a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20 3rdparty
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
