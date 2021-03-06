---
layout: page
title: "Q154556: Delegation Requires a Stop and Restart of the DNS Server"
permalink: /kb/154/Q154556/
---

## Q154556: Delegation Requires a Stop and Restart of the DNS Server

{% raw %}

	Article: Q154556
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Depending on the steps you take to delegate a subzone to a different server by
	means of Domain Name System (DNS) Manager, you may or may not be required to
	stop and restart the DNS service.
	
	MORE INFORMATION
	================
	
	Delegate a Sub-domain: To create and delegate a new subzone for a new domain,
	follow these steps:
	
	1. In the Server List, add the server that will be authoritative for the new
	  subzone.
	
	2. Click this server and create the subzone as a new primary zone.
	
	3. In the Server List, double-click the primary server.
	
	4. If a domain does not exist for the new subzone, right-click the existing
	  zone, click New Domain and add a new domain for the subzone.
	
	5. Right-click the new domain and click New Record.
	
	6. Under Record Type, click NS Record. For Domain Server DNS Name, type the
	  fully qualified domain name (FQDN) of the DNS server that is authoritative
	  for the new subzone.
	
	7. Under Record Type, create an A record for the server that will be
	  authoritative for the new subzone and click OK.
	
	  NOTE: You only need to create an A record if the authoritative server for the
	  new subzone is within the domain of the authoritative zone on the primary
	  server.
	
	  For example, if you are authoritative for ms.com and delegating nt.ms.com to
	  bob.ms.com, you need to create an A record. However, if you are delegating
	  nt.ms.com to bob.otherzone.com, there is no need to create the A record.
	
	Example of Creating and Delegating a New Subzone for a New Domain
	-----------------------------------------------------------------
	
	The following steps create a new domain (nt.ms.com) in the ms.com zone on
	<server 1> and delegate it to nt.ms.com on <server 2>.
	
	1. In the Server List add <server 2>.
	
	2. Right-click <server 2> and create a the new primary zone nt.ms.com.
	
	3. Double-click <server 1>.
	
	4. Right-click the ms.com zone, and then add the domain nt.ms.com.
	
	5. Right-click the new domain, and then create an A record. For Host Name, type
	  <server 2>. For Host IP Address, type the IP address for <server
	  2>.
	
	6. Right-click the new domain again, and then create an NS record. For Domain
	  Server DNS Name, type <server 2>.nt.ms.com.
	
	If you follow the same steps as above, but reverse step 5 and step 6 (create the
	NS record before the A record), you need to restart the DNS server service
	because the delegation is not active until the DNS server service is stopped and
	restarted.
	
	Additional query words: prodnt ntdns
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}
