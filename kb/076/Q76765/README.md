---
layout: page
title: "Q76765: README.TXT: Using Windows with Multimedia Extensions"
permalink: /kb/076/Q76765/
---

## Q76765: README.TXT: Using Windows with Multimedia Extensions

{% raw %}

	Article: Q76765
	Product(s): Miscellaneous Windows Products
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows with Multimedia Extensions, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is contained in the Windows with Multimedia Extensions
	version 1.0 README.TXT file. The Setup program copies this file to the Windows
	with Multimedia Extensions directory.
	
	This information does not apply to later versions of Windows.
	
	MORE INFORMATION
	================
	
	--------------------------
	README.TXT ONLINE DOCUMENT
	--------------------------
	
	USING WINDOWS WITH MULTIMEDIA EXTENSIONS
	========================================
	
	This section describes information you need to know when running
	Windows with Multimedia Extensions or installing the multimedia
	extensions from the CD-ROM.
	
	WINDOWS OPERATING MODES
	-----------------------
	
	Windows runs in three operating modes: real, standard, and 386
	enhanced. Of these operating modes, the Multimedia extensions augment
	the capabilities of Windows standard and 386 enhanced modes with
	sound, photographic-quality images, and animation. The Multimedia
	extensions are designed for data intensive applications and minimally
	require a 80386sx PC platform for performance considerations.
	
	You can run Windows 3.0 in real mode; however, you will be unable to
	use the Multimedia extensions while using Windows real mode.
	
	DISPLAY DRIVER SETTINGS
	-----------------------
	
	MCGA256 Driver
	--------------
	
	When setting up the display driver for Windows with Multimedia, the
	SETUP program and the Display application from  the Control Panel
	adjust several entries of the SYSTEM.INI  file. For the MCGA256 video
	driver, the 386grabber entry in the [boot] section of SYSTEM.INI  is
	assigned the driver vga.gr3 and may not update parts of a DOS box
	window properly.
	
	This may be solved by changing the line in SYSTEM.INI from
	
	  386grabber=vga.gr3
	
	to
	
	  386grabber=v7vga.gr3
	
	Using a Display Driver with VRAM II
	-----------------------------------
	
	The VRAMII video card uses the VGAPAL.DRV video driver shipped with
	Windows with Multimedia. You can use either this video driver or the
	video driver that comes with the card.
	
	The drivers MMV7VGA.DRV and V7VGA.DRV do not support this video card;
	they support the VRAM I card.
	
	WHEN DEVICE DRIVER ASSIGNMENTS BECOME EFFECTIVE
	-----------------------------------------------
	
	Windows with Multimedia loads its waveform, MIDI, joystick, and timer
	drivers at boot time. You can install and change these driver
	assignments at any time with the Drivers Control Panel application;
	however, Windows with Multimedia doesn't make these changes during the
	current Windows session. Instead, it records the changes for the next
	session of Windows. To recognize driver changes once they've been
	recorded, close and restart Windows.
	
	RUNNING TSR PROGRAMS DURING SETUP
	---------------------------------
	
	When you run SETUP for Windows with Multimedia, avoid invoking TSR
	programs while the installation is running. That is, don't interrupt
	the installation by starting TSR programs.
	
	USING SCREEN SAVERS
	-------------------
	
	The Multimedia extensions for Windows include screen saver
	applications, which you can install from SETUP and from the Screen
	Saver Control Panel application. For information about Screen Savers
	included with the Multimedia extensions, see the HyperGuide section
	entitled Appearances, in the Control Panel Concepts. The Control Panel
	is part of the Main Group in HyperGuide.
	
	Third party screen saver applications also exist and can conflict if
	they are loaded concurrently in Windows. The main symptom of a
	conflict is that the system fails to recognize keystrokes and mouse
	movements once the Screen Saver assumes control of the system. To
	remedy this situation, you must disable one of the screen savers.
	
	To keep the Multimedia extensions Screen Saver, remove the third-party
	screen saver from the files listed in the "load=" entry in the
	[windows] section of the WIN.INI file. WIN.INI is located in your
	Windows directory.
	
	To keep the third-party screen saver, you must make two edits:
	
	1. In the WIN.INI file located in your Windows directory, remove
	  SCRNSVR.EXE from the "load=" entry in the [Windows] section.
	
	2. In the SYSTEM.INI file located in your Windows directory, remove
	  the file name assigned to the "SCRNSAVE.EXE=" entry in the [boot]
	  section.
	
	WORKING WITH CD-ROM DRIVES
	--------------------------
	
	To avoid problems, don't change discs in the CD-ROM drive while in the
	middle of an operation (for example, getting a directory listing,
	playing an audio segment from the CD-ROM, or playing an audio CD with
	Music Box).
	
	The MS-DOS COMP utility doesn't work when comparing files on a CD-ROM.
	
	WORKING WITH THE MSCDEX CD-ROM DRIVER
	-------------------------------------
	
	Be careful when installing the CD-ROM driver MSCDEX.EXE from the
	Windows DOS Prompt. MSCDEX doesn't check to find out whether it has
	already been loaded before loading itself. Thus, you might encounter
	situations in which multiple versions of MSCDEX are loaded on top of
	one another. To make sure this doesn't occur, always install MSCDEX
	from an AUTOEXEC.BAT file before starting the Windows graphical
	environment.
	
	MSCDEX can't be loaded into high memory (for example, using LOADHIGH
	in the AUTOEXEC.BAT file).
	
	CALIBRATING JOYSTICKS
	---------------------
	
	Don't use the Joystick Control Panel application to calibrate a
	joystick while running a game or other application that uses the
	joystick.
	
	USING SOUND RECORDER WITH EXCEL 3.0
	-----------------------------------
	
	The Sound Recorder accessory can be used for Object Linking and
	Embedding (OLE) with applications that support OLE. Microsoft Excel
	Version 3.0 allows you to use Sound Recorder to embed up to 32K of
	data. You can link to data larger than 32K if the 32K limit on
	embedded data is too small.
	
	COPYING WINDOWS WITH MULTIMEDIA FILES FROM THE CD-ROM
	-----------------------------------------------------
	
	The files on the Windows with Multimedia CD-ROM may be compressed.
	Compressed files are not usable until they are expanded. Setup and
	Control Panel expand the compressed files as they are copied onto your
	hard disk.
	
	If you need to copy files directly from the CD-ROM without using Setup
	or Control Panel, follow these steps:
	
	1. Copy EXPAND.EXE from the CD-ROM directory \xxxxx onto your hard
	  drive. (This utility expands compressed files to a usable format.)
	
	2. Type the following and press ENTER:
	
	     expand x:<path\filename> y:<path\filename>
	
	   where x: is the CD-ROM drive (source)
	         y: is the disk drive you are copying to (destination)
	
	  The compressed file is expanded as it is copied onto your hard-disk
	  drive.
	
	System files (.SYS) are named SY$ as compressed files. For example,
	MOUSE.SYS is named MOUSE.SY$; HIMEM.SYS, HIMEM.SY$ and so forth. When
	you use Windows Setup to install these files, they are renamed with
	.SYS extensions automatically.
	
	If you use the expand utility to copy .SY$ files onto your hard disk,
	you must change their filename extensions to .SYS. You can use the
	MS-DOS Rename command or you can rename each file as you copy them
	from the CD-ROM with the Expand command.
	
	To rename a file when you expand it, type the following command and
	press ENTER:
	
	  expand x:filename.sy$ c:\windirectory\filename.sys
	
	where x: is the CD-ROM drive (source), filename.sy$ is the name of the
	compressed file you want to copy, \windirectory is the name of your
	windows directory, and filename.sys is the renamed file that will
	appear on your hard disk.
	
	LEARNING ABOUT WINDOWS APPLICATIONS IN HYPERGUIDE
	-------------------------------------------------
	
	The Quick Looks topics in the HyperGuide on-line documentation system
	show how to use the programs provided in the Windows graphical
	environment with multimedia extensions. For easy access to these
	topics, you may want to copy the files that contain them from the
	Windows with Multimedia CD-ROM to your hard disk. (These files may be
	compressed on the CD-ROM; see the instructions in the preceding
	section for copying compressed files.) Use the following procedure:
	
	1. Copy the Quick Look help files from the CD-ROM to your Windows
	  directory. The Quick Look help files have "QL" as the last letters
	  in their base names. If compressed, these files have extensions of
	  .HL$. (For example, MQL.HL$ is the compressed help file for the
	  Windows Program Manager.)  Otherwise, they have extensions of .HLP.
	  If these files are are compressed, you must rename these files so
	  they have extensions of .HLP after you expand them. (For example,
	  you must rename PMQL.HL$ to PMQL.HLP after you expand it.)
	
	2. Copy the file named QLHD.HL$ (if compressed) or QLHD.HLP (if
	  uncompressed) from the CD-ROM to your Windows directory.  This file
	  contains the Table of Contents for the Quick Look topics. If this
	  file is compressed, you must change the filename to QLHD.HLP after
	  you expand the file.
	
	3. Copy the file named QUIKLOOK.IC$ (if compressed) or QUIKLOOK.ICO
	  (if uncompressed) from the CD-ROM to your Windows directory.  This
	  file contains the icon for the Quick Look topics.  If this file is
	  compressed, you must change the filename to QUIKLOOK.ICO after you
	  expand the file.
	
	4. Add a new program item to any Program Manager group for the Quick
	  Look topics. Specify QUIKLOOK.ICO as the icon file for the new
	  program item. Specify the following command line for the program
	  item:
	
	     winhelp qlhd.hlp
	
	Now, anytime you want to learn how to run any Windows application,
	simply select the Quick Look icon you created in step 4. Follow the
	instructions in HyperGuide to learn about the application.
	
	KBCategory: kbref kbdisplay kbsound
	KBSubcategory:
	
	Additional query words: MMWIN kbmm readme
	
	======================================================================
	Keywords          :  
	Technology        : kbWinMultiXSearch kbWinMultiX100
	Version           : :1.0
	
	=============================================================================
	

{% endraw %}
