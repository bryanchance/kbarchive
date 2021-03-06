---
layout: page
title: "Q128244: INFO: SNA Server Load Balancing and Hot Backup"
permalink: /kb/128/Q128244/
---

## Q128244: INFO: SNA Server Load Balancing and Hot Backup

{% raw %}

	Article: Q128244
	Product(s): Microsoft SNA Server
	Version(s): 2.0,2.1,2.11,2.11 SP1,3.0,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbsna211sp1
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 3.0, 4.0 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how SNA Server clients perform load balancing and hot
	backups across SNA Servers.
	
	When an SNA session is opened on an SNA Server client machine, the underlying SNA
	client software randomly chooses a server to try. In effect, load balancing and
	hot backups are initiated by the client. However, this requires two or more SNA
	Servers to be configured to support the same LU resources (3270, LUA pool, or
	APPC LU aliases spanning two or more servers).
	
	NOTE: SNA Server doesn't support load balancing across connections defined on a
	single server.
	
	
	Load balancing and hot backups are supported regardless of the SNA Server
	client-server LAN interface used (Named pipes, IPX/SPX, TCP/IP sockets, Banyan
	IP, or AppleTalk).
	
	MORE INFORMATION
	================
	
	How SNA Server Clients Load Balance and Hot Backup to SNA Servers
	-----------------------------------------------------------------
	
	- The SnaBase service on each SNA Server broadcasts a list of SNA Server
	  services running on the server to all other SNA Servers in the subdomain. The
	  SnaBase service listens for these broadcasts and dynamically maintains a list
	  of SNA Server services in the subdomain.
	
	  NOTE: The transports used and frequency of SNA Server broadcasts are
	  controlled at the Server Broadcasts dialog box, found by choosing Server
	  Broadcasts from the Options menu of the SNA Server Administrator for SNA
	  Server 2.x or by choosing the Server Broadcasts tab in the SNA Subdomain
	  Properties page in SNA Server Manager for version 3.0. This configures the
	  subdomain.
	
	- The SNA client process (SnaBase service on Windows NT, WNAP.exe on Windows
	  3.x, SNABASE.exe on MS-DOS, and COMNAP.exe on OS/2) opens a sponsor
	  connection to the SnaBase service on an SNA Server in the subdomain. This
	  sponsor connection remains active while the SNA client process is running.
	  When the SNA client process first starts, the client receives a list of all
	  SNA Servers in the subdomain. Afterward, only server changes are sent (as SNA
	  Servers are started and stopped in the subdomain).
	
	  NOTE: The transports that an SNA Server supports for client connections is
	  configured in the Protocol dialog box in SNA Server Setup. This is configured
	  on a server by server basis.
	
	- When an SNA application requests a session (3270, LUA, APPC, or CPIC, and so
	  forth), the underlying SNA client sends the request to a randomly selected
	  server. If the server supports the LU being requested and the LU resource is
	  available, the session is established through the server.
	
	  NOTE: Besides opening sessions to SNA Servers in the sponsor subdomain, an
	  "otherservers" parameter can be configured on the client to specify
	  additional servers that the client should try to open sessions with. More
	  information about the otherservers parameter is included below.
	
	
	- If a second or subsequent client session is opened, the client first tries
	  the servers that it already has a session with to conserve LAN resources on
	  the client.
	
	Configuring Fault Tolerance For 3270 Sessions
	---------------------------------------------
	
	1. Group similar types of 3270 display LU's across servers and connections into
	  a 3270 LU pool using the LU Pools dialog box in SNA Server Administrator.
	  Only LU's of a given type can be pooled together. Secondary connections can
	  be configured as "On demand" to only start when needed.
	
	  NOTE: SNA Server doesn't support pooling of 3270 Printer LU's. Specific
	  Printer LU's must be preassigned to a user in order for print jobs to be
	  routed to a known printer destination. For example:
	
	  In the Servers and Connections window in SNA Administrator (on SNA Server 2.x)
	  or under the Connection[ASCII 146]s folder in SNA Server Manager(SNA Server
	  3.0):
	
	     SERVER1                         SERVER2
	        TOKEN1  connection               TOKEN2 connection
	             SRV1LU02 (3270 LU)              SRV2LU02  (3270 LU)
	             SRV1LU03 (3270 LU)              SRV2LU03  (3270 LU)
	             SRV1LU04 (3270 LU)              SRV2LU03  (3270 LU)
	
	     In the LU Pools window in SNA Server Administrator or in the LU Pools
	     folder in SNA Server Manager:
	
	        Pool: 3270POOL
	        LU Names: SRV1LU02
	                  SRV1LU03
	                  SRV2LU02
	                  SRV2LU03
	
	2. Assign one or more instances of the 3270 pool to an SNA Server user or group,
	  using either the Users and Groups window in SNA Server Administrator or the
	  Configured Users folder in SNA Server Manager. For example:
	
	     User: Everyone
	        LU or LU Pool Session #1: 3270POOL
	
	     User: DOMAIN\Domain Users
	        LU or LU Pool Session #1: 3270POOL
	        LU or LU Pool Session #2: 3270POOL
	
	  NOTE: In this example, one pooled session has been granted to the Everyone
	  group and two pooled sessions have been granted to users from the Domain
	  Users group.
	
	3. When an SNA client opens a 3270 pooled session, a session is established
	  through a server which supports an available instance of the LU pool. For
	  example, in the Session / Session Configuration dialog box in the 3270
	  applet, configure the pool like this:
	
	        LU or Pool Name: 3270POOL
	
	  and choose Session / Connect.
	
	
	The above example assumes different host LU's are used for hot backup. To
	configure SNA Server for 3270 hot backup to the same LU:
	
	- Configure two connections to the host, where each connection is emulating the
	  same PU definition. One of the connections should be configured for "On
	  Server Startup activation, with the other connection set for "On Demand"
	  (only one connection can be active at a time). For example:
	
	     SERVER1                              SERVER2
	        TOKEN1 connection                    TOKEN2 connection
	        (Activation: On Server Startup)      (Activation: On Demand)
	           SRV1LU02 (3270 LU)                    SRV2LU02 (3270 LU)
	
	- Define an LU pool for each LU local address spanning each connection. For
	  example:
	
	     Pool: LU2POOL
	     LU Names: SRV1LU02
	               SRV2LU02
	
	- Assign an instance of the LU2POOL to a specific user. Only one user will be
	  able to access one LU from the pool at any one time (since the pool
	  effectively contains the same host LU).
	
	When the user opens "LU2POOL" using a 3270 emulator, the user will be routed to
	the server with the active connection. If this server is stopped or unavailable,
	the on-demand connection on the backup server will be activated automatically
	and the user will gain access to the same 3270 LU from the backup server.
	
	Configuring Fault Tolerance for APPC/5250 Sessions
	--------------------------------------------------
	
	The following section describes how to configure SNA Server to support fault
	tolerance of LU6.2 sessions for APPC and CPIC (or 5250) applications which
	"invoke" LU6.2 conversations. An APPC application invokes a conversation by
	calling [MC_]ALLOCATE. A CPIC application invokes a conversation by calling
	CMALLC. A 5250 emulator always invokes the LU6.2 conversation.
	
	If the APPC or CPIC application is "invoked" by the remote system (in other
	words, if the APPC application calls RECEIVE_ALLOCATE, or CPIC application calls
	CMACCP), then the remote system determines the LU6.2 session (and thus, the
	connection and SNA Server) that a conversation start request (in other words,
	the IBM SNA FMH-5 attach message) is sent over. If a host system is invoking the
	conversation, the VTAM "ALSLIST" parameter can be used to control the LU over
	which the attach request is sent. See the IBM VTAM documentation for more
	information about this parameter.
	
	
	Configuring fault tolerance for APPC, CPIC or 5250 invoking programs
	
	1. Configure redundant Local/Remote LU Aliases across SNA Servers in the SNA
	  Server Administrator or Manager. For example:
	
	     Within Servers and Connections window in SNA Administrator or within
	     SNA Server Manager:
	
	     SERVER1
	            Local APPC LU alias = SNASERV
	            Local APPC LU network name = APPN, LU Name = SERVER1
	
	        TOKEN1  connection
	            Remote APPC LU alias = AS400
	            Remote APPC LU network name = APPN  LU Name = AS400
	            (partnered with SNASERV using the QPCSUPP mode)
	
	NOTE: SNA Server 3.0 introduces the use of dynamic APPC partnering. Therefore, an
	administrator configures remote LUs, but does not need to partner them with
	local LUs. SNA Server 3.0 will automatically partner the LUs when needed. SNA
	Server 3.0 also supports the dynamic creation of Remote APPC LU's, if the
	checkbox for "Dynamic Remote APPC LU definition" is checked on the connection
	dialog. If an SNA Server receives a client allocate request for a Remote LU not
	defined on the server, and dynamic Remote LU definition is enabled, this causes
	SNA Server to automatically create the Remote APPC LU requested by the
	application. If dynamic creation is selected for connections owned by one server
	and not others in the same subdomain, this may tend to cause client sessions to
	use this server rather than others.
	
	     SERVER2
	            Local APPC LU alias = SNASERV
	            Local APPC LU network name = APPN, LU Name = SERVER2
	
	        TOKEN2  connection
	            Remote APPC LU alias = AS400
	            Remote APPC LU network name = APPN  LU Name = AS400
	            (partnered with SNASERV using the QPCSUPP mode)
	
	- SERVER1 Local APPC LU (SNASERV): Check the "Member of default outgoing Local
	  APPC LU pool" checkbox
	
	- SERVER2 Local APPC LU (SNASERV): Check the "Member of default outgoing Local
	  APPC LU pool" checkbox
	
	NOTE: While the Local APPC LU alias must be the same to support fault tolerance
	across SNA Servers, the LU Name must be unique so that unique AS/400 Device
	Names are requested for each user. Otherwise, users will be requesting the same
	device name, causing their 5250 emulator to hang while waiting for the device to
	become available.
	
	1. In the APPC application (such as the 5250 emulator), open a session using the
	  Local and Remote LU aliases supported by the servers. For example, using the
	  5250 applet, open the Session / Session Configuration dialog box and enter: "
	  Local LU alias = (leave blank) Partner LU alias = AS400 " (without the
	  quotation marks) NOTE #1: For load balancing to work across SNA Servers, the
	  Local APPC LU alias (1) must not be specified by the APPC application in it's
	  TP_STARTED request, (2) the "default" Local LU alias must be left blank in
	  the user or group record in SNA Server Admin/SNA Server Manager and (3) the
	  LocalLU parameter must not be set in the SNA client configuration for the
	  transaction program. The LocalLU parameter is described in the SNA Server
	  APPC and CPIC Programmer's Guide, chapter 2.
	
	  If the Local LU alias is defaulted using any one of these options, then the
	  SNA Server APPC interface may not choose an SNA Server with an available
	  LU6.2 session, causing an APPC/CPIC conversation startup request to "hang"
	  until a session becomes available. Relying on the "default outgoing Local
	  APPC LU pool" checkbox on the Local APPC LU is recommended for best LU6.2
	  load balancing and hot backup.
	
	  When APPC LU aliases are defaulted on a user/group record, these LU aliases
	  are used if no LU aliases are provided by the APPC application. Other ways of
	  defaulting APPC LU's are described in Chapter 6 of the "SNA Server 2.1 Admin
	  Guide" or in Part 4 of the SNA Server 3.0 Administration Guide[ASCII 148]
	  (<snaroot>\system\admingd.hlp).
	
	  NOTE #2: The Local LU alias can be specified using any method above and load
	  balancing will work normally if the LUWIDSUP parameter is set to NO in the
	  SNA client software, as described in Appendix C of the SNA Server Reference
	  Guide. This parameter causes the SNA Server APPC interface to deactivate
	  support for the logical unit of work identifier (luw_id) for APPC programs.
	  This causes the SNA client APPC interface to always defer it's location of an
	  SNA Server until the application issues an [MC_]ALLOCATE or CMALLC request.
	
	
	The "Otherservers" Feature
	--------------------------
	
	The SNA Server client software supports an "otherservers" configuration entry, as
	described in Appendix C of the SNA Server Reference Guide. This entry allows the
	client to try connecting to a list of SNA Servers when opening an SNA session,
	in addition to the SNA Servers running in the subdomain to which the client has
	a sponsor connection.
	
	The SNA Server client will always retrieve it's user/group (3270 and APPC alias)
	configuration entries from the subdomain which the client has an established
	sponsor connection. The SNA Server client has no way of retrieving the
	user/group record configured on servers outside of this subdomain (unless the
	SNA client is reconfigured to connect to a different sponsor server).
	
	In order to open a session through an "otherserver" (located outside of the
	client subdomain), these servers must be configured to support the same LU
	resource names (that is, 3270 pool names and APPC LU alias names) as the primary
	subdomain.
	
	Troubleshooting Suggestions
	---------------------------
	
	If users don't appear to be load balancing across SNA Servers:
	
	- Using SNA Administrator or SNA Manager, make sure the SNA Servers are running,
	the connections supporting the pooled LU's (or APPC LU's) are active and the
	LU's are available. The 3270 LU status should appear as "Available". The APPC LU
	status is viewable in SNA Server Admin by zooming on the Local LU and choosing
	"Status". The APPC LU session limit should be non-zero. If it is zero, this
	indicates an APPC LU session activation problem where SNA Server Data Link
	Control traces and SNA Server configuration file (COM.CFG) are needed to
	diagnose the cause. If the active session count is the same as the LU session
	limit, this means all available sessions are in use on this APPC LU/LU pair.
	
	NOTE: SNA Server 3.0 does not include a way of checking the status of APPC LUs
	since it does not do CNOS negotiation until a session is requested. SNA Server
	2.x performs CNOS negotiation by default when a connection with APPC LUs was
	activated. The DISPLAY.EXE program, included with SNA Server 3.0, can be used to
	determine the negotiated session limits on all APPC LU/LU/mode partnerships for
	any SNA Server in a subdomain.
	
	- If the servers are operating normally, check the Windows NT application event
	log (using Event Viewer) to see if the SNA Server service or connections were
	recently restarted. If so, only recent users have established sessions to this
	server.
	
	- For 3270, make sure the users opening sessions against the servers have been
	assigned an instance of an LU pool which spans the servers evenly. Note that
	once a user has a session against a server, additional client sessions will be
	opened to the same server first.
	
	- Make sure the user has LAN access to open a session against the servers in the
	subdomain or to the "otherservers". This is especially true if a user is unable
	to get a session through an "otherserver" which resides outside of the
	subdomain.
	
	- Check the Windows NT system event log for any indication of Server service
	resource shortages. If so, this could indicate LAN connection problems for SNA
	clients connecting over a named pipe connection.
	
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q266275 Host Integration Server 2000 Client LU6.2 Load Balancing Across
	  Servers
	
	Additional query words: prodsna backup snafaq
	
	======================================================================
	Keywords          : kbnetwork kbsna211sp1 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210 kbSNAServ211SP1
	Version           : :2.0,2.1,2.11,2.11 SP1,3.0,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
