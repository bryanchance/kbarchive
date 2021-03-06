---
layout: page
title: "Q163071: SNA Server Access Violation May Occur If Link Fails to Start"
permalink: /kb/163/Q163071/
---

## Q163071: SNA Server Access Violation May Occur If Link Fails to Start

{% raw %}

	Article: Q163071
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If an underlying link service fails to start, SNA Server may fail with an access
	violation (AV) immediately after it is started. When this happens, the following
	errors occur:
	
	Windows NT application event log errors:
	
	  
	
	  Event ID: 624
	  Source:   SNA Server
	  Description: Creating dump file D:\SNA\Traces\Snadump.log for
	  Snaservr.exe
	
	  Event ID: 4097
	  Source:   DrWatson
	
	  <Ntroot>\Drwtsn32.log will include the following failure information:
	
	  Application exception occurred:
	     Application: exe\snaservr.DBG (pid=447)
	     When: 1/23/1997 @ 14:56:5.593
	     Exception number: c0000005 (access violation)
	
	  [data omitted]
	
	  State Dump for Thread Id 0x23b
	
	  eax=00000000 ebx=004b1c00 ecx=00000000 edx=00000000 esi=00000001
	  edi=00000001
	  eip=003f60eb esp=00baff40 ebp=000700c8 iopl=0         nv up ei pl zr na
	  po nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000
	  efl=00000246
	
	  function: s1pulkiw
	          003f60ce eb37             jmp     s1pulkiw+0x357 (003f6107)
	          003f60d0 8b442414         mov     eax,[esp+0x14]
	  ss:0262e947=???
	          003f60d4 8b5004           mov     edx,[eax+0x4]
	  ds:01a7ea06=???
	          003f60d7 8bc1             mov     eax,ecx
	          003f60d9 25ffff0000       and     eax,0xffff
	          003f60de 8bc8             mov     ecx,eax
	          003f60e0 c1e010           shl     eax,0x10
	          003f60e3 03c1             add     eax,ecx
	          003f60e5 c1c008           rol     eax,0x8
	          003f60e8 0fbfc8           movsx   ecx,ax
	  FAULT ->003f60eb 0fbf4204         movsx   eax,word ptr [edx+0x4]
	  ds:01a7ea07
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  000700c8 00050001 00000000 00000000 0000007a 00020000 snaservr!s1pulkiw
	
	CAUSE
	=====
	
	If SNA Server receives a "lost locality" error from a link service before an
	Open(Link) response is received from the link service, SNA Server attempts to
	log the name of the failing connection by parsing the Open(Link) response. This
	leads to an access violation.
	
	The cause of the link service "lost locality" may vary. In one case, the SNA
	802.2/DLC link service failed to initialize because the token ring adapter cable
	was not inserted into the token ring network. This could have been due to any of
	the following reasons:
	
	- The token ring cable was not inserted.
	
	- The MAU port was inoperative.
	
	- The adapter was configured for 16 Mbps and the token ring network was
	  operating at a 4 Mbps ring speed.
	
	This error caused an "Event 242 error - Invalid adapter <snadlc1>
	configured" error to appear in the log, before the Event 624 error noted above.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the hotfix mentioned below. However, the cause
	of the link service "lost locality" error must be debugged separately.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	2.0, 2.1, 2.11, and 2.11 Service Pack 1. This problem was corrected in the
	latest SNA Server version 2.11 U.S. Service Pack. For information on obtaining
	this Service Pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	Additional query words: sp1 prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ200 kbSNAServ211 kbSNAServ210 kbSNAServ211SP1
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1
	
	=============================================================================
	

{% endraw %}
