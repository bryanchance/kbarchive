---
layout: page
title: "Q224600: RPC Application Causes AV When Dereferencing Freed Connection"
permalink: /kb/224/Q224600/
---

## Q224600: RPC Application Causes AV When Dereferencing Freed Connection

{% raw %}

	Article: Q224600
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): winnt:4.0,5.5
	Operating System(s): 
	Keyword(s): kbWinNT4sp6fix
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An application using the remote procedure call (RPC) transport, such as the
	Microsoft Exchange Server information store, may display an access violation
	error message. The error message is displayed because of a general protection
	fault that may occur when the Windows NT Remote Procedure Call Common Server
	Transport module is under stress.
	
	CAUSE
	=====
	
	The Remote Procedure Call Common Server Transport module can attempt to
	dereference a buffer within a connection that has already been freed under high
	stress conditions.
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or the
	individual software update. For information on obtaining the latest service
	pack, please go to:
	
	- http://www.microsoft.com/Windows/ServicePacks/
	
	-or-
	
	- Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For information on obtaining the individual software update, contact Microsoft
	Product Support Services. For a complete list of Microsoft Product Support
	Services phone numbers and information on support costs, please go to the
	following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT Server version 4.0, Terminal Server Edition Service Pack 6.
	
	MORE INFORMATION
	================
	
	If the correct Windows NT symbols are installed, the resulting Dr. Watson log
	may have a stack dump similar to the following sample dump:
	
	Application exception occurred:
	
	       App: exe\store.dbg (pid=334)
	       When: 11/23/1998 @ 9:3:26.687
	       Exception number: c0000005 (access violation)
	
	State Dump for Thread Id 0x26a
	
	function: COMMON_ServerReceive
	       74fa42f7 7e4e             jle     COMMON_ServerReceive+0xc2 
	       74fa42f9 6603f8           add     di,ax
	       74fa42fc 6683ff10         cmp     di,0x10
	       74fa4300 72d9             jb      COMMON_ServerReceive+0x56 
	FAULT ->74fa4302 f6430410         test    byte ptr [ebx+0x4],0x10      
	       74fa4306 756b             jnz     COMMON_ServerReceive+0xee 
	       74fa4308 8a4309           mov     al,[ebx+0x9]                                                                      
	                                                                                                  
	*----> Stack Back Trace <----*                                                                     
	                                                                                                  
	FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name                                
	2350fef8 74fa2214 00218744 2350ff88 2350ff84 00000000 
	rpcltscm!COMMON_ServerReceive 
	2350ff2c 77e18c00 00169698 2350ff58 2350ff88 2350ff84
	rpcltscm!COMMON_ServerReceiveAny
	2350ff60 77e1a587 2350ff8c 2350ff88 2350ff84 16640528
	rpcrt4!TRANS_ADDRESS::TransReceive
	2350ff90 77e1ac1c 77e15eaf 001695b8 2350ffec 74fa426c
	rpcrt4!OSF_ADDRESS::ReceiveLotsaCalls
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT4sp6fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:4.0,5.5
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
