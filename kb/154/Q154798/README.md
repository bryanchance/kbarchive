---
layout: page
title: "Q154798: XFOR: SMTP Mail Attachments not Visible in PC Mail 3.x Clients"
permalink: /kb/154/Q154798/
---

## Q154798: XFOR: SMTP Mail Attachments not Visible in PC Mail 3.x Clients

{% raw %}

	Article: Q154798
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:3.0,3.2,3.2a,3.5; winnt:4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 02-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	- Microsoft Mail for PC Networks, versions 3.0, 3.2, 3.2a, 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An external user sends a mail message with an attachment over the Internet and a
	Microsoft Exchange Server's Internet Mail Connector (IMC) receives the message.
	The IMC then hands off the message to the MS Mail Connector (MSMI) which
	forwards the message to an MS Mail for PC Networks Postoffice. The PC Mail 3.x
	Windows client picks up the message and displays it in the user's Inbox with a
	paper-clip indicating an attachment. When the user opens the message, they don't
	see the attachment. If they forward the message, the attachment appears and can
	be viewed.
	
	
	WORKAROUND
	==========
	
	The attachment appears if it is sent to a user on a Microsoft Exchange Server.
	It also appears in PC Mail DOS clients and Microsoft Exchange clients running
	against the PC Mail 3.x Postoffice.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. This problem was corrected in the latest Microsoft Exchange Service
	Pack. For information on obtaining the Service Pack, query on the following word
	in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2 kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN320a kbMailPCN300 kbMailPCN350
	Version           : WINDOWS:3.0,3.2,3.2a,3.5; winnt:4.0
	
	=============================================================================
	

{% endraw %}
