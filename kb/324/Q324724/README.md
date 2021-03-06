---
layout: page
title: "Q324724: BUG: Backup Sponsor Servers Added to Client's Sponsor Server Lis"
permalink: /kb/324/Q324724/
---

## Q324724: BUG: Backup Sponsor Servers Added to Client's Sponsor Server Lis

{% raw %}

	Article: Q324724
	Product(s): Microsoft SNA Server
	Version(s): 4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4
	Last Modified: 28-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you turn on the Backup Sponsor Server feature for an SNA subdomain, SNA
	Server 4.0 clients and Host Integration Server 2000 clients may try to connect
	to the configured backup sponsor servers, although there are available sponsor
	servers in the client's configured subdomain.
	
	If the SNA client or the Host Integration Server client makes a sponsor
	connection to a backup sponsor server, any later host session obtained by the
	user will be through an SNA Server server or a Host Integration Server 2000
	server that belongs to the SNA subdomain of the backup sponsor server.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Host Integration
	Server 2000 .
	
	
	MORE INFORMATION
	================
	
	The following explains how the problem described in this article can occur. The
	example uses Host Integration Server 2000, but it also applies to SNA Server
	4.0.
	
	- Host Integration Server 2000 End User Client Configuration:
	
	  By using the Resource Location Wizard, the client is configured to "Locate
	  Servers by Server Name". The following sponsor servers are configured for the
	  client:
	
	   - SPONSOR1
	   - SPONSOR2
	
	  Additionally, the following configuration options are turned on:
	
	   - Update SNA Server computer list dynamically
	   - Select an SNA Service computer list in random order
	
	- Host Integration Server 2000 Server Configuration:
	
	  The Backup Sponsor Server option is turned on and BACKUP1 is added as the
	  backup sponsor server to be advertised to the Host Integration Server 2000
	  clients. BACKUP1 is in a different SNA subdomain than SPONSOR1 and SPONSOR2.
	
	If SPONSOR1 and SPONSOR2 are unavailable, the Host Integration Server 2000 client
	correctly fails over to BACKUP1 to get a sponsor connection. The Host
	Integration Server 2000 client can then host sessions from Host Integration
	Server 2000 servers in the SNA subdomain in which BACKUP1 is located.
	
	When the failover occurs, the Host Integration Server 2000 client's sponsor
	server list is updated to include BACKUP1, in addition to SPONSOR1 and SPONSOR2.
	The problem occurs when the client randomly tries to connect to BACKUP1 as a
	sponsor server each time SnaBase.exe initializes. This is not the correct
	behavior; a backup sponsor should be used only when the client's configured
	sponsor servers are not available.
	
	If a Host Integration Server 2000 client has the DeleteNonActiveSponsors registry
	entry set to "YES" (without the quotation marks), and the configuration settings
	described previously, BACKUP1 is added to the client's sponsor server list and
	the other sponsor servers (SPONSOR1 and SPONSOR2, in this example) are removed
	from the sponsor server list when the client fails over to its backup sponsor
	server. The result is that the Host Integration Server 2000 client cannot
	reconnect to any Host Integration Server 2000 servers in its configured SNA
	subdomain. The Host Integration Server 2000 client must be reconfigured manually
	to have the correct sponsor servers added to its sponsor server list.
	
	REFERENCES
	----------
	
	For additional information about related topics, click the article numbers below
	to view the articles in the Microsoft Knowledge Base:
	
	  Q236578 Offline Servers Should Be Removed from Clients' Service Table
	
	  Q271516 Offline Servers Are Not Removed from the Service Table
	
	  Q160849 INFO: How the SNA Server Client Chooses a Sponsor SNA Server
	
	  Q323189 Random Sponsors Option Doesn't Work on HIS End-User Client
	
	Additional query words:
	
	======================================================================
	Keywords          : sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ400SP4
	Version           : :4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
