---
layout: page
title: "Q168776: SMSINST: Using the Repackager Successfully"
permalink: /kb/168/Q168776/
---

## Q168776: SMSINST: Using the Repackager Successfully

{% raw %}

	Article: Q168776
	Product(s): Microsoft Systems Management Server
	Version(s): WINDOWS:1.0; winnt:1.2
	Operating System(s): 
	Keyword(s): kbnetwork smsinst
	Last Modified: 03-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	- Microsoft Systems Management Server Installer version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The automated procedure for creating an installation package with the Systems
	Management Server Installer is called "repackaging." The repackaging feature of
	the Systems Management Server Installer allows the administrator to install a
	standard application on a reference computer, and have the installation
	duplicated on desktops throughout the organization.
	
	Repackaging begins by clicking Repackage to access the Repackage Installation
	dialog box. In this dialog box, the path to the application's Setup program is
	specified, along with any required command-line options.
	
	Scan the Directories and Registry
	---------------------------------
	
	The Systems Management Server Installer monitors drives and directories during
	the repackage process. By default, the Systems Management Server Installer
	automatically designates to scan the Windows NT drive and all its
	subdirectories, but it is possible to remove directories from the scan. For
	example, if the computer has multiple hard-disk partitions, but the application
	only installs files on one partition, configure the Systems Management Server
	Installer to scan only the one drive. This is done by clicking Change in the
	Repackage Installation dialog box. From the Repackage Installation dialog box,
	drives and directories can be configured in the top portion of the Advanced
	Settings dialog box.
	
	During the installation of the application, which is completed during the
	repackage procedure, it is possible for some temporary files, such as .log or
	.tmp files, to be modified. The temporary files may not be necessary for the
	installation to be successful, but rather a residual effect of the installation.
	The Systems Management Server Installer can be configured to ignore the files
	during the scanning process. Configuration of files to be ignored is
	accomplished by clicking Change in the Repackage Installation dialog box. From
	the Repackage Installation dialog box, files that should be ignored can be
	configured in the bottom portion of the Advanced Settings dialog box.
	
	The repackage process will also capture all changes made to the registry. Special
	attention should be given to registry values that may change (for example, a
	DHCP release and renew with a new address), and are not part of the
	installation. Configure registry values to be ignored by clicking the Change
	button in the Repackage Installation dialog box.
	
	Run Installation
	----------------
	
	After the scanning of directories and the registry is complete, the Setup program
	runs. The application should be installed and configured as required for the
	end-user computer.
	
	Scan the Directories and Registry Again
	---------------------------------------
	
	After the installation and configuration of the application, The Systems
	Management Server Installer performs another scan of the configured drives and
	directories, as well as the registry. An installation script is then produced
	that references all the files copied, icons created, program groups or Start
	menu items created, and registry entries modified.
	
	The Systems Management Server Installer automatically scans the Windows NT drive
	and all its subdirectories. These directories are displayed on the Repackage
	Installation dialog box, so you only have to change it if it is not correct. If
	you want to change it, click Change.
	
	MORE INFORMATION
	================
	
	The following are some things to consider when repackaging an application:
	
	Reference Computer
	------------------
	
	To ensure that a repackaged application will install correctly, your reference
	(or test) computer should be as clean as possible. Many applications share
	files, and if the original setup program detects these files, it may not
	reinstall them. For example, if you want to repackage Microsoft Word and you use
	a reference computer with Microsoft Excel on it for your repackage, some of the
	shared DLL files and files in the Msapps directory may not be installed in the
	repackage operation. Consequently, if Excel is not already installed on your
	target computers, your repackaged Word will not install completely, and may fail
	to run correctly.
	
	Data Conversion
	---------------
	
	If the original setup program does any kind of upgrade or modification of data
	files (such as user database files), the Repackager will fail to capture the
	conversion. Consequently, the Systems Management Server Installer application
	will not install correctly on the target computer. In cases where data
	conversion occurs as part of the original setup, do not use the Repackager
	feature.
	
	Hardware Scans
	--------------
	
	If the original setup program does any kind of hardware detection, a repackaged
	Systems Management Server Installer application may fail.
	
	Shared Network Files
	--------------------
	
	If the original setup program makes any modifications to shared or network files,
	special consideration should be given to the Repackager setup. If the Repackager
	makes modifications to shared files, the installation will probably fail. If the
	Repackager references network files, the installation may fail. Extra testing
	should be performed to ensure that the repackage will run on all clients and
	under all logon names.
	
	Additional query words: prodsms sms
	
	======================================================================
	Keywords          : kbnetwork smsinst 
	Technology        : kbSMSSearch kbSMS120 kbSMSI100
	Version           : WINDOWS:1.0; winnt:1.2
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
