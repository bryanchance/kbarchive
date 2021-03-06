---
layout: page
title: "Q98768: Troubleshooting MS-DOS 6.x and EMM386.EXE"
permalink: /kb/098/Q98768/
---

## Q98768: Troubleshooting MS-DOS 6.x and EMM386.EXE

{% raw %}

	Article: Q98768
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.1,3.11,95
	Operating System(s): 
	Keyword(s): msdos
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	You encounter unexpected behavior (for example, your system stops responding
	[hangs] or a program hangs) when using the version of EMM386.EXE included with
	the following products:
	
	Product                              Version of EMM386.EXE
	
	MS-DOS 6.0                                    4.45
	MS-DOS 6.2 and 6.21                           4.48
	MS-DOS 6.22                                   4.49
	Windows for Workgroups 3.1                    4.44
	Windows for Workgroups 3.11                   4.48
	Windows 95                                    4.95
	
	WORKAROUND
	==========
	
	Use the steps in the following sections to pinpoint and then correct the
	problems.
	
	Troubleshooting MS-DOS 6.x and EMM386.EXE
	-----------------------------------------
	
	1. Turn your machine off, then turn it back on (cold boot) to fully reinitialize
	  the system.
	
	2. Start MS-DOS interactively by pressing the F8 key as soon as the text
	  "Starting MS-DOS..." appears.
	
	3. When prompted to load EMM386.EXE, choose N for No. If the problem persists
	  without loading EMM386.EXE, something other than EMM386.EXE is causing the
	  problem.
	
	4. If the problem disappears when EMM386.EXE is not loaded, edit the CONFIG.SYS
	  file as follows using an ASCII text editor (such as MS-DOS Editor):
	
	  device=c:\dos\emm386.exe x=a000-f7ff nohi noems novcpi nomovexbda notr
	
	  NOTE: If the problem is specific to the use of the CTRL+ALT+DEL key
	  combination (warm boot) and EMM386.EXE, add the ALTBOOT parameter to the
	  above line.
	
	5. Cold boot the machine after making the above changes. If the problem
	  persists, the system may have faulty RAM chips or may require a special
	  machine switch for HIMEM.SYS. In addition, any CMOS settings (such as shadow
	  RAM) may need to be disabled, or the system ROM BIOS may need to be upgraded
	  for compatibility with MS-DOS 6.x. Consult the system vendor for information
	  on CMOS settings and/or the availability of BIOS upgrades.
	
	6. If the problem disappears after loading EMM386.EXE as specified above,
	  EMM386.EXE itself is not the source of the problem. Instead, the problem may
	  be related to some service(s) that EMM386.EXE provides.
	
	If the above procedure corrected the problem, remove each command-line option for
	EMM386.EXE one by one and cold boot the machine. If the problem reappears, use
	the information below to find a resolution.
	
	X=A000-F7FF
	-----------
	
	If excluding the entire upper memory area (UMA) resolves a system problem,
	EMM386.EXE may be scanning too aggressively and setting up upper memory blocks
	(UMBs) on top of some adapter ROM or RAM. Use any available hardware
	documentation (including documentation on the add-on hardware devices such as
	video, network, and disk controller cards) to identify any ROM or RAM present in
	the UMA for that device, and exclude all pertinent regions. If the hardware
	documentation is not available or does not give the required information, you
	can use the Microsoft Diagnostic Utility (MSD) to identify the memory regions.
	
	NOHI
	----
	
	EMM386.EXE has the ability to load a portion of itself into UMBs. If the NOHI
	option corrects the problem with EMM386.EXE, EMM386.EXE may be loading into an
	occupied UMB. (Excluding the appropriate ranges in the UMA may correct this
	problem; see the "X=A000-F7FF" section above.) If all such regions are excluded,
	EMM386.EXE cannot be loaded high on the system, and NOHI must be used. Contact
	the system manufacturer or vendor for additional information on compatibility
	with EMM386.EXE.
	
	NOEMS
	-----
	
	If the NOEMS parameter corrects the problem with EMM386.EXE, EMM386.EXE may be
	inadvertently conflicting with some hardware ROM or RAM address in the UMA when
	attempting to establish an expanded memory (EMS) page frame. If EMS is required
	to run MS-DOS-based applications, use the parameter FRAME= or M<x> (where
	<x> is the defined hexadecimal address) to explicitly specify placement of
	the EMS page frame in a nonconflicting region. If no applications require EMS,
	simply continue to use the NOEMS parameter.
	
	NOVCPI
	------
	
	The NOVCPI switch disables Virtual Control Program Interface (VCPI) support and
	can be used only in conjunction with the NOEMS parameter. If using NOVCPI
	corrects the problem, the application may not be fully compatible with the
	EMM386.EXE VCPI allocation scheme. Either continue using the NOVCPI parameter,
	or do not load EMM386.EXE when using the application.
	
	NOMOVEXBDA
	----------
	
	Some machines use the last kilobyte of conventional memory for an extended BIOS
	Data Area. By default, EMM386.EXE remaps this memory area into the UMA instead
	of conventional memory. If this causes unexpected system behavior, the
	NOMOVEXBDA parameter MUST be used.
	
	NOTR
	----
	
	EMM386.EXE has a detection code to search for the presence of a token ring
	network adapter. This detection code may cause some computers to hang. The NOTR
	switch can be used to disable this search.
	
	MORE INFORMATION
	================
	
	For more information about EMM386.EXE command-line parameters and syntax, refer
	to MS-DOS Help by typing "help emm386.exe" (without quotation marks) at the
	MS-DOS command prompt and pressing ENTER.
	
	Additional query words: 6.22 6.00 6.20 golden emm hang lockup crash tshoot conflict emm386
	
	======================================================================
	Keywords          : msdos 
	Technology        : kbAudDeveloper kbWin95search kbWFWSearch kbZNotKeyword3 kbWFW310 kbWFW311 kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.1,3.11,95
	
	=============================================================================
	

{% endraw %}
