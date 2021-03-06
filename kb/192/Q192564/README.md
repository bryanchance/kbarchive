---
layout: page
title: "Q192564: INFO: Set Winsock Control RemoteHost and RemotePort for UDP"
permalink: /kb/192/Q192564/
---

## Q192564: INFO: Set Winsock Control RemoteHost and RemotePort for UDP

{% raw %}

	Article: Q192564
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbGrpDSVB
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When a UDP message is received by a Winsock control, the RemoteHostIP property
	is set to the IP address of the remote machine, and the RemotePort property is
	set to the IP port of the remote UDP application. The previous properties values
	are overwritten.
	
	This could create a problem if the user was not expecting data on that port from
	a different RemoteHostIP. Attempts to call the SendData method without setting
	these two properties to the appropriate values might send the data to an
	unplanned recipient.
	
	Whenever a UDP socket is being used, you should always reset the RemoteHostIP and
	RemotePort properties to your own known values before calling the SendData
	method.
	
	MORE INFORMATION
	================
	
	This is by design. At the Winsock layer, the sendto API requires a sockaddr
	structure of the remote UDP peer to send the message to, and the recvfrom API
	always gets a sockaddr structure for the remote UDP peer. The Winsock control
	internally uses the same sockaddr structure in both sendto and recvfrom API. As
	UDP is a connectionless protocol, it is possible that one UDP peer could receive
	a UDP message from a third machine unexpectedly. Therefore, it is important to
	reset the RemoteHostIP and RemotePort properties to your own known values before
	calling the SendData method.
	
	Additional query words: kbVBp500 kbCtrl kbNetGrp kbNetwork kbWinsock kbNTOS400 kbWinOS95 kbWinOS98 kbAPI kbdss kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbVBp500 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB500
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
