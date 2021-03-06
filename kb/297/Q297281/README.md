---
layout: page
title: "Q297281: XADM: Out of Office Message Is Not Sent"
permalink: /kb/297/Q297281/
---

## Q297281: XADM: Out of Office Message Is Not Sent

{% raw %}

	Article: Q297281
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you send an e-mail message to a mailbox that has the Out Of Office
	Assistant functionality enabled, the Out Of Office Assistant does not send an
	Out Of Office reply. This issue occurs with messages that originate both
	internally and externally.
	
	CAUSE
	=====
	
	This issue can occur if the mailbox has an alternate recipient configured on the
	server and the "Deliver messages to both recipient and alternate recipient"
	option is not selected. In this scenario, the incoming message does not arrive
	in the recipients mailbox, and the Out Of Office Assistant is not initiated.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q248456 XADM: Out Of Office Assistant Does Not Start If a Rule Is Set to Stop
	  Processing Other Rules
	
	RESOLUTION
	==========
	
	To resolve this issue:
	
	1. Click Start, point to Programs, click Microsoft Exchange, and then click
	  Microsoft Exchange Administrator.
	
	2. Open the properties for the mailbox that has the alternate recipient
	  configured.
	
	3. Click the Delivery Options tab.
	
	4. Click "Deliver messages to both recipient and alternate recipient".
	
	5. Click Apply, and then click OK.
	
	WORKAROUND
	==========
	
	If you do not want the incoming messages to be stored in your mailbox, you can
	replace Out Of Office Assistant and alternate recipient message forwarding with
	traditional client-side rules. In this case, if you remove the Alternate
	Recipient setting from the mailbox on the server, all message forwarding is
	handled through rules on the client. Configure one rule to send the Out Of
	Office notification, and a second rule to forward the message to the alternate
	recipient.
	
	For additional information about how to initiate the Out Of Office Assistant,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q260987 OL2000: (CW) How to Emulate the Out Of Office Assistant
	
	  Q248830 OL2000: (IMO) How to Emulate the Out Of Office Assistant
	
	  Q196212 OL2000: How to Use the Rules Wizard in Outlook 2000
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q255697 XADM: How to Forward E-mail Messages from an Exchange Mailbox to a
	  POP3 Address
	
	  Q157961 XCLN: Out Of Office Reply Sent Only Once
	
	
	Additional query words: sbs outlook ooa oof o2000
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
