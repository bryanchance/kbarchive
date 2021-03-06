---
layout: page
title: "Q153617: Chgpass.exe May Cause Message &quot;Error Getting PDC Name&quot;"
permalink: /kb/153/Q153617/
---

## Q153617: Chgpass.exe May Cause Message &quot;Error Getting PDC Name&quot;

{% raw %}

	Article: Q153617
	Product(s): Microsoft Windows NT
	Version(s): 3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a NetWare client uses Microsoft Chgpass.exe to change or synchronize
	passwords on File and Print Services for NetWare (FPNW) and NetWare servers, the
	message "Error getting PDC name" is returned.
	
	CAUSE
	=====
	
	When the client gets a positive response for the object queries for the FPNWPDC
	or SYNCPDC properties, it tries to contact the PDC in the following response
	frame(s):
	
	- client -> server NCP Request: Read Property Value, Object Name = MS_WINNT,
	  Property Name = SYNCPDC
	
	- server -> client: the server only returns the PDC name (for example
	  EVEREST) NCP Reply: Read Property Value - Success
	
	- client -> server NCP Request: Read Property Value, Object Name = EVEREST,
	  Property Name = NET_ADDRESS
	
	- server-client: NCP Reply: Read Property Value - No such object
	
	Because the client couldn't get the MAC address of the DSMN PDC, Chgpass.exe
	returns the message "Error getting PDC name."
	
	WORKAROUND
	==========
	
	The incorrect name of the DSMN PDC was returned by the NetWare server. If the
	NetWare server returns incorrect information, delete the WINNT_SYNC_AGENT user
	account from the NetWare server and add this NetWare server to your DSMN domain
	(using DSMN Synchronization Manager). This way the correct information will be
	written to the NetWare bindery.
	
	For more information on adding a NetWare server to your DSMN domain, see Chapter
	2 ("Adding a NetWare Server to Be Managed in a Domain") in the Administrator's
	Guide for Directory Service Manager for NetWare.
	
	Be aware that a NetWare server will continue to answer the client's CHGPASS
	question regardless of whether it is a DSMN- added NetWare server (NCP Request:
	Read Property Value, Object Name = MS_WINNT, Property Name = SYNCPDC). Also be
	aware that if this NetWare server wasn't properly deleted using the DSMN
	Synchronization Manager, it will return the original DSMN domain and PDC name.
	If this happens, use the NetWare utility Setpass.exe to change the password on
	the NetWare server, because this utility doesn't check for DSMN functionality.
	
	MORE INFORMATION
	================
	
	If Microsoft Chgpass.exe is involved, the following will happen:
	
	1. The client opens Chgpass.exe on an FPNW server and reads the .exe file:
	
	  NCP Request: File Open PUBLIC\CHGPASS.EXE
	  NCP Request: File Read
	  NCP Request: Burst Read: 22,840 bytes
	
	There are two situations in which the behavior of Chgpass.exe is different from
	that of NetWare Setpass.exe: with an FPNW server and with a NetWare server
	managed by Directory Service Manager for NetWare (DSMN).
	
	2. The client checks to see if the servers it is attached to are real NetWare
	  servers or FPNW servers. An FPNW server will return the domain and primary
	  domain controller (PDC) name.
	
	  NCP Request: Read Property Value, Object Name = MS_EXTENDED_NCPS, Property
	  Name = FPNWPDC
	
	  An FPNW server will respond with the PDC and domain name of the account
	  domain.
	
	3. The client asks the FPNW server for the MAC address of the PDC, and the
	  server returns the address.
	
	  NCP Request: Read Property Value, Object Name = Name_of_PDC, Property Name =
	  NET_ADDRESS
	
	4. The client connects via remote procedure call (RPC) over SPX to the PDC and
	  changes the password. Before this happens, you will see in the trace that the
	  client reads an RPC module:
	
	  Request: File Open PUBLIC\RPC16C6.RPC
	
	5. If the response to the request in item 2 is negative, the client checks to
	  see if the server it is attached to is a NetWare server that is part of a
	  DSMN domain:
	
	  NCP Request: Read Property Value, Object Name = MS_WINNT, Property Name =
	  SYNCPDC
	
	  The PDC name returned is from the domain that added this NetWare server to the
	  DSMN Synchronization Manager. The WINNT_SYNC_AGENT NetWare user account that
	  is created when DSMN Synchronization Manager is installed on Windows NT is an
	  indication that the NetWare server is managed by DSMN and that it will
	  respond to this request.
	
	  If the NetWare server is neither an FPNW server nor a DSMN- added server, it
	  will answer both Read Property Value requests with "no such object," causing
	  the NetWare client to change the password directly on this NetWare server as
	  Setpass.exe from Novell would do.
	
	6. The client asks the NetWare server for the MAC address of the PDC and the
	  server returns the address.
	
	  NCP Request: Read Property Value, Object Name = Name_of_PDC, Property Name =
	  NET_ADDRESS
	
	7. The password of the user is changed on the PDC of the DSMN domain the same
	  way as with the FPNW server. The PDC will replicate the change to its backup
	  domain controllers (BDCs) and the NetWare servers listed in the DSMN
	  administrator tool.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT versions 3.51 and
	4.0. We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : :3.51,4.0
	
	=============================================================================
	

{% endraw %}
