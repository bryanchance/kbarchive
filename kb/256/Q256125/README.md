---
layout: page
title: "Q256125: SMS: No Status Message When Client Base Components Upgraded"
permalink: /kb/256/Q256125/
---

## Q256125: SMS: No Status Message When Client Base Components Upgraded

{% raw %}

	Article: Q256125
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbClient kbsms200 kbsms200bug kbUpgrade kbsms200sp2fix
	Last Modified: 30-JUL-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft System Management Server (SMS) 2.0 and 2.0 SP1, status messages are
	not generated when the client base components are updated on the SMS 2.0 client
	successfully (either by applying a hotfix or by a software upgrade). This can
	make it difficult for an administrator to determine when an upgrade to SMS
	clients has finished successfully.
	
	CAUSE
	=====
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	This problem was first corrected in Systems Management Server version 2.0 Service
	Pack 2.
	
	MORE INFORMATION
	================
	
	
	Starting with Systems Management Server 2.0 Service Pack 2 there is a Heartbeat
	Discovery Data Record (DDR) generated after a base component version upgrade.
	This DDR is created during the Client Component Installation Manager(CCIM) cycle
	following the upgrade, and added to the database.
	
	This new functionality is available with all upgrades after Systems Management
	Server 2.0 SP2, but is not reported to the client base component version upgrade
	when installing Service Pack 2.
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbClient kbsms200 kbsms200bug kbUpgrade kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
