---
layout: page
title: "Q223443: Streets and Trips 2000: Testing CD-ROM Drive for File Access"
permalink: /kb/223/Q223443/
---

## Q223443: Streets and Trips 2000: Testing CD-ROM Drive for File Access

{% raw %}

	Article: Q223443
	Product(s): Microsoft Automap
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbhw kbsetup kbimu kbHardware
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets and Trips 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Because of physical read limitations of some CD-ROM drives, you may be denied
	access to some of the files and folders on the Microsoft Expedia Streets and
	Trips 2000 compact disc. This article lists those files and supplies a method to
	test your CD-ROM drive.
	
	MORE INFORMATION
	================
	
	To test for specific drive-capacity limitations, attempt to gain access to the
	following files.
	
	  Files                                   Location on disc
	  --------------------------------------------------------
	
	  Data\Usa0409i.dat                            0.06 MB
	  Data\Usaarts.its                             0.42 MB
	  Data\Usam2p.dat                             64.94 MB
	  Data\Usaroads.dat                           69.57 MB
	  Data\Usaroute.dct                           69.58 MB
	  Data\Usaroute.ndx                           73.03 MB
	  Data\Usaroute.vlf                           73.30 MB
	  Data\Usa_cd.mad                            129.52 MB
	  Autorun.inf                                619.15 MB
	  Autousa7.exe                               619.16 MB
	
	The Expedia Streets & Trips 2000 CD-ROM contains 620 MB of data. The final
	file on the CD-ROM is Autousa7.exe.
	
	NOTE: This list contains every file located on the Expedia Streets & Trips
	2000 Run CD-ROM.
	
	Testing Your CD-ROM Drive
	-------------------------
	
	To test the integrity of any files you copy from your CD-ROM drive to your hard
	disk, compare the files using the MS-DOS File Compare program (Fc.exe). You can
	use this test to determine if the CD-ROM subsystem is functioning properly at
	the device driver or hardware level(s).
	
	The Fc.exe program is a useful method for testing problems related to general
	protection (GP) faults or other critical errors (such as read errors or out of
	memory messages) that may occur when you use CD-ROM drives with Windows
	programs.
	
	To test your CD-ROM drive, attempt to copy one of these files to your hard disk.
	
	For information about how to copy files in Windows, click Start, click Help,
	click the Index tab, type "copying, files" (without the quotation marks), and
	then click Display.
	
	NOTE: If you are using Microsoft Windows 98, click Start, click Help, click the
	Index tab, type "copying files, folders" (without the quotation marks), and then
	click Display.
	
	If you receive the following error message
	
	  CDR101: Not Ready
	
	the CD-ROM drive cannot read the disc at the specified location.
	
	If the file is copied, test the file's integrity by using Fc.exe with the /B
	(binary) switch. For example, to compare the Autousa7.exe file on the CD-ROM to
	the Autousa7.exe file you copied to your hard disk, type the following line at
	the MS-DOS command prompt, and then press ENTER
	
	  fc /b <cd-rom>:\Autousa7.exe <drive>:\Autousa7.exe
	
	where <cd-rom> is the drive letter of your CD-ROM drive, and <drive>
	is the drive letter of the hard disk on which Streets and Trips 2000 is
	installed.
	
	If you receive errors, your CD-ROM drive is having problems reading the compact
	disc at that location.
	
	Additional query words: multi multi-media media mm auto-map amap cdrom
	
	======================================================================
	Keywords          : kbhw kbsetup kbimu kbHardware 
	Technology        : kbHomeProdSearch kbExpediaSearch kbExpediaStreets2000
	Version           : WINDOWS:
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
