---
layout: page
title: "Q268722: Access Violation in Cmd.exe Calling CreateProcess()"
permalink: /kb/268/Q268722/
---

## Q268722: Access Violation in Cmd.exe Calling CreateProcess()

{% raw %}

	Article: Q268722
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Parent programs that spawn a child program pass an environment block to the
	spawned child. In cases in which an extremely long path (more than 1,900 bytes)
	exists in the parent environment, an access violation may occur during the
	startup of a child process. For example, this might occur when a Setup program
	(as a parent) starts another program as a child process.
	
	The actual supported length for a path statement is 1,024 characters. Typically,
	a "Path too long" error message is generated when the path exceeds approximately
	1,900 bytes. However, an extremely long path (more than 1,024 bytes but less
	than the amount that triggers the "Path too long" error message) may still
	generate an error message when a child process is spawned.
	
	As the parent spawns a child process (calling CreateProcess), a new Cmd.exe
	session is started and some expansion of the inherited environment block occurs.
	The following error message may occur when the new environment block is
	initialized for the child process:
	
	  Cmd.exe - Application Error
	
	  The instruction at "0x77f64bab" referenced memory at "0x0067006f". The memory
	  could not be "written".
	  Click on OK to terminate the application.
	
	CAUSE
	=====
	
	An incorrect initialization of a buffer is occurring.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time    Size     File name  Platform
	  ------------------------------------------------
	  07/20/2000  03:02p  208,144  Cmd.exe    Intel
	
	
	
	WORKAROUND
	==========
	
	To work around this issue, shorten the path statement length.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTSsearch kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400search kbWinNTS400 kbWinNTW400sp6 kbWinNTW400SP6a
	Version           : winnt:4.0,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
