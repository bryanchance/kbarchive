---
layout: page
title: "Q256322: Error Configuring IIS to Use Samba Network Share As Its Root"
permalink: /kb/256/Q256322/
---

## Q256322: Error Configuring IIS to Use Samba Network Share As Its Root

{% raw %}

	Article: Q256322
	Product(s): Internet Information Server
	Version(s): winnt:4.0,5.0
	Operating System(s): 
	Keyword(s): kbOSWin2000
	Last Modified: 12-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to specify a Samba network share for an IIS virtual directory root
	or Web site root, the Microsoft Management Console (MMC) generates an "Access is
	Denied" error message, and the new virtual directory or site has a stop sign
	icon next to it. However, if you use the NET command, you can map a drive letter
	to the Samba network share with no problems.
	
	When there is no network connection open, IIS cannot list the files, and the
	"Access is Denied" error message occurs even though the user has root access to
	the share and its contents.
	
	When a network connection is open, IIS can then list the contents of the share,
	but a user cannot browse to the default file. (A stop sign icon still appears
	next to the virtual directory.)
	
	If you map a drive letter to the share, and IIS is configured to search for the
	mapping, a user can successfully browse to that site. (A stop sign icon still
	appears next to the virtual directory.)
	
	CAUSE
	=====
	
	This problem occurs when Samba is not configured to encrypt passwords that are
	sent across the network.
	
	RESOLUTION
	==========
	
	On the computer running Windows NT Server, remove the following registry entry
	to enable plain-text passwords (if the entry previously existed):
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Rdr\Parameters\
	  EnablePlainTextPassword (DWORD Value=1)
	
	Configure the Smb.cnf configuration file on the Samba server to reflect the
	following:
	
	  [Global]
	  Workgroup = (Windows NT Server name)
	  Security = Server
	  Encrypt Passwords = Yes
	
	WORKAROUND
	==========
	
	To work around this problem, do the following:
	
	1. Map a drive letter to \\<servername>\iisroot using "root" and
	  "password."
	
	2. In the Samba virtual directory, change the home directory from Share on
	  Another Computer to Local Directory, and then specify the drive letter that
	  you mapped in the previous step.
	
	3. Restart the Web site, and then test it by browsing.
	
	NOTE: This method involves a security risk, because the user that created the
	mapping must remain logged on to the local console. Therefore, the only security
	is by locking the computer.
	
	MORE INFORMATION
	================
	
	Further support for the UNIX/Samba configuration can be obtained from Samba.
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Additional query words: Samba; Unix
	
	======================================================================
	Keywords          : kbOSWin2000 
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : winnt:4.0,5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
