---
layout: page
title: "Q317062: Unable to Add Users to SNA HAC DB in Multi-Domain Environment"
permalink: /kb/317/Q317062/
---

## Q317062: Unable to Add Users to SNA HAC DB in Multi-Domain Environment

{% raw %}

	Article: Q317062
	Product(s): Microsoft SNA Server
	Version(s): 
	Operating System(s): 
	Keyword(s): kbhis2000 kbhis2000bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you use Host Account Manager to add a user account to an SNA Host Account
	Cache database from a Windows NT or a Windows 2000 domain other than the domain
	where the SNA Host Account Cache (HAC) database is located, you may receive the
	following error message:
	
	  There is no record of the selected user in the Host Account Cache. Please
	  select a different account.
	
	If you use the Host Integration Server 2000 command-line configuration utility
	(Snacfg.exe) to add a user account to an SNA Host Account Cache database from a
	Windows NT or a Windows 2000 domain other than the domain where the SNA Host
	Account Cache (HAC) database is located, you may receive the following error
	message:
	
	  Cannot add <domain>\<username>. Error: Referenced WinNT user not
	  found
	
	CAUSE
	=====
	
	Before the SNA Host Account Cache service (Snaudb.exe) adds a user account to
	the HAC database, Snaudb.exe calls a Win32 API to obtain detailed information
	about the user account.
	
	If the user account does not exist in the domain in which the SNA Host Account
	Cache service is running, then the Win32 API call fails and you receive an error
	message.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	File name    Date         Time      
	------------------------------------
	Snaudb.exe   03/12/2002   08:08am 
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Host Integration
	Server 2000.
	
	MORE INFORMATION
	================
	
	Many customers implement multiple domain models in their Windows NT or Windows
	2000 environments. Please refer to the following Knowledge Base article for more
	details about how to configure host security in a multiple domain environment:
	
	  Q194695 How to Configure Host Security for a Multi-Domain Environment
	
	The following is an example of a multiple domain model that implements the
	Security Integration feature included with Host Integration Server (HIS) 2000.
	
	The sample multiple domain model consists of a Windows 2000 Forest that includes
	a parent domain named "Parent" and a child domain named "Child".
	
	The Child domain contains one or more servers running HIS 2000. The Primary
	Domain Controller (PDC) Emulator for the Child domain is running the following
	Security Integration features:
	
	- SNA Host Account Cache service
	- SNA WinNT Account Synchronization service
	
	NOTE: Each of these services is operating in a primary role. The SNA WinNT
	Account Synchronization service also is installed on the remaining the domain
	controllers (DCs) in the Child domain, but these DCs are configured in a backup
	role.
	
	The SNA WinNT Account Synchronization service also is installed on all of the DCs
	in the Parent domain. The SNA WinNT Account Synchronization service on the PDC
	Emulator in the Parent domain is configured manually to operate in a backup role
	because there should be only one primary SNA WinNT Account Synchronization
	service in a host security environment.
	
	In this configuration, you can add user accounts to the HAC database in the Child
	domain. The problem described previously occurs when you try to use Host Account
	Manager or Snacfg.exe to add user accounts from the Parent domain to the HAC
	database.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbhis2000 kbhis2000bug 
	Technology        : kbAudDeveloper kbHostIntegServ2000
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
