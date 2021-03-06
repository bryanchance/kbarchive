---
layout: page
title: "Q282228: Terminal Server Random &quot;Stop 0x0000001E&quot; Error Message"
permalink: /kb/282/Q282228/
---

## Q282228: Terminal Server Random &quot;Stop 0x0000001E&quot; Error Message

{% raw %}

	Article: Q282228
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Windows NT Server 4.0-based computer that is a Terminal Server may stop
	responding (crash) and display the following error message on a blue screen in
	Win32k.sys:
	
	    STOP 0x0000001E (0xc0000005, 0xa30818d4, 0x00000000, 0x00000004)
	
	CAUSE
	=====
	
	This problem can occur if the Windows NT Server 4.0-based computer that is a
	Terminal Server is trying to flush the palette while destroying the thread info.
	The pointer to the window is partially destroyed and returns a NULL value when
	referenced.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT Server 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time         Size         File name     Platform
	  ------------------------------------------------------------
	  3/27/2001   12:20 P.M.     170,256    Gdi32.dll     Intel
	  7/11/2000    2:10 P.M.      47,456    User.exe      Intel
	  7/11/2000    5:44 P.M.     331,536    User32.dll    Intel
	  4/12/2001   10:35 A.M.   1,279,824    Win32k.sys    Intel
	  3/1/2001     6:19 P.M.     195,856    Winsrv.dll    Intel
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT Server 4.0, Terminal
	Server Edition.
	
	MORE INFORMATION
	================
	
	0: kd> .bugcheck
	Bugcheck code 0000001E
	Arguments c0000005 a30818d4 00000000 00000004
	
	1: kd> !trap bd223d64
	eax=00000000 ebx=e119a934 ecx=00000000 edx=00000000 esi=a5190618 edi=e119a948
	eip=a30818d4 esp=bd223dd8 ebp=bd223df8 iopl=3    nv up ei ng nz na po nc
	vip=0    vif=0
	cs=0008  ss=0010  ds=0023  es=0023  fs=0030  gs=0000    efl=00013286
	ErrCode = 00000000
	a30818d4 8b4104           mov     eax,[ecx+0x4]
	
	1: kd> !kv
	ChildEBP RetAddr  Args to Child
	bd223df8 a3054a96 a5190618 bd223e28 80b08aa0 win32k!xxxFlushPalette+0x32
	bd223e14 a30539ad 80b08aa0 00000001 a3053892 win32k!xxxDestroyThreadInfo+0x128
	bd223e28 a30538fb e119a8a8 00000001 e119a8a8 win32k!UserThreadCallout+0xad
	bd223e3c 801a4ec7 e119a8a8 00000001 80b08aa0 win32k!W32pThreadCallout+0x29
	bd223ec4 801a48c1 00000000 bd223f04 00000000 ntkrnlmp!PspExitThread+0x253
	bd223ed8 801a4b94 80b08aa0 00000000 7ffd56e4 ntkrnlmp!PspTerminateThreadByPointer+0x21
	bd223ef4 80148589 00000000 00000000 00000000 ntkrnlmp!NtTerminateThread+0x112
	bd223ef4 77f68587 00000000 00000000 00000000 ntkrnlmp!KiSystemService+0xc9
	7ffd56f0 ffffffff 01230000 00000000 00000000 ntdll!NtTerminateThread+0xb
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
