---
layout: page
title: "Q99002: Mac LDF: No Password Assigned When Rebuilding Local Mail File"
permalink: /kb/099/Q99002/
---

## Q99002: Mac LDF: No Password Assigned When Rebuilding Local Mail File

{% raw %}

	Article: Q99002
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When attempting to rebuild a user's local mail file using the Mail Tools Utility
	program from version 3.1 of Microsoft Mail for AppleTalk Networks, the following
	message appears:
	
	  Rebuilding the local mail files will temporarily remove its password
	  protection. The rebuilt file will inherit the password of its first user.
	
	This message indicates that after completing the rebuild of a mail file, the
	locally stored mail file has no password. The first user to sign in to Microsoft
	mail whose name matches the local mail file will have his or her password
	assigned to that local file.
	
	Example:
	
	1. Rebuild the user "User X" locally stored mail file using the Mail Tools
	  Utility program.
	
	2. After rebuilding the mail file, rename the local mail file to "User 1"
	  (without the quotation marks).
	
	3. Sign in to Mail as "User 1" at that workstation.
	
	4. The password that was entered during the sign-in process for User 1's mail
	  account will be assigned to the local mail file. User 1 can now access any of
	  User X's mail that is stored locally.
	
	MORE INFORMATION
	================
	
	It is highly recommended that the Mail Tools Utility program not be distributed
	to unauthorized personnel.
	
	
	Additional query words: 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
