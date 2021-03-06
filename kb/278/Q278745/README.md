---
layout: page
title: "Q278745: SMS: Site Component Manager Reinstalls Component Servers"
permalink: /kb/278/Q278745/
---

## Q278745: SMS: Site Component Manager Reinstalls Component Servers

{% raw %}

	Article: Q278745
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsms200 kbsms120bug kbSiteComp kbsms200preSP4fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a remote Systems Management Server (SMS) component server is offline or
	otherwise unreachable over the network when the SMS Site Component Manager
	service attempts to contact it, Site Component Manager flags the SMS components
	to be reinstalled. When the remote server comes back online, Site Component
	Manager reinstalls the SMS components on that computer.
	
	This reinstallation process involves re-creating the service account for the SMS
	Executive service on the remote server. Therefore, a new user profile for the
	SMSSvc_[site_code]_<xxxx> account is created. Typically, this should not
	be a problem. However, if the network link to the remote server is prone to
	congestion or down time, the SMS components may be reinstalled frequently. As
	the user profiles accumulate, a large amount of disk space may be consumed on
	the system drive partition on the remote server.
	
	CAUSE
	=====
	
	If a system has been offline, it is reinstalled to ensure that all of the SMS
	components are installed and functional.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	
	WORKAROUND
	==========
	
	For an SMS component server that is a member server in a domain, the service
	account that is used by the SMS Executive service is a local machine account,
	not a domain account. For SMS component servers that are domain controllers, the
	service account is created in the domain. If there are multiple domain
	controllers performing SMS component server roles, there is more than one
	SMSSvc_[sitecode]_<xxxx> account in the domain. Do not delete the accounts
	manually because SMS does this automatically. The problem is only that the user
	profile is not deleted. Therefore, in both situations, you can confirm which
	account is in use by examining the startup properties of the SMS Executive
	service on a server and delete only the user profiles for the accounts that are
	not being used on that server.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	Currently, only remote site systems that are managed directly by Site Component
	Manager are affected by this problem. These include:
	
	- SMS SQL Server
	
	- SMS Client Access Point (CAP)
	
	These site systems are not managed directly by Site Component Manager and are not
	affected by this problem:
	
	- SMS Distribution Point
	
	- Software Metering Server
	
	- Software Metering Database Server
	
	
	
	Note that attempting to install a CAP to a clustered server can cause a similar
	problem. CAP reinstallations are not uncommon; attempts to reinstall a CAP to a
	clustered server by Site Component Manager do not work because Site Component
	Manager cannot find a non-clustered drive. For additional information, visit the
	following Microsoft Web site:
	
	  Microsoft Windows 2000 Server Clustering Interoperability with SMS
	  (http://www.microsoft.com/smsmgmt/techdetails/clustinterop.asp)
	
	Additional query words: prodsms profile sitecomp
	
	======================================================================
	Keywords          : kbsms200 kbsms120bug kbSiteComp kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
