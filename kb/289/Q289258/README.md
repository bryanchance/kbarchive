---
layout: page
title: "Q289258: XGEN: Exchange Server 5.5 Post-SP4 Internet Mail Service Fixes"
permalink: /kb/289/Q289258/
---

## Q289258: XGEN: Exchange Server 5.5 Post-SP4 Internet Mail Service Fixes

{% raw %}

	Article: Q289258
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): exc55kbfixlist
	Last Modified: 18-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists the article numbers for Exchange Server 5.5 Internet Mail
	Service bugs that have been fixed after Exchange Server 5.5 Service Pack 4 was
	released.
	
	For information about how to obtain the fixes listed in this article, click the
	article number(s) listed in the "More Information" section of this article.
	
	NOTE: Exchange Server fixes for a particular component are cumulative and contain
	all of the previous fixes for that component. Fixes with a particular version
	number contain all of the fixes that have an earlier version number.
	
	MORE INFORMATION
	================
	
	Internet Mail Service fixes include the following files:
	+--------------------------------+
	| File name    | Current version | 
	+--------------------------------+
	| Imcmsg.dll   | 5.5.2655.55     | 
	+--------------------------------+
	| Msexcimc.exe | 5.5.2655.55     | 
	+--------------------------------+
	
	Fixes Released on October 2, 2001
	---------------------------------
	
	The following files are modified:
	
	  Imcmsg.dll incremented to version 5.5.2655.15
	  Msexcimc.exe incremented to version 5.5.2655.15
	
	The following fix is included:
	
	  Q301690 XIMS: Corrupted Message Header Causes Access Violation in
	  Msexcimc.exe
	
	Fixes Released on February 13, 2001
	-----------------------------------
	
	The following files are modified:
	
	  Imcmsg.dll incremented to version 5.5.2654.14
	  Msexcimc.exe incremented to version 5.5.2654.52
	
	The following fixes are included:
	
	  Q272672 XIMS: Internet Mail Service Does Not Generate Non-Delivery Report
	  Message If Number of Recipients Exceeds 32,766
	
	  Q279320 XFOR: Messages in the Internet Mail Service Pickup Folder May Be
	  Moved to the Bad Mail Folder
	
	  Q285023 XCON: Internet Mail Service Does Not Follow Time to Live for DNS
	
	Additional query words: IMS IMC sp4 imcmsg dll msexcimc
	
	======================================================================
	Keywords          : exc55 kbfixlist
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
