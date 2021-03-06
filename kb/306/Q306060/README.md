---
layout: page
title: "Q306060: XADM: Mailbox Manager Can't Notify Users After Cleaning Mailbox"
permalink: /kb/306/Q306060/
---

## Q306060: XADM: Mailbox Manager Can't Notify Users After Cleaning Mailbox

{% raw %}

	Article: Q306060
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): kbExchange550preSP5fix kbExchange550SP5Fea
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Mailbox Cleanup Agent (MBClean) may fail to properly
	notify users when it has cleaned their mailbox. This behavior can occur if
	MBClean's own mailbox is over the quota limit specified for the information
	store. This condition may also cause MBClean to prematurely stop cleaning
	mailboxes. The following two errors in the event log may indicate this problem:
	
	  Event Type: Error
	  Event Source: MSExchangeMCA
	  Event Category: None
	  Event ID: 706
	  Date: 6/26/2001
	  Time: 7:15:00 PM
	  User: N/A
	  Computer: SERVERNAME
	  Description:
	  Failed to process users in container /o=Organization/ou=Site/cn=Recipients.
	
	  Event Type: Error
	  Event Source: MSExchangeMCA
	  Event Category: None
	  Event ID: 721
	  Date: 6/26/2001
	  Time: 7:15:00 PM
	  User: N/A
	  Computer: SERVERNAME
	  Description:
	  Microsoft Exchange Server Mailbox Manager was interrupted before processing
	  was complete - error no = 80004005.The Microsoft Exchange Server Mailbox
	  Manager has completed processing mailboxes
	
	  Started at: 04/30/01 15:33:36
	  Completed at: 04/30/01 15:52:39
	  Mailboxes processed: 267
	  Messages moved: 532
	  Size of moved messages: 18.00 MB
	  Deleted messages: 17
	  Size of deleted messages: 52.00 KB
	
	CAUSE
	=====
	
	The MBClean mailbox has exceeded its mailbox size limit, as specified by the
	information store settings. When MBClean tries to submit a message to notify a
	user that their mailbox has been cleaned, the information store returns the
	error 0x4D9, which is ecQuotaExceeded. This error is returned as 0x80004005
	(MAPI_E_CALL_FAILED), which is logged in event 721 above.
	
	RESOLUTION
	==========
	
	To correct this behavior, MBClean has been modified to permanently delete any
	messages in its Inbox folder upon starting the service. Also, MBClean will set
	the incoming size limit for the mailbox to 0 to prevent any further messages
	from being delivered. The mailbox is also configured to not use the information
	store storage limit defaults.
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Exchange Server 5.5 service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: MBClean
	
	+---------------------------+
	| File name   | Version     | 
	+---------------------------+
	| Mbclean.exe | 5.5.2655.34 | 
	+---------------------------+
	
	NOTE: Due to file dependencies, this hotfix requires Microsoft Exchange Server
	version 5.5 Service Pack 4.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5.
	
	MORE INFORMATION
	================
	
	To determine if the MBClean mailbox is over its size limit:
	
	1. In the Microsoft Exchange Server 5.5. Administrator program, locate the
	  Mailbox Resources object under the Private Information Store object.
	
	2. Add the Storage Limits column to the view. For more information on how to
	  perform this step, please refer to the following article:
	
	  Q260184 XADM: How to Add Storage Limits Columns for Mailboxes
	
	3. Find the mailbox with the display name "Microsoft Exchange Server Mailbox
	  Manager for <ServerName>, where <ServerName> is the name of the
	  server on which MBClean is running.
	
	The Storage Limits column for this mailbox will display "Prohibit Send" or
	"Mailbox Disabled," depending on the information store storage limits that are
	configured. If either setting is displayed, MBClean may not correctly send
	status messages to the users to inform them that their mailbox was cleaned.
	
	Additional query words: mbxman mailbox manager
	
	======================================================================
	Keywords          : kbExchange550preSP5fix kbExchange550SP5Fea 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
