---
layout: page
title: "Q198393: XFOR: MS Mail Connector May Stop with Error 2380"
permalink: /kb/198/Q198393/
---

## Q198393: XFOR: MS Mail Connector May Stop with Error 2380

{% raw %}

	Article: Q198393
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Mail Connector may stop in irregular intervals with an error
	message similar to the following:
	
	  Event ID: 2380
	  Source: MSExchangeMSMI
	  Description: A memory access violation has occurred that prevents further
	  processing of a message. The access violation that occurred is an attempt to
	  read from 0x480df78. Please refer to the immediately following event(s)
	  logged by MS Mail Connector Interchange for more information on the message
	  that could not be processed. (Exception address: 0x4496c2.)
	
	This message may be followed by an Event 10003:
	
	  Event ID: 10003
	  Source: MSExchangeMSMI
	  Description: Fatal Error: File SFSEMS.CPP, line 878
	  Mailer Thread failed.
	
	In addition, when trying to restart the service, the following error message may
	be displayed:
	
	  Internal Windows NT Error 2140
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Microsoft Mail Connector
	
	  File Name   Version
	  ----------------------
	  Mt.exe      5.5.2524.0
	  Mtmsg.dll   5.5.2524.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : 5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
