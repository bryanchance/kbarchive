---
layout: page
title: "Q218107: SNA Server 4.0 SP2 Requires Internet Explorer 3.02 or Later"
permalink: /kb/218/Q218107/
---

## Q218107: SNA Server 4.0 SP2 Requires Internet Explorer 3.02 or Later

{% raw %}

	Article: Q218107
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0 SP2
	Operating System(s): 
	Keyword(s): kbsna300sp4fix kbsna400sp3fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Internet Explorer 3.02 or later must be installed prior to running the Setup
	program to install SNA Server 4.0 Service Pack 2 (SP2), the SNA Server 4.0 SP2
	client for Windows NT, or the SNA Server 4.0 SP2 client for Windows 95/98.
	Internet Explorer 3.02 or later is also required when running the Update program
	to apply SP2 to an existing SNA Server/Client 4.0 or 4.0 Service Pack 1 system.
	
	The following message is displayed if the SNA Server/Client 4.0 SP2 Setup or
	Update program is run on a system that does not have Internet Explorer 3.02 or
	later installed:
	
	  Requirements Information
	
	  A review of your system for external software dependencies has found the
	  following issue:
	
	  Internet Explorer Version 3.02 or greater required.
	
	The Setup or Update program ends after the message dialog box is closed by
	clicking OK.
	
	In addition, Internet Explorer 3.02 or later needs to be installed in order to
	uninstall SNA Server 4.0 SP2.
	
	CAUSE
	=====
	
	SNA Server 4.0 SP2 requires Internet Explorer because a few of its components
	rely on it to function properly. These components include MMC (Microsoft
	Management Console), COMTI (COM Transaction Integrator for CICS and IMS), and
	the OLE/DB Providers.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	4.0. For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft SNA Server version
	4.0 SP2. This problem was first corrected in SNA Server version 4.0 Service Pack
	3.
	
	MORE INFORMATION
	================
	
	IMPORTANT: Following this procedure can cause unpredictable problems when you
	attempt to use certain SNA Server client and/or server components.
	
	The Setup.exe and Update.exe programs for the following have been updated to
	allow the check for Internet Explorer 3.02 or later to be disabled:
	
	- SNA Server client for Windows NT
	- SNA Server client for Windows 95/98
	- SNA Server
	
	
	The following steps explain how to apply and use the updated binaries to disable
	the Internet Explorer check:
	
	1. Copy the SNA Server 4.0 SP2 version of the Windows NT and Windows 95/98
	  client to a directory on a hard drive such that the following directory
	  structure exists on the hard drive:
	
	  <root>
	  <root>\Mmc\....
	  <root>\Mdac\....
	  <root>\Clients
	  <root>\Clients\Win9x
	  <root>\Clients\Winnt\I386
	  <root>\Clients\Winnt\Alpha
	
	  The following directory structure is needed for SNA Server:
	
	  <root>
	  <root>\Mmc\....
	  <root>\Mdac\....
	  <root>\I386
	
	  NOTE: The root of the SNA Server 4.0 SP2 CD, the MMC, and the MDAC directories
	  are required to ensure proper installation.
	
	2. Back up or rename the existing Setup.exe, Update.exe, and Snasetup.dll
	  binaries in the appropriate client directory (for example, Clients\Win9x\ for
	  the Windows 95/98 client) and/or the I386 directory for the SNA Server. Note
	  that the Snasetup.dll is only needed when installing/updating an SNA Server,
	  not a SNA Server client.
	
	3. Copy the updated versions into the appropriate client and/or server
	  directories.
	
	  NOTE: The updated client Setup.exe and Update.exe programs apply to both the
	  Windows NT and Windows 95/98 version of the SNA Server client. The updated
	  Setup.exe, Update.exe, and Snasetup.dll for SNA Server only apply to SNA
	  Server.
	
	4. Run Setup or Update from a command prompt as follows to disable the Internet
	  Explorer check:
	
	  "setup /noie" (without the quotation marks)
	
	  -or-
	
	  update /setupparms: "/noie" (NOTE: The quotation marks are necessary.)
	
	  Setup.exe should be used for new installations of the SNA Server 4.0 SP2
	  client for Windows NT or Windows 95/98, or SNA Server. Update.exe should be
	  used when updating existing versions of the SNA Server 4.0 or 4.0 SP1 clients
	  for Windows NT or Windows 95/98, or existing SNA Server 4.0 or 4.0 SP1
	  systems.
	
	  If the Setup program has to be run later to add or remove components, to
	  remove SNA Server, or to reinstall components, the Setup program will need to
	  be run using the /noie parameter.
	
	NOTE: The SNA Server client functions that require Internet Explorer will not
	function correctly if the client is installed on a system that does not have
	Internet Explorer installed. Some of the features that may not work properly are
	the SNA Server MMC Snap-In, COMTI, and the SNA OLE/DB providers. If these
	features are needed, Internet Explorer 3.02 or later has to be installed to
	ensure that these features function properly.
	
	The Readme.txt file included with SNA Server 4.0 SP2 indicates that Internet
	Explorer 3.02 is one of the minimum requirements needed to install or apply SNA
	Server 4.0 SP2. Please refer to the Readme.txt file for information on the other
	requirements for SNA Server 4.0 SP2.
	
	Internet Explorer is not installed by either the SNA Server Setup or Update
	programs. However, the SNA Server 4.0 SP2 CDs include a copy of Internet
	Explorer 4.0 in the Ie directory.
	
	If Internet Explorer is uninstalled after SNA Server/Client 4.0 SP2 is installed,
	running the SNA Server Setup program to uninstall SNA Server 4.0 SP2 will result
	in the message dialog box described in the "Symptoms" section.
	
	NOTE: If you use the setup /noie option to install SNA Server 4.0 SP2 on a
	Windows NT Server that does not have Internet Explorer installed, the following
	error message may be displayed after you select the SNA Server components to
	install:
	
	  MMC and MDAC requires Internet Explorer version 3.02 or higher.
	
	This occurs if the updated Snasetup.dll file is not used in conjunction with the
	updated Setup.exe program.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp4fix kbsna400sp3fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400SP2
	Version           : WINDOWS:4.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
