---
layout: page
title: "Q167002: XWEB: Limitations of the Active Server Components"
permalink: /kb/167/Q167002/
---

## Q167002: XWEB: Limitations of the Active Server Components

{% raw %}

	Article: Q167002
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 16-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Active Server Components, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the Microsoft Exchange Active Server Components (also known as the Web
	Connector), you can use a web browser to access your private mailbox, as well
	public folder discussions and directory information. Developers can also easily
	build interactive web-based applications using the rich data storage and
	directory and messaging capabilities of Microsoft Exchange Server. These
	applications enable developers to make ordinary web pages more rich,
	interactive, and compelling by adding Microsoft Exchange services such as a
	threaded discussion. (See the Microsoft Web site at
	http://www.microsoft.com/exchange/http.htm for more background information).
	
	This article outlines known limitations of the Microsoft Exchange Active Server
	Components.
	
	MORE INFORMATION
	================
	
	Known limitations of the Microsoft Exchange Active Server Components are:
	
	- Attachments can only be sent provided the following requirements are met:
	
	  1. Microsoft Exchange Server must be at Service Pack 1 or higher.
	
	  2. The Microsoft Internet Explorer must be version 3.02 or higher.
	
	  3. The File Upload add-on for Microsoft Internet Explorer must be applied to
	     the browser.
	
	  4. The MAC version of Microsoft Internet Explorer must be 3.01a or higher.
	
	  5. The version of Netscape Navigator must be 3.02 or greater.
	
	  Note: The File Upload add-on only needs to be applied to the Windows versions
	  of Microsoft Internet Explorer.
	
	- Scheduling information cannot currently be viewed. This is a planned feature
	  for a future version.
	
	- When logging on to the browser, you get no notification if the Out-Of- Office
	  assistant is turned on.
	
	- Display names are not accepted in the logon.asp Log On page. You must enter
	  the mailbox name [alias] as it appears from the Microsoft Exchange Server
	  Administrator program.
	
	- Unread message count is not displayed.
	
	- Windows NT Domain passwords cannot be changed.
	
	- You cannot open other individuals' mailboxes.
	
	- There is currently no forms support. However, Outlook server-based folders
	  (Calendar, Contacts, Journal, Notes, and Tasks) are included. These are
	  Outlook forms and will appear as messages in the Active Server Components.
	
	- Folders cannot be renamed when using the Web client. For additional
	  information, please see the following article in the Microsoft Knowledge
	  Base:
	
	  Q162484 XWEB: Unable to Rename Folders with ASC
	
	- Mailbox Storage limit warnings are not received on the Web client. If the
	  Prohibit Send option is enabled for a mailbox and that mailbox is over its
	  storage limit, no descriptive error message is displayed when attempting to
	  send mail from the Web client. The following is displayed:
	
	  Failed to send message
	
	Additional query words: kluane
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbZNotKeyword6 kbExchangeSearch kbZNotKeyword2 kbExchangeActiveServComp500
	Version           : 5.0
	
	=============================================================================
	

{% endraw %}
