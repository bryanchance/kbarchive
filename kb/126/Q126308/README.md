---
layout: page
title: "Q126308: Problems Accessing Netware Server From a Windows NT RAS Client"
permalink: /kb/126/Q126308/
---

## Q126308: Problems Accessing Netware Server From a Windows NT RAS Client

{% raw %}

	Article: Q126308
	Product(s): Microsoft Windows NT
	Version(s): 3.5 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You may encounter problems when you attempt to establish a connection to a
	remote NetWare Server from a Windows NT Remote Access Service (RAS) client that
	is dialing into a Windows NT RAS Server. This problem will occur if the NetWare
	Server and the Windows NT RAS Server are on different network segments.
	
	To correct this problem, assign a unique IPX network number to the segment that
	the Windows NT RAS Server is located on. Alternatively, install the NetWare
	Server on the same network segment as the Windows NT RAS Server.
	
	MORE INFORMATION
	================
	
	Windows NT 3.5x
	---------------
	
	To assign a unique IPX network number to the network segment that the Windows NT
	RAS Server is located on, perform the following steps:
	
	1. Determine a unique IPX network number. That is one that does not conflict
	  with any previously assigned IPX network numbers.
	
	2. On the Windows NT RAS Server, choose Network in Control Panel.
	
	3. In the list of Installed Network Software, select NWLink IPX/SPX Compatible
	  Transport.
	
	4. Choose the Configure button.
	
	5. In the Adapter box, select the network card driver.
	
	6. Enter the unique IPX network number from Step 1 above into the Internal
	  Network Number box.
	
	7. Choose the OK button in both the NWLink IPX/SPX Protocol Configuration dialog
	  box and the Network Settings dialog box.
	
	8. Shutdown and restart Windows NT.
	
	Windows NT 4.0
	--------------
	
	In Windows NT version 4.0, you can change both the (external) network number and
	internal network number through the Graphic User Interface (GUI) in Control
	Panel. Use the following steps:
	
	To set or change the external network number:
	
	1. Click Start, point to Settings, and click Control Panel.
	
	2. Double-click Network, click Protocols, and double-click NWLink IPX/SPX
	  Compatible Transport.
	
	3. Select the appropriate adapter in the Adapter list and click the Manual Frame
	  Type Detection radio button.
	
	4. Click Add, select the correct frame type and type your unique (external)
	  network number.
	
	For additional information, please see the following article in the Microsoft
	Knowledge base:
	
	  Q150546: NWLink IPX/SPX: Network Number .vs. Internal Network Number
	
	NetWare is manufactured by Novell Inc., a vendor independent of Microsoft; we
	make no warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.5 4.0
	
	=============================================================================
	

{% endraw %}
