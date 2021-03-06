---
layout: page
title: "Q100947: Port Trapping in Windows 3.0/3.1"
permalink: /kb/100/Q100947/
---

## Q100947: Port Trapping in Windows 3.0/3.1

{% raw %}

	Article: Q100947
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300
	Last Modified: 09-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	In enhanced mode Windows, the I/O permission bitmap (IOPM) is used by the
	virtual machine manager (VMM) to determine whether I/O is permitted at a given
	I/O port. The IOPM is clear when the VMM is initialized, which means that any
	I/O port can be accessed. VxDs can trap specific I/O ports to prevent direct
	access. Therefore, unless a VxD traps a port, direct I/O access is permitted. In
	standard mode, the IOPM is not used, so direct I/O access is always permitted.
	This does not apply to Windows NT.
	
	The sample IOPORT.ZIP lists ports trapped by the standard VxDs included in
	enhanced mode Windows (IOPMPORT.XLS and IOPMPORT.TXT), and an MS-DOS program
	IOPM.EXE, which lists all currently trapped ports. Also, the DT (dump TSS)
	command in WDEB386 lists all currently trapped ports.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	Ioport.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	The IOPM is contained in the task state segment (TSS). The I/O privilege level
	(IOPL) and the I/O permission bitmap determine whether a task is allowed to
	perform I/O. The IOPL determines the minimum privilege level required to perform
	I/O without checking the permission bitmap. For example, if IOPL = 1, then a
	procedure must have a code privilege level (CPL) of 1 or 0 (zero) to perform
	unrestricted I/O. However, if the CPL of the current task is greater than the
	IOPL, or the processor is operating in virtual 8086 mode, then the I/O
	permission bitmap is checked to determine whether I/O is permitted at the
	requested port.
	
	In enhanced mode Windows, CPL is always greater than IOPL, so the IOPM is always
	checked to determine whether direct I/O access is permitted. In standard mode,
	CPL equals IOPL, so the IOPM is never checked.
	
	Each bit in the bitmap corresponds to an I/O port byte address. For example, the
	bit for port address 60 (decimal) corresponds to the 60th bit, or the 4th bit in
	the 8th byte of the bitmap. In enhanced mode Windows, the bitmap is always 8192
	bytes, and the bitmap is initialized to allow I/O at any port.
	
	When a VxD is initialized, it can call Install_IO_Handler to trap specific I/O
	ports. Install_IO_Handler sets the corresponding bits in the IOPM. When a
	trapped port is accessed, the VxD I/O handler will take over and perform the
	appropriate action. Windows maintains a single TSS for all VMs. When a VM switch
	occurs, the TSS IOPM is updated to reflect the local IOPM of the incoming VM.
	Port trapping for a specific port may be disabled locally or globally from a VxD
	by calling Disable_Local_Trapping or Disable_Global_Trapping.
	
	Additional query words: softlib IOPORT.ZIP kbfile
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
