---
layout: page
title: "Q196284: Controlling Default Behavior for Roaming User Profiles"
permalink: /kb/196/Q196284/
---

## Q196284: Controlling Default Behavior for Roaming User Profiles

{% raw %}

	Article: Q196284
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fea
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	Windows NT Service Pack 4 includes a new feature in the System Policy Editor
	that will allow the administrator to define the default selection for the prompt
	displayed to the user in the event that the locally cached user profile is newer
	than the central profile. This fix requires that the service pack be applied to
	the client workstation.
	
	MORE INFORMATION
	================
	
	These new system policies are located under Default Computer/Windows NT User
	Profiles.
	
	- "Choose profile default operation" allows the administrator to specify which
	  option in the dialog box will be the default -- use the local profile or
	  overwrite it with the server-based copy.
	
	- "Time out for dialog boxes" allows the administrator to determine how long
	  the dialog box waits for the user to decide.
	
	Using these policies, the administrator can set Windows NT to use the local
	profile by default, and set the dialog box time out to 0 seconds. With this
	configuration, the client will automatically use the local profile if it is
	newer than the central profile, and the user will not even be prompted.
	
	As an alternative, these options can be set directly in the registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Add the following value to the registry.
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT
	  \CurrentVersion\Winlogon
	
	  NOTE: The registry key above is all one path; it has been wrapped for
	  readability.
	
	  Value: ChooseProfileDefault
	  Type:  REG_DWORD
	  Values: 0 or 1
	
	  0 = Use Local Profile
	  1 = Download Profile
	
	3. Add the following value to the registry.
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT
	  \CurrentVersion\Winlogon
	
	  NOTE: The registry key above is all one path; it has been wrapped for
	  readability.
	
	  Value: ProfileDlgTimeOut
	  Type: REG_DWORD
	  Range: 0 - 600 (seconds)
	
	Additional query words: spe poledit roving roam
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
