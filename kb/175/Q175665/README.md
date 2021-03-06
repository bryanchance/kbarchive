---
layout: page
title: "Q175665: No Repair Option Offered Using Small Business Server Boot Disks"
permalink: /kb/175/Q175665/
---

## Q175665: No Repair Option Offered Using Small Business Server Boot Disks

{% raw %}

	Article: Q175665
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0a,4.5
	Operating System(s): 
	Keyword(s): kbsetup sbs
	Last Modified: 28-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Small Business Server versions 4.0, 4.0a, 4.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start an Intel processor-based system from the three setup disks that
	come with Small Business Server, or when you start Setup on a DEC Alpha (RISC)
	system from the Small Business Server compact disc, you never get the option to
	run through the repair process.
	
	CAUSE
	=====
	
	The three SBS setup disks and the compact disc are programmed to perform an
	unattended installation of Small Business Server and related components and,
	therefore, bypass the screen that offers the repair option.
	
	WORKAROUND
	==========
	
	On an Intel System
	------------------
	
	- On the second setup disk, rename Winnt.sif to Winnt.bak. You can restart from
	  these disks and it will prompt you to run the Repair process.
	
	  -or-
	
	- Re-create a second set of setup disks by using the Small Business Server
	  distribution compact disc (not a retail version of Windows NT 4.0 Server or
	  Workstation).
	
	  To do this, go to any computer running the retail version of Windows NT. Place
	  the first Small Business Server distribution compact disc into the CD-ROM
	  drive and type the following at a command prompt:
	
	  "D:\i386\winnt32 /ox" (without the quotation marks)
	
	  Alternately, go to an MS-DOS/Windows-based computer and type the following at
	  the command prompt:
	
	  "D:\i386\winnt /ox" (without the quotation marks)
	
	For additional information on creating three setup disks, please see the
	following article in the Microsoft Knowledge Base:
	
	ARTICLE-ID: Q131735
	TITLE : How to Create Windows NT Boot Floppy Disks
	
	Keep in mind that using an Emergency Repair Disk should be considered a last
	resort, because this process overwrites many system files with versions that may
	not be compatible with the programs that are installed on the server.
	
	On a DEC Alpha (RISC) System
	----------------------------
	
	If a retail version of Windows NT Server (non-SBS) compact disc is available, use
	the Alpha firmware utilities to start the Windows NT setup process from the
	retail version of Windows NT Server compact disc. When you are presented with
	the screen that says "Welcome to Setup," replace the Windows NT Server compact
	disc with the first compact disc of Small Business Server. Select "R" to repair
	the system and then continue with the emergency repair.
	
	WARNING: Do not attempt to repair the system with the retail version of Windows
	NT Server compact disc. Doing so will produce unpredictable and undesirable
	results.
	
	If a retail version of Windows NT Server compact disc is not available, you can
	use the following steps to perform the repair.
	
	1. Install a new copy of Small Business Server (install Windows NT only -- do
	  not install the Server Applications, for example, Microsoft Exchange Server,
	  SQL Server, and so on), or Windows NT Workstation into a directory other than
	  Winnt.sbs. If you are installing Small Business Server, you will be informed
	  during the installation that the Winnt.sbs directory already exists. Press
	  ESC and type in a new directory name, such as Repair.
	
	  NOTE: The Small Business Server installation requires 2 GB of free hard disk
	  drive space. If 2 GB of space is not available, the installation will fail
	  and the only workaround is to use a Windows NT Workstation or Windows NT
	  Server compact disc.
	
	2. Start into this new working installation.
	
	3. Run Winnt32.exe from the Alpha directory of the first Small Business Server
	  compact disc. This will copy some temporary files to the hard drive, create a
	  new entry in the Alpha Boot menu called Installation/Upgrade.
	
	4. Restart the server and select the Installation/Upgrade selection on the Boot
	  menu. When you get to the screen that says "Welcome to Setup," select "R" to
	  repair.
	
	5. After the repair is finished, you may remove the extra entries from the Alpha
	  Boot menu and delete the temporary directory $WIN_NT$.~LS from drive C.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft BackOffice Small
	Business Server version 4.0. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: smallbiz sbs erd
	
	======================================================================
	Keywords          : kbsetup sbs 
	Technology        : kbAudDeveloper kbSBServSearch kbSBServ400 kbSBServ400a kbSBServ450
	Version           : winnt:4.0,4.0a,4.5
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
