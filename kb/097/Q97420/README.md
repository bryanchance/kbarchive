---
layout: page
title: "Q97420: MS-DOS 6 Upgrade Setup Err Msg: Current Drive Must Be Set to A"
permalink: /kb/097/Q97420/
---

## Q97420: MS-DOS 6 Upgrade Setup Err Msg: Current Drive Must Be Set to A

{% raw %}

	Article: Q97420
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may receive the following error message if you attempt to install MS-DOS
	from a drive other than A:
	
	  Current Drive Must be set to A
	
	CAUSE
	=====
	
	This error message can occur when one or more of the following conditions
	exists:
	
	- Your CMOS settings are incorrectly set and do not include your floppy disk
	  drive.
	
	- You are using a high-capacity optical drive with removable disks (called a
	  "floptical" drive) and the device driver for it is incompatible with Setup.
	
	- You are using an external floppy disk drive and the device driver for it is
	  incompatible with Setup.
	
	- You are using a 2.88-megabyte (MB) floppy disk controller. (Some of these use
	  extended BIOS chip sets that are incompatible with Setup.)
	
	WORKAROUND
	==========
	
	If your drive C has at least 9 MB free space, you can work around this problem
	by copying the MS-DOS 6 Upgrade files to your hard disk drive and running Setup
	from your hard disk drive. To do this, use the following steps:
	
	1. Create a temporary directory on your drive C. For example, type "MD DOSTEMP"
	  (without the quotation marks) at the MS-DOS command prompt and then press
	  ENTER.
	
	2. Copy the MS-DOS Upgrade files from each floppy disk to the DOSTEMP directory.
	  For example, type "copy b:\*.* c:\dostemp" (without the quotation marks) at
	  the MS-DOS command prompt and then press ENTER.
	
	3. To run Setup, type "c:\dostemp\setup" (without the quotation marks) at the
	  MS-DOS command prompt and then press ENTER.
	
	
	
	Additional query words: 6.22 6.00 6.20 drive A B upgrade step-up stepup
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
