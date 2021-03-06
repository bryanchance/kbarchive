---
layout: page
title: "Q207510: Err Msg: An Error Occurred Reading or Setting a Configuration..."
permalink: /kb/207/Q207510/
---

## Q207510: Err Msg: An Error Occurred Reading or Setting a Configuration...

{% raw %}

	Article: Q207510
	Product(s): Internet Information Server
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you remotely connect to an Internet Information Server (IIS) computer using
	the Internet Service Manager (ISM) in the Microsoft Management Console (MMC),
	and you attempt to make a directory or virtual directory into an application,
	the following error message is displayed:
	
	  An error occurred reading or setting a configuration parameter.
	  (0x80080005)
	
	Also, when you use the Microsoft Transaction Server (MTS) MMC snap-in and attempt
	to open a package, the following error message occurs:
	
	  An error occurred accessing components in the system package on this
	  computer.
	  Error code was 8080005. Make sure that:
	  Microsoft Transaction server is installed correctly
	  If you have set a specific identity for the system
	  package, check that the user account and password are correct.
	
	CAUSE
	=====
	
	During the Microsoft Transaction Server portion of the Windows NT Option Pack
	installation, the user may have accepted the default of Local administration,
	rather than Remote. Therefore, no remote administration user account was set for
	MTS.
	
	RESOLUTION
	==========
	
	To specify an account for the MTS package's identity, which can also be used for
	remote administration, perform the following steps:
	
	1. If you do not have an account to use for remote administration, create one
	  using User Manager.
	
	2. On the IIS computer, in the scope (left-hand) pane of the MMC, go to the
	  following branch:
	
	  Microsoft Transaction Server
	 Computers
	   My Computer
	     Packages Installed
	
	3. Right-click the package where the identity needs to be changed, and then
	  click Properties on the context menu.
	
	4. Click the Identity tab.
	
	5. Select the This user radio button, and then provide the user account and
	  password to use.
	  Note: Be sure to include the domain in the user text box, followed by a
	  backslash before the user's name, in the form of
	  <DomainName>\<UserName>
	
	MORE INFORMATION
	================
	
	By default, MTS packages run as Interactive User. However, for remote
	administration, it is preferable to run a package as a Windows NT user account.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Kevin
	Zollman, Microsoft Corporation.
	
	
	Additional query words: Microsoft Transaction Server mtx administrative account errmsg kberrmsg akz
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400
	Version           : winnt:4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
