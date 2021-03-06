---
layout: page
title: "Q253557: XCLN: Outlook (CW) Meeting Request Going to Someone Else"
permalink: /kb/253/Q253557/
---

## Q253557: XCLN: Outlook (CW) Meeting Request Going to Someone Else

{% raw %}

	Article: Q253557
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 2000 
	- Microsoft Outlook 98 
	- Microsoft Outlook 97 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	NOTE: These procedures only apply if you have installed Outlook with 
	the Corporate or Workgroup option. This option allows you to use Messaging 
	Application Programming Interface (MAPI) services. To determine your 
	installation type, on the Help menu, click About Microsoft Outlook. In About 
	Microsoft Outlook, you should see "Corporate or Workgroup" if you have the 
	Corporate or Workgroup installation.
	
	SYMPTOMS
	========
	
	If you specify a delegate and later remove that delegate, the former delegate
	continues to receive meeting requests and responses as if the former delegate is
	still a delegate.
	
	The former delegate is either not listed in the Outlook client, or is listed as a
	user and repeatedly receives meeting requests and responses that are intended
	for someone else.
	
	CAUSE
	=====
	
	This problem occurs because the delegate is represented by a rule that is hidden
	in the mailbox. The delegate rule is "stranded" in the information store.
	
	RESOLUTION
	==========
	
	To resolve this problem, use the MDBView utility to identify the delegate rules
	and remove them. The Outlook delegate rules are stored in the Inbox folder.
	
	The delegate rule is an item in the Associated Messages in FLD window, in the CB
	entry, and has a description of "Schedule + EMS Interface."
	
	To remove delegate rules by using the MDBView utility:
	
	1. Start the MDBView utility, click MAPI_Explicit_PROFILE, and then click OK.
	
	2. Click the profile name of the user whose mailbox contains the delegate rule.
	
	3. On the MDB menu, click Open Message Store. In the Store Display Name pane,
	  click the user's mailbox, and then click Open.
	
	4. On the MDB menu, click Open Root Folder.
	
	5. In the root folder, double-click the "Top of Information Store" folder.
	
	6. Double-click the Inbox folder.
	
	7. In the "Associated message in FLD" window, double-click to open each message
	  until you find a message with "Schedule + EMS Interface" in the properties
	  (the bottom window in the dialog).
	
	8. Close this message to return the focus to the list.
	
	9. To delete this message, in the Associated Message In FLD window, click to
	  select the message. In the Operations Available box, click the
	  "lpFLD->DeleteMessages()". Click Call Function and then click OK to
	  confirm the deletion. The message is deleted.
	
	If the user had an existing delegate, re-add the delegate.
	
	MORE INFORMATION
	================
	
	The MDBView utility (Mdbvu32.exe) is located on both the Standard Edition and
	Enterprise Edition of the Exchange Server CD-ROM in the Support\Utils\I386
	folder. You can run the utility directly from the CD-ROM.
	
	Additional query words: Delegate Rule MDBVU32 OL97 OL98 OL2000
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchange550 kbZNotKeyword2 kbOutlook2000Search kbOutlook97Search kbOutlook98Search kbZNotKeyword3
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
