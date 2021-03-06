---
layout: page
title: "Q169143: XCON: MTA Event 9221 A Sockets Err 10054 on a WSARecvEx() Call"
permalink: /kb/169/Q169143/
---

## Q169143: XCON: MTA Event 9221 A Sockets Err 10054 on a WSARecvEx() Call

{% raw %}

	Article: Q169143
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You may encounter a MSExchangeMTA Event 9221 in the Windows NT Application Log
	that contains a sockets error 10054 similar to the following example:
	
	  Event ID: 9221
	  Source:   MSExchangeMTA
	  Type:     Warning
	  Category: Operating System
	
	A sockets error 10054 on a WSARecvEx() call was detected. The message transfer
	agent (MTA) will attempt to recover the sockets connection. Control block index:
	1. [BASE IL TCP/IP DRVR 10 262] (12)
	
	MORE INFORMATION
	================
	
	A 10054 socket error in this context is not an indication of a problem, but is
	currently known and expected behavior. It happens any time a WinSock connection
	is closed down (TCP/IP or TP4, whether clean or dirty). Although this event by
	itself may be confusing, it is not harmful.
	
	Winsock Error code 10054 (WSAECONNRESET) indicates a "Connection reset by peer."
	for a list of Winsock error codes, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q150537 Windows Sockets Error Codes, Values, and Meaning
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
