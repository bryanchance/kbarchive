---
layout: page
title: "Q185153: XFOR: Using Exchange As a Gateway Between UNIX and MS Mail"
permalink: /kb/185/Q185153/
---

## Q185153: XFOR: Using Exchange As a Gateway Between UNIX and MS Mail

{% raw %}

	Article: Q185153
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0
	Operating System(s): 
	Keyword(s): exc4 exc5
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After an upgrade from Exchange Server version 4.0 to Exchange Server version
	5.0, MS Mail users may be unable to reply to mail received by means of the
	Internet Mail Service. This can also occur in systems where custom recipients
	have been created in Exchange Server for users connected to Exchange by means of
	the Internet Mail Service. A good example is an internal mail system that uses
	the Internet Mail Service to connect to a UNIX based mail system.
	
	CAUSE
	=====
	
	To prevent spoofing (impersonating another person via Internet mail), Exchange
	Server version 5.0 does not automatically resolve the Reply To address to a
	friendly name. Therefore, when a user receives mail from the Internet Mail
	Service, the Reply To address is in SMTP format (user@company.com) instead of
	the display name associated with the SMTP address. When this mail is sent to the
	MS Mail user, the Reply To address remains in SMTP format. Without the Access
	component, this address can not be resolved by MS Mail, and a reply message will
	fail.
	
	WORKAROUND
	==========
	
	To resolve this problem, use one of the following workarounds:
	
	Install the Access component that is supplied on the Exchange Server version 5.0
	CD and has unlimited licenses on each MS Mail postoffice. Have them point to the
	shadow postoffice on the Exchange Server computer. This will allow MS Mail to
	correctly route the reply mail, but it will NOT show the friendly name in the
	Reply To field on the MS Mail client.
	
	- or -
	
	Modify the registry to enable Exchange Server to resolve Reply To addresses on
	messages received from the Internet Mail Service to Exchange Server friendly
	names. This option requires that Service Pack 1 be installed on the computer
	running Exchange Server version 5.0.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Click the Start button, and then click Run.
	
	2. In the Open box, type "Regedt32" (without the quotation marks).
	
	3. In the Windows Registry Editor, click "HKEY_LOCAL_MACHINE on Local Machine"
	  on the Window menu.
	
	4. Double-click the System subfolder.
	
	5. Double-click the CurrentControlSet subfolder.
	
	6. Double-click the Services subfolder.
	
	7. Double-click the MSExchangeIMC subfolder.
	
	8. Double-click the Parameters subfolder.
	
	9. On the Edit menu, click Add Value and use the following value:
	
	  Value Name: AddressRewrite
	  Data Type: REG_DWORD
	  Value: 1
	
	10. Locate the ResolveP2 value name; double-click it and change the value to 1.
	  It should resemble the following:
	
	  Value Name: ResolveP2
	  Data Type: REG_DWORD
	  Value: 1
	
	When these parameters are set, Exchange Server remaps the Reply To address to the
	friendly name.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc4 exc5 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
