---
layout: page
title: "Q197060: XADM: JET Retry Hotfix Makes Repair (ESEUTIL /P) Very Slow"
permalink: /kb/197/Q197060/
---

## Q197060: XADM: JET Retry Hotfix Makes Repair (ESEUTIL /P) Very Slow

{% raw %}

	Article: Q197060
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 25-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you apply the fix detailed in the following Microsoft Knowledge Base
	article, running repair (ESEUTIL /P) is considerably slower than before the fix
	was in place.
	
	  Q192333 XADM: JET Will Now Retry 16 Times on -1018 Error
	
	CAUSE
	=====
	
	The second phase of repair is to scan every page in the database. During this
	scan, the Exchange Server database engine expects to encounter un- initialized
	pages. Un-initialized pages are zeroed out pages that have not been used yet.
	When an un-initialized page are encountered, a -1019 error
	(JET_errPageNotInitialized -- Blank database page) is generated in the Windows
	NT Application Event log, but repair is expecting that error.
	
	However, when the hotfix Ese.dll (in the article listed above) sees an un-
	initialized page, it retries the read 16 times. Retrying the reads for each
	un-initialized page in the database slows the scanning phase considerably.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Exchange Database Engine
	
	  File Name   Version
	  ----------------------
	  Ese.dll     5.5.2416.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	Additional query words: hang defrag
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
