---
layout: page
title: "Q236951: PRB: VI Projects Do Not Appear or Added to Wrong VSS Database"
permalink: /kb/236/Q236951/
---

## Q236951: PRB: VI Projects Do Not Appear or Added to Wrong VSS Database

{% raw %}

	Article: Q236951
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:6.0,6.0 SP1,6.0 SP2,6.0 SP3
	Operating System(s): 
	Keyword(s): kbVisID kbGrpDSSSafe
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, version 6.0 
	- Microsoft Visual InterDev, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After adding a Visual InterDev project to Source Control you cannot see the
	project in the Visual SourceSafe explorer.
	
	CAUSE
	=====
	
	This can happen if the Visual InterDev project is added to a different Visual
	SourceSafe database than expected. This sometimes happens when Visual SourceSafe
	is installed during the Visual Studio setup, which provides two distinct setup
	opportunities. The option to install Visual SourceSafe occurs both in the Client
	and Server portions of the installation of Visual Studio 6.0. The two
	installations are slightly different, and install to different paths.
	
	The Visual SourceSafe installation in the server portion of Visual Studio setup
	installs Visual SourceSafe Server into \Program Files\Microsoft Visual
	Studio\VSS. This version contains tools for setting up Source Control on remote
	computers that utilize a centralized Visual SourceSafe database.
	
	The Visual SourceSafe installation from the client portion of Visual Studio setup
	installs to \Program Files\Microsoft Visual Studio\Common\VSS. This version of
	Visual SourceSafe is intended for developers to use locally on their computers,
	and does not have the support to set up remote computers to utilize this Visual
	SourceSafe database, specifically Netsetup.exe support.
	
	When Visual InterDev is used to put a Web project under Source Control, it makes
	requests to the FrontPage Server Extensions (FPSE) to check files in to and out
	of Source Control on the users' behalf. The FrontPage Server Extensions attempt
	to locate a Visual SourceSafe database they can use by searching the registry
	for the location of Ssapi.dll. Since both installations of Visual SourceSafe
	install and register this DLL, the setup program that was run last is the DLL
	that is found. The server extensions then move up one folder and read the
	contents of the Srcsafe.ini file for detailed information on implementing Visual
	SourceSafe. Note that this activity occurs on the Web server, and not the client
	where Visual InterDev is installed.
	
	RESOLUTION
	==========
	
	Look in the two paths cited above, or search the hard disk drive for multiple
	versions of the Ssapi.dll. Uninstall multiple copies of Visual SourceSafe, and
	reinstall the version that you want to use. The Server version of Visual
	SourceSafe can be uninstalled from the Add/Remove control panel. The Client
	version of Visual SourceSafe can be uninstalled by running the Visual Studio
	Setup program. Choose Workstation Tools and Components, and then cancel the
	Visual SourceSafe selection in the Add/Remove section.
	
	If you require multiple Visual SourceSafe databases on the Web server and the
	FPSE do not find the database you want, you can either reinstall the version of
	Visual SourceSafe you want the FPSE to use, or you can manually register
	\VSS\Win32\SSAPI.dll for the appropriate installation of Visual SourceSafe for
	the FPSE to use.
	
	To register the DLL manually, click Start, Run, and type:
	
	" regsvr32 <full path to dll>\ssapi.dll " (without the quotation marks)
	
	You should receive a success dialog box if the DLL is registered correctly.
	
	Ensure that the Visual SourceSafe Administrator tool adds user accounts to the
	correct Visual SourceSafe database by clicking Users/Open SourceSafe Database
	and checking the path. Add user accounts to the appropriate Visual SourceSafe
	database for each developer's user name that will be working against the project
	in Visual InterDev. The password field is ignored and may be left blank.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	When you use Change Connection in Visual InterDev, the FrontPage Server
	extensions use the currently registered Ssapi.dll file, and add the Visual
	InterDev project to the correct Visual SourceSafe database.
	
	If the Visual SourceSafe project in the wrong database has file histories that
	you want to preserve, you can use the Archive and Restore utilities in Visual
	SourceSafe to copy the project from one database to another. You should do this
	before following the steps in the Resolution section above, and restore the
	project as the one that you are using in step 4.
	
	REFERENCES
	==========
	
	For additional information about enabling Visual InterDev integration with
	Visual SourceSafe, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q171116 HOWTO: Enable VSS Integration with FrontPage and Visual InterDev
	
	  Q199035 PRB: Solution and Web Files Added to Different Databases
	
	For additional information about using Archive and Restore to copy projects ,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q176909 HOWTO: Move a VSS Database or Project to New Location
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVisID kbGrpDSSSafe 
	Technology        : kbVisIDsearch kbSSafeSearch kbAudDeveloper kbVisID600 kbSSafe600
	Version           : WINDOWS:6.0,6.0 SP1,6.0 SP2,6.0 SP3
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
