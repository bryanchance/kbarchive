---
layout: page
title: "Q140476: How to Install a BDC in a Routed TCP/IP Environment"
permalink: /kb/140/Q140476/
---

## Q140476: How to Install a BDC in a Routed TCP/IP Environment

{% raw %}

	Article: Q140476
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When an installation of a backup domain controller (BDC) is performed, the
	primary domain controller (PDC) must be available to establish the computer
	account and the Security Identifier (SID) for the new BDC. If the protocol being
	used is TCP/IP and, in order to form a connection to the PDC, TCP/IP must be
	routed, name resolution for the domain name and the computer name must be
	established during the Network setup.
	
	MORE INFORMATION
	================
	
	Name resolution for connectivity to the primary domain controller can be
	established by using one of the following methods:
	
	- Enter a primary and, optionally, a secondary WINS server where the PDC has
	  registered the domain<1Bh> entry.
	
	  -or-
	
	- Use an LMHOSTS file that has at least an entry for the PDC as follows:
	
	  
	
	  <;PDC IP address>;  "DOMAINNAME   \0x1B"  #PRE
	
	  NOTE: There must be exactly 20 characters inside the double quotes.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q180094 How to Write an LMHOSTS File for Domain Validation
	
	  Q180099 Troubleshooting LMHOSTS Name Resolution Issues
	
	During installation, if WINS servers are not available, the LMHOSTS file can be
	used by importing it from a floppy disk or from an existing physical drive on
	the computer being installed. The location for importing the LMHOSTS file is in
	the Advanced options in the TCP/IP configuration dialog during Network setup.
	This must be completed during the portion of Setup where you configure the
	properties of the TCP/IP protocol.
	
	If the PDC cannot be located during setup, you will get the following error
	message:
	
	  The domain controller for this domain cannot be located.
	
	If you get this message, check the following:
	
	- Adapter configuration settings.
	
	- Default gateway configuration on the adapter.
	
	- If using WINS to locate the PDC, make sure the WINS server you are pointing
	  to contains the 1Bh registration for the domain name.
	
	- Check the syntax of the LMHOSTS file.
	
	At this point, installation must be restarted. Going back to the network
	configuration by selecting the previous screen boxes will not reinitialize your
	TCP/IP configuration settings.
	
	NOTE: If you are installing a Windows NT 4.0 domain controller, restarting the
	server will restart the installation at the GUI portion of setup. Previous
	versions of Windows NT require setup to be restarted from the beginning.
	
	This scenario is not an issue for a server non-domain controller, as that type of
	installation is capable of becoming part of a workgroup where membership in the
	domain is not mandatory during setup.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : :3.5,3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
