---
layout: page
title: "Q174633: Windows NT May Appear To Be Hung with Kernel Debugger"
permalink: /kb/174/Q174633/
---

## Q174633: Windows NT May Appear To Be Hung with Kernel Debugger

{% raw %}

	Article: Q174633
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A computer running Windows NT version 3.51 or 4.0, appears to stop responding
	(hang). There is no network connectivity to the computer, and there is no mouse
	cursor movement or keyboard input.
	
	CAUSE
	=====
	
	If the kernel-mode debugger is enabled on the affected computer, (the computer
	is booted in debug mode) then the following could be causing the computer to
	stop responding:
	
	A DebugBreak function was called by a Win32 app and there is no user-mode
	debugger specified on the computer. The int 3 will be reflected into the
	kernel-mode debugger, causing the computer to appear like it has stopped
	responding. Going to the computer's kernel debugger will show that the computer
	is at a ntdll!DebugBreakPoint. Simply pressing "g" and Enter will release the
	kernel debugger.
	
	For more information on the kernel debugger, see the following Microsoft
	Knowledge Base articles:
	
	ARTICLE-ID: Q148954
	TITLE : How to Set Up a Remote Debug Session Using a Modem
	
	ARTICLE-ID: Q151981
	TITLE : How to Set Up a Remote Debug Session Using a Null Modem Cable
	
	For information on how to set up a user-mode debugger, see the following
	Microsoft Knowledge Base article:
	
	ARTICLE-ID: Q121434
	TITLE : Specifying the Debugger for Unhandled User Mode Exceptions
	
	MORE INFORMATION
	================
	
	When a Win32 user-mode application calls the DebugBreak function, the
	application causes a breakpoint exception to occur in the current process so
	that the calling thread can signal the debugger and force it to take action.
	
	If there is no user-mode debugger specified to catch the int 3, and the
	kernel-mode debugger is enabled on the computer, the int 3, will be reflected
	into kernel-mode debugger and as a result, the computer appears to stop
	responding.
	
	Additional query words: debugref
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Hardware          : ALPHA PPC x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
