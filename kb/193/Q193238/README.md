---
layout: page
title: "Q193238: HOWTO: Run Automation Manager as a Windows NT Service"
permalink: /kb/193/Q193238/
---

## Q193238: HOWTO: Run Automation Manager as a Windows NT Service

{% raw %}

	Article: Q193238
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0; winnt:4.0
	Operating System(s): 
	Keyword(s): kbAutomation kbRegistry _IK964 kbService kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbD
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Windows NT Resource Kit provides two utilities, Srvany.exe and Instsrv.exe,
	that allow for the creation of a user-defined service. This article describes
	how to use these two utilities to set up the Automation Manager (Autmgr32.exe)
	as an Windows NT service.
	
	NOTE: The Microsoft Windows NT 4.0 Resource Kit documents Srvany.exe as an
	unsupported tool. Use this tool at your own risk.
	
	MORE INFORMATION
	================
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	The following steps will allow for the creation of a user-defined Windows NT
	service:
	
	Step-by-Step Example
	--------------------
	
	1. Copy SRVANY.EXE and INSTSRV.EXE to your Windows\System32 directory.
	
	2. Select a name for your service, AutoMan for instance, and install it as a new
	  service by typing the following at an MS-DOS prompt:
	
	  INSTSRV AutoMan C:\windows\system32\SRVANY.EXE (Modify path as necessary)
	
	  If the new service is created successfully, the following should be received:
	
	  The service was successfully added!
	  Make sure that you go into the Control Panel and use
	  the Services applet to change the Account Name and
	  Password that this newly installed service will use
	  for its Security Context.
	
	3. On the taskbar, click the Start button, point to Settings and click Control
	  Panel.
	
	4. In the Control Panel, double-click the Services icon.
	
	5. Select AutoMan from the lists of services, and click Startup.
	
	6. If you want your service to start every time you boot your machine, select
	  Automatic for Startup Type in the Service dialog box. Otherwise, select
	  Manual or Disabled. If you select Manual, you will need to go into the
	  Services utility, select the service, and click the Start or Stop button
	  every time you want to start or stop the service.
	
	7. In the Log On As area, click System Account, select "Allow Service to
	  Interact with Desktop," and then click Ok.
	
	8. Click Close to close the Services control panel.
	
	9. On the taskbar, click the Start button, and then click run.
	
	10. In the Run dialog box, enter "Regedit" (without the quotes) and click OK.
	
	11. Expand the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AutoMan
	
	12. Select the AutoMan key, and from the Edit menu, point to New, and click Key.
	
	13. Set the name of the new key to "Parameters" (without the quotes).
	
	14. Select the Parameters key, and from the Edit menu, point to New, and click
	  the String Value. Set the name to "Application" (without the quotes).
	
	15. On the Edit menu, click Modify. Change the Value data to the path to
	  Autmgr32.exe and click Ok. For example:
	
	  c:\winnt\system32\autmgr32.exe
	
	  NOTE: To run the Automation Manager invisible, add another string value under
	  the Parameters key with the following information:
	
	     Name             Data
	     ----             ----
	     AppParameters    /hidden
	
	16. On the Registry menu, click Exit. If you selected Automatic for Startup Type
	  in step 6, the Automation Manager should start automatically when the
	  machine reboots. Otherwise, open the Services utility from the Control Panel
	  and start the service manually.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q137890 : HOWTO: Create a User-Defined Service
	
	  Q138067 : HOWTO: Hide the Automation Manager
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAutomation kbRegistry _IK964 kbService kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport kbRemoteProg 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0; winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
