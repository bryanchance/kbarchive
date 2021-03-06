---
layout: page
title: "Q179441: XCLN: Exchange Server Slows with Message Stuck in User Mailbox"
permalink: /kb/179/Q179441/
---

## Q179441: XCLN: Exchange Server Slows with Message Stuck in User Mailbox

{% raw %}

	Article: Q179441
	Product(s): Microsoft Exchange
	Version(s): MACINTOSH:8.0; WINDOWS:4.0,5.0,5.5,8.0; :8.0,8.01,8.02,8.03
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0, 5.5 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0, 5.5 
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0, 5.5 
	- Microsoft Exchange Macintosh client, versions 4.0, 5.0, 5.5 
	- Microsoft Outlook, Exchange Server Edition, version 8.0, used with:
	   - the operating system: Microsoft Windows versions 3.1, 3.11 
	- Microsoft Outlook for Macintosh, Exchange Server Edition, version 8.0 
	- Microsoft Outlook 97, versions 8.0, 8.01, 8.02, 8.03 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Exchange Server computer becomes very sluggish. If your are working at the
	console on the server, you notice the slowness. Clients sending or receiving
	messages also notice a slowdown.
	
	Additional indicators of the problem covered in this article:
	
	1. Store.exe is between 75% and 100% processor utilization.
	
	2. The Performance Monitor counter Write Bytes RPC Clients/sec under the
	  MSExchangeIS object stays at a high number (a rate of around 100,000 or
	  above).
	
	3. A network trace shows that the network segment is saturated. Most of the
	  traffic will be RPC (remote procedure calls).
	
	4. Go to the Private Information Store properties Logons tab. Add the Total Ops
	  column. There will be users with 300 to 400 sustained Total Ops.
	
	CAUSE
	=====
	
	Some of the Exchange clients have a hung message on the server. When the user
	logs on to Exchange, the MAPI spooler on the client constantly tries to pull
	this message down. This problem does not prevent other messages from flowing to
	the client computer. When 20 to 30 users on the Exchange Server computer are in
	the same condition with the hung message, this will consume most of the Exchange
	Server computer's resources.
	
	
	WORKAROUND
	==========
	
	To work around this problem, do the following:
	
	1. Go to the Private Information Store properties, Logons tab.
	
	2. Add the Total Ops column and look at the result. Users having 300 to 400
	  sustained Total Ops are the users causing the problem.
	
	3. After the users have been located, go to each user's computer. Open the
	  e-mail client and look in the user's server mailbox. There should be a
	  message there that cannot be pulled to the user's local PST. Delete that
	  message. You must do this for all users with a high Total Ops count.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Exchange and Outlook clients
	listed above. A supported fix is now available, but has not been fully
	regression-tested and should be applied only to systems experiencing this
	specific problem. Unless you are severely impacted by this specific problem,
	Microsoft recommends that you wait for the next Service Pack that contains this
	fix. Contact Microsoft Technical Support for more information.
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Additional query words: sluggish hung hanging prodnt
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbHWMAC kbOSMAC kbOutlookSearch kbExchangeSearch kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3
	Version           : MACINTOSH:8.0; WINDOWS:4.0,5.0,5.5,8.0; :8.0,8.01,8.02,8.03
	Hardware          : ALPHA PPC x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
