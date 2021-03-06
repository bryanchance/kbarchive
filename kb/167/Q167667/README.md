---
layout: page
title: "Q167667: SNA Server Rejects LU6.2 BIND over 2nd Connection"
permalink: /kb/167/Q167667/
---

## Q167667: SNA Server Rejects LU6.2 BIND over 2nd Connection

{% raw %}

	Article: Q167667
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If SNA Server 3.0 is configured with more than one connection to a remote
	system, and that remote system attempts to serially activate an LU6.2 session
	using the same Local APPC LU /Remote APPC LU /APPC Mode name combination over
	each connection, the BIND over the first connection succeeds, but the BIND over
	the second connection is rejected by SNA Server with sense code = 083500xx,
	unless the SNA Server service is stopped and started.
	
	SNA Server will log the following event when sending the negative response to the
	BIND arriving over the second connection:
	
	  Event ID: 17
	  Source: SNA Server
	  Description:
	  APPC session activation failure: BIND negative response sent
	
	  Sense data = 083500xx (where xx may be any value)
	
	CAUSE
	=====
	
	When SNA Server 3.0 accepts an LU6.2 BIND over a connection, the LU/LU/mode
	partnership is cached in SNA Server for that connection. After the session ends,
	SNA Server then rejects an LU6.2 BIND for this same LU/LU/mode partnership
	received over a different connection, because SNA Server already has a
	partnership defined over the first connection.
	
	This problem did not exist in SNA Server 2.x, because the SNA Server
	Administrator program prevented the configuration of the same LU/LU/mode
	partnership over different connections owned by the same server. However, with
	SNA Server 3.0, no explicit APPC LU partnerships are defined, so this allows SNA
	Server to encounter this condition.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0 and 3.0
	Service Pack 1 (SP1). This problem was corrected in the latest SNA Server
	version 3.0 U.S. Service Pack. For information on obtaining this Service Pack,
	query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	With the hotfix applied, SNA Server will accept a BIND for a specific LU/LU/mode
	pairing over a connection even after the same LU/LU/mode session had previously
	been active over a different connection. Note that SNA Server does not support
	concurrent bound sessions using the same LU/LU/mode names over different
	connections.
	
	When a BIND arrives for a Mode that is already partnered over another connection,
	SNA Server now checks the state of the partnered connection before failing the
	BIND. If the other connection is not active, SNA Server now points the
	partnership at the new connection (since the remote LU is obviously on this new
	connection now). It would continue to reject the BIND if the first connection is
	active, since it is definitely not legal to have the partnerships over two
	connections active at the same time.
	
	NOTE: With this update applied, a separate problem occurs in SNA Manager; the
	APPC LU status information is not displayed properly when the LU-LU session is
	established over the alternate connection. This problem is only a cosmetic
	issue. This SNA Manager problem will be corrected in a future SNA Server 3.0
	service pack.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:3.0,3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
