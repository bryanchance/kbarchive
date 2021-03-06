---
layout: page
title: "Q124997: HP PC LAN Adapters Not Listed in Network Client Version 3.0"
permalink: /kb/124/Q124997/
---

## Q124997: HP PC LAN Adapters Not Listed in Network Client Version 3.0

{% raw %}

	Article: Q124997
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): winnt:3.0,3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.5 
	- Microsoft Network Client for MS-DOS version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to install the Hewlett-Packard (HP) PC LAN series adapter
	drivers in the Network Client version 3.0 for MS-DOS Setup program, they are not
	available in the list of network adapter drivers. These network adapter drivers
	are shipped with the network operating system and are located in the Windows NT
	Server version 3.5 CD.
	
	CAUSE
	=====
	
	This problem occurs because the HP PC LAN adapter drivers are commented out in
	the NETWORK.INF, SETUP.INF, WCNET.INF and WCSETUP.INF files. WCNET.INF and
	WCSETUP.INF files are pre-Setup files and NETWORK.INF and SETUP.INF are
	post-Setup files.
	
	RESOLUTION
	==========
	
	To correct this problem:
	
	1. If you have not installed Network Client version 3.0 for MS-DOS, modify the
	  WCSETUP.INF file. If you have already installed Network Client, modify the
	  SETUP.INF file. In the [netdrivers] section, remove the semicolon (;) in
	  front of each line and save the file(s):
	
	        ;1=,hplanb.dos,,hplanb.dos,
	        ;1=,hplanp.dos,,hplanp.dos,
	
	2. If you have not installed Network Client version 3.0 for MS-DOS, modify the
	  WCNET.INF file. If you have already installed Network Client, modify the
	  NETWORK.INF file. In the following sections, remove the semicolons (;) in
	  front of each line and save the file:
	
	  [netcard] Section
	  -----------------
	
	        ;ms$hp27250="HP PC LAN Adapter/8 TL (HP27250)", ...
	        ;ms$hp27245="HP PC LAN Adapter/8 TP (HP27245)", ...
	        ;ms$hp27247A="HP PC LAN Adapter/16 TP (HP27247A)", ...
	        ;ms$hp27252="HP PC LAN Adapter/16 TL Plus (HP27252)", ...
	        ;ms$hp27247B="HP PC LAN Adapter/16 TP Plus (HP27247B)", ...
	
	  [ms$HPLANB] Section
	  -------------------
	
	        ;[ms$HPLANB]
	        ;ndis2=1:hplanb.dos
	
	  [ms$hplanb_nif] Section
	  -----------------------
	
	        [ms$hplanb_nif]
	        ;drivername=HPLANB$
	        ;irq=interrupt,,text,"3,4,5,7,9,10,11",3,0x38
	        ;io=ioaddress,,text,"0x200,0x240,0x280,0x2C0,0x300, ...
	        ;param=maxhwtrans,"Maximum Hardware Transmit Packets", ...
	        ;param=maxswtrans,"Maximum Software Transmit Packets", ...
	        ;param=maxmulticast,"Maximum Multicast Addresses", ...
	        ;param=maxicnest,"Max Nesting of Indication Completes", ...
	
	  [ms$HPLANP] Section
	  -------------------
	
	        ;[ms$HPLANP]
	        ;ndis2=1:hplanp.dos
	
	  [ms$hplanp_nif] Section
	  -----------------------
	
	        ;[ms$hplanp_nif]
	        ;drivername=HPLANP$
	        ;irq=interrupt,,text,"3,4,5,7,9,10,11,12,15",3,0x30
	        ;io=ioaddress,,hex,"0x100,0x3A0,0x20",0x300,0x30
	        ;param=MemoryMappedBaseAddress,"Base Memory Address ...
	        ;param=maxhwtrans,"Maximum Hardware Transmit Packets", ...
	        ;param=maxswtrans,"Maximum Software Transmit Packets", ...
	        ;param=maxmulticast,"Maximum Multicast Addresses", ...
	        ;param=maxicnest,"Max Nesting of Indication Completes", ...
	        ;param=aui,"Use AUI Instead of Twisted Pair", text, ...
	
	MORE INFORMATION
	================
	
	HP PC LAN adapters are supported in LAN Manager version 2.x, Workgroup Add- On
	for MS-DOS version 3.11 and Network Client version 3.0 for MS-DOS. The following
	lists supported HP PC LAN adapters:
	
	  HP PC LAN Adapter/8 TL (HP27250)
	  HP PC LAN Adapter/8 TP (HP27245)
	  HP PC LAN Adapter/16 TP (HP27247A)
	  HP PC LAN Adapter/16 TL Plus (HP27252)
	  HP PC LAN Adapter/16 TP Plus (HP27247B)
	
	Additional query words: prodnt 3.00 wgao net
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search kbAudDeveloper kbZNotKeyword kbNetworkClientSearch kbNetworkClient300DOS
	Version           : winnt:3.0,3.5
	
	=============================================================================
	

{% endraw %}
