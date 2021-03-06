---
layout: page
title: "Q130144: PRB: SourceSafe for Windows Setup Fails w/ Novell VLM.EXE 1.1"
permalink: /kb/130/Q130144/
---

## Q130144: PRB: SourceSafe for Windows Setup Fails w/ Novell VLM.EXE 1.1

{% raw %}

	Article: Q130144
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kb3rdparty kbsetup kbSSafe400 kbSSafe500 kbSSafe600
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft SourceSafe for Windows, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you are trying to install SourceSafe version 3.1 for Windows on a Novell
	server, where the workstation is using Virtual Loadable Module (VLM) version 1.1
	software, an error message occurs during the installation process. You cannot
	complete the installation. This error occurs even after any virus-protection
	software is disabled. Different error messages will appear, depending on which
	Novell server you are installing to.
	
	One of the following error messages will occur:
	
	  Cannot change properties of the file named: <path>\SSD.EXE
	
	
	-or-
	
	  Could not open the file named: <path>\SSD.EXE
	
	
	When you are trying to cancel the installation, you may receive this error
	message:
	
	  Microsoft Test Driver (ds) Error Runtime Error: Undefined Error
	  SETUP.INC(1005)
	
	NOTE: These errors can also occur if you are not using VLM.EXE and the line READ
	ONLY COMPATIBILITY=ON is in your NET.CFG file. If you change this line to READ
	ONLY COMPATIBILITY=OFF, SourceSafe for Windows will install correctly.
	
	CAUSE
	=====
	
	In version 1.1 of VLM.EXE, Novell changed the default value for READ ONLY
	COMPATIBILITY from OFF to ON.
	
	RESOLUTION
	==========
	
	If you are getting a failed installation on a Novell server and the workstation
	is using VLM version 1.1, do one of the following:
	
	- Modify the NET.CFG or SHELL.CFG file. Under the "Network DOS Requestor"
	  section, add the following line:
	
	        READ ONLY COMPATIBILITY = OFF
	
	-or-
	
	- Install SourceSafe locally and then copy all the files to the appropriate
	  network directory.
	
	NOTE: These solutions apply only to Novell workstations using VLM.EXE version
	1.1, which is loaded in the AUTOEXEC.BAT or STARTNET.BAT file. You can determine
	the version of VLM.EXE either by rebooting the workstation and watching for the
	loading of the VLM software or by typing "VLM /D" (without the quotation marks)
	at the command prompt. The /D option displays the diagnostic information
	(including the version number) for the VLM software.
	
	MORE INFORMATION
	================
	
	The Novell products included here are manufactured by a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding these products'
	performance or reliability.
	
	REFERENCES
	==========
	
	For additional information about testing VLMs, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q115423 PRB: Fox for Windows Installation Fails with Novell VLM or NLM
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbsetup kbSSafe400 kbSSafe500 kbSSafe600 
	Technology        : kbSSafeSearch kbAudDeveloper kbZNotKeyword3 kbSSafe310 kbSSafe600 kbSSafe400 kbSSafe500
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
