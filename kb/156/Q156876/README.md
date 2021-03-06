---
layout: page
title: "Q156876: INFO: Using UDF Files with Windows NT 4.0 Unattended Setup"
permalink: /kb/156/Q156876/
---

## Q156876: INFO: Using UDF Files with Windows NT 4.0 Unattended Setup

{% raw %}

	Article: Q156876
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbsetup kbOPK kbSBKkbfaq
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Unattended Setup with Windows NT 4.0 supports the use of the Uniqueness Database
	File (UDF), which provides the ability to specify per-computer parameters. The
	functionality of the UDF is to merge or replace specific sections of the answer
	file for the GUI portion of setup. The use of the UDF provides a structured and
	convenient method for the deployment of Windows NT 4.0 on a large scale.
	
	The information in this article assumes that a working answer file has been
	developed for unattended installation of Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	The UDF is an ASCII text file created using a simple text editor. The file is
	stored with the other Windows NT files on the distribution server.
	
	The UDF is broken down into two sections, the UniqueIDs and the UniqueID
	parameters. The UniqueIDs section identifies the Unique ID and the sections of
	the answer file that are going to be merged or replaced. The UniqueIDs parameter
	is the actual data that will be merged or replaced in the answer file.
	
	Example 1
	---------
	
	In this example, two Unique IDs have been created: UserID1 and UserID2. UserID1
	and UserID2 will have Userdata, GuiUnattended, and Network sections that will
	merge or replace the corresponding sections in the answer file.
	
	     [UniqueIDs]
	        UserID1 = Userdata,GuiUnattended,Network
	        UserID2 = Userdata,GuiUnattended,Network
	
	In the next section of the UDF, Unique ID sections are identified by using the
	Unique ID and the section name, separated by a colon.
	
	Example 2
	---------
	
	In this example, the Userdata, GuiUnattended, and Network sections will be merged
	into the answer file. See the sample Unattend.txt file at the end of this
	article as a reference.
	
	     [UniqueIDs]
	        UserID1 = Userdata,GuiUnattended,Network
	        UserID2 = Userdata,GuiUnattended,Network
	
	     [UserID1:UserData]
	     FullName = "User ID-1"
	     ComputerName = "MACHINE-1"
	
	     [UserID1:GuiUnattended]
	     TimeZone = " (GMT-05:00) Eastern Time (US & Canada)"
	
	     [UserID1:Network]
	     JoinDomain = "DomainEast"
	
	     [UserID2:UserData]
	     FullName = "User ID-2"
	     ComputerName = "MACHINE-2"
	
	     [UserID2:GuiUnattended]
	     TimeZone = "(GMT-06:00) Central Time (US & Canada)"
	
	     [UserID2:Network]
	     JoinDomain = "DomainCentral"
	
	Merging of this unique information occurs during the execution of Winnt.exe or
	Winnt32.exe. To invoke the UDF file, use the following command-line options:
	
	/u:answer_file /s:NT_Source /t:temp_drive /UDF:UniqueID,local_name_of_udf
	
	Example:
	
	winnt /u:answ.txt /s:z:\ /t:c: /udf:userid1,z:\udf.txt
	
	ADDITIONAL INFORMATION
	----------------------
	
	Sample answer file used for reference:
	
	     [Unattended]
	     NoWaitAfterTextMode = 1
	     NoWaitAfterGUIMode = 1
	     FileSystem = LeaveAlone
	     ExtendOemPartition = 0
	     ConfirmHardware = No
	     NtUpgrade = no
	     Win31Upgade = no
	     OverwriteOemFilesOnUpgrade = yes
	     TargetPath = winnt
	
	     [GuiUnattended]
	     OemBlankAdminPassword = 1
	     DetachedProgram = "C:\REGINI.EXE"
	     Arguments = "C:\CHANGEIT.INI"
	
	     [UserData]
	     OrgName = "The Computer Company"
	     ProductID = "123-1234567"
	
	     [NetWork]
	     InstallAdapters = AdaptersList
	     InstallProtocols = ProtocolsList
	
	     [AdaptersList]
	     DECETHERWORKSTURBO = DECParams
	
	     [DECParams]
	     InterruptNumber = 5
	     IOBaseAddress = 768
	     MemoryMappedBaseAddress = 851968
	     InterfaceType = 1
	     BusNumber = 0
	
	     [ProtocolsList]
	     NBF = NetBeuiParams
	
	     [NetBeuiParams]
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q155197 Unattended Setup Parameters for Unattend.txt File
	
	Additional information on Windows NT 4.0 deployment is available on the Microsoft
	web site at http://www.microsoft.com/ under the Windows NT 4.0 Workstation Home
	Page Migration Tools section.
	
	
	Additional query words: prodnt Unattended Setup
	
	======================================================================
	Keywords          : kbsetup kbOPK kbSBK kbfaq
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
