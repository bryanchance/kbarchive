---
layout: page
title: "Q173939: How to Identify User Who Changed Administrator Password"
permalink: /kb/173/Q173939/
---

## Q173939: How to Identify User Who Changed Administrator Password

{% raw %}

	Article: Q173939
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Enabling auditing for user and group management will generate audit events when
	user or group accounts are changed. However, the events will list the security
	ID (SID) rather than the user name of the user who made the change.
	
	For security purposes, it is often desirable to know the user name of the user
	who made the change. This can be accomplished by auditing changes on the
	registry key corresponding to the Administrator account.
	
	MORE INFORMATION
	================
	
	This procedure should be performed at the console of the primary domain
	controller. This procedure should NOT be attempted over a WAN because of the
	large number of registry changes involved.
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Open User Manager for Domains and select Audit from the Policies menu.
	
	2. Select Audit These Events and then enable Success and Failure audits for File
	  and Object Access events.
	
	3. Click the OK button and close User Manager for Domains.
	
	4. Open REGEDT32.
	
	5. Select the window for the HKEY_LOCAL_MACHINE hive and select the SAM key.
	
	6. Select Permissions from the Security menu.
	
	7. Select the Change Permissions on Existing Subkeys checkbox.
	
	8. Change the ACE for the Administrators local group from Special to Full
	  Control.
	
	9. Click OK to change the permissions.
	
	10. Go to the following key:
	
	  HKEY_LOCAL_MACHINE\SAM\SAM\Domains\Account\Users\000001F4
	
	11. Select Auditing from the Security menu and select the Audit Permission on
	  Existing Subkeys checkbox.
	
	12. Add the Administrators local group to the list of names.
	
	13. Select the Administrators local group in the list of names, and enable
	  Success and Failure auditing for Set Value events.
	
	14. Click the OK button and close Registry Editor.
	
	If you want to restore the default permissions for the Administrators local group
	on the SAM key and its subkeys, give them the Write DAC and Read Control
	permissions only.
	
	When any changes are made to the Administrator account, several events will be
	generated. The event indicating the user who made the change will be:
	
	  ID: 560
	  Source: Security
	  Type: Success Audit
	  Category: Object Access
	
	This event will indicate the user who made the change, and the date and time of
	the change.
	
	Additional query words: screen saver lock password protect
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51,4.0
	Hardware          : x86
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
