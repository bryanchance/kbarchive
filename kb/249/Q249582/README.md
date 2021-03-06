---
layout: page
title: "Q249582: SMS: &quot;Primary Key Violation&quot; Error Message When Processing DDRs"
permalink: /kb/249/Q249582/
---

## Q249582: SMS: &quot;Primary Key Violation&quot; Error Message When Processing DDRs

{% raw %}

	Article: Q249582
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms200sp2fix
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems Management Server (SMS) 2.0 Discovery Data Manager (DDM) may stop
	processing Discovery Data Records (DDRs) and generate a "Primary key violation"
	error message in the Ddm.log file. In the following sample log file excerpt, the
	name of the computer being processed is "OPGM-89." Note the space after the name
	of the computer being processed.
	
	  SQL>>>insert into System_Resource_N_ARR (ItemKey, Resource_Names0)
	  values (2725, "OPGM-89 ") SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:49 AM
	  472 (0x1D8)
	  SQL>>> Violation of PRIMARY KEY constraint
	  'System_Resource_N_ARR_PK'. Cannot insert duplicate key in object
	  'System_Resource_N_ARR'. SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:49 AM
	  472 (0x1D8)
	  SQL>>> The statement has been terminated. SMS_DISCOVERY_DATA_MANAGER
	  12/20/1999 10:23:49 AM 472 (0x1D8)
	  SQL>>> General SQL Server error: Check messages from the SQL Server.
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:49 AM 472 (0x1D8) 3
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472 (0x1D8)
	  CDiscoverySource_SQL::UpdateItem - could not execute sql- insert into
	  System_Resource_N_ARR (ItemKey, Resource_Names0) values (2725, "OPGM-89 ")
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472 (0x1D8)
	  CDiscoverDataManager::ProcessDDRs_PS - Unable to update data source
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472 (0x1D8)
	  TATMSG: ID=2636 SEV=E LEV=M SOURCE="SMS Server"
	  COMP="SMS_DISCOVERY_DATA_MANAGER" SYS=RRBSMS SITE=RRB PID=99 TID=472
	  GMTDATE=Mon Dec 20 16:23:50.671 1999
	  ISTR0="D:\SMS\inboxes\ddm.box\PP9DNM8E.DDR" ISTR1="" ISTR2="" ISTR3=""
	  ISTR4="" ISTR5="" ISTR6="" ISSTR7="" ISTR8="" ISTR9="" NUMATTRS=0
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472 (0x1D8)
	  CDiscoverDataManager::ProcessDDRs_PS - SQL problem detected. Will retry later.
	  SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472 (0x1D8)
	  CDiscoverDataManager::Process - Failed to manage files in inbox. Will retry in
	  at least 60 seconds SMS_DISCOVERY_DATA_MANAGER 12/20/1999 10:23:50 AM 472
	  (0x1D8)
	
	Status message error:
	
	  SMS_DISCOVERY_DATA_MANAGER 2636 SMS Discovery Data Manager failed to process
	  the discovery data record (DDR) "D:\SMS\inboxes\ddm.box\PP9DNM8E.DDR",
	  because it cannot update the data source.
	
	After DDM encounters this error, no other DDRs are processed until the problem
	DDR is removed from the SMS\Inboxes\DDM.box folder. This can cause a large
	backlog of DDRs, and over time can also cause high CPU usage.
	
	CAUSE
	=====
	
	This issue is caused by Network Discovery discovering a workstation that
	contains a space at the end of its NetBIOS name. Microsoft Windows NT-based
	clients do not allow you place a space at the end of the name. It is possible to
	encounter this problem with Windows NT-based workstations that are not running
	Windows NT.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	WORKAROUND
	==========
	
	To work around this problem, determine which client has a name with a space at
	the end and remove the space from the workstation's NetBIOS name. To determine
	which client is causing this problem:
	
	1. Check the Ddm.log file to determine the name of the workstation. You see a
	  line just before the "Primary Key error" message similar to:
	
	  ==>Name = <OPGM-81 >
	
	The name between the brackets is the name of the workstation.
	
	2. Stop the SMS_Executive service on the site server.
	
	3. Find the problem DDR in the SMS\Inboxes\DDM.box folder by performing a text
	  search on all files containing the computer name. In this example, search for
	  "<OPGM-81 >".
	
	4. Delete all DDRs that you locate with this search.
	
	5. On the workstation itself, remove the space from the end of the NetBIOS name.
	
	You may have to delete multiple DDRs from the DDM.box folder, depending on how
	many times the workstation has been discovered.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
