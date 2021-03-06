---
layout: page
title: "Q96480: Fp0779.exe ISDISKIN Utility"
permalink: /kb/096/Q96480/
---

## Q96480: Fp0779.exe ISDISKIN Utility

{% raw %}

	Article: Q96480
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5,2.5a,2.5b,2.6
	Operating System(s): 
	Keyword(s): kbcode kbfile kbSample kbDSupport
	Last Modified: 19-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b, 2.6 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Fp0779.exe is a sample that contains the ISDISKIN utility that provides an
	alternative method of dealing with the "Not Ready Reading Drive A" error
	message.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Fp0779.exe
	  (http://download.microsoft.com/download/fox26dos/Utility/1/DOS/EN-US/Fp0779.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	When a FoxPro program attempts to load a file from a floppy disk and no disk is
	present in the drive or the drive door is open, MS-DOS returns a "Not ready
	reading drive <letter>" message and provides the option to "Abort, Retry,
	Ignore" the error.
	
	To provide an alternative method of dealing with this error, the ISDISKIN utility
	is included in the multiuser version of Microsoft FoxPro versions 1.02 and 2.0
	for MS-DOS. A FoxPro application can call ISDISKIN to determine the status of
	the drive and, if necessary, provide a more appropriate message for the user.
	
	THE TEXT OF FP0779
	------------------
	
	======================================================================
	      Microsoft(R) Technical Support Application Note (Text File)
	                      FP0779: ISDISKIN UTILITY
	======================================================================
	                                                  Revision Date: 2/94
	                                                      1 Disk Included
	
	The following information applies to Microsoft FoxPro(R) versions 1.02,
	2.0, 2.5, 2.5a, and 2.5b for MS-DOS(R).
	
	-----------------------------------------------------------------------
	| INFORMATION PROVIDED IN THIS DOCUMENT AND ANY SOFTWARE THAT MAY     |
	| ACCOMPANY THIS DOCUMENT (collectively referred to as an Application |
	| Note) IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER      |
	| EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED      |
	| WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR       |
	| PURPOSE. The user assumes the entire risk as to the accuracy and    |
	| the use of this Application Note. This Application Note may be      |
	| copied and distributed subject to the following conditions:  1) All |
	| text must be copied without modification and all pages must be      |
	| included;  2) If software is included, all files on the disk(s)     |
	| must be copied without modification (the MS-DOS utility diskcopy is |
	| appropriate for this purpose);  3) All components of this           |
	| Application Note must be distributed together;  and  4) This        |
	| Application Note may not be distributed for profit.                 |
	|                                                                     |
	| Copyright (C) 1993-1994 Microsoft Corporation. All Rights Reserved. |
	| Microsoft, FoxPro, and MS-DOS are registered trademarks and Windows |
	| is a trademark of Microsoft Corporation.                            |
	|---------------------------------------------------------------------|
	
	INTRODUCTION
	============
	
	When a FoxPro program attempts to load a file from a floppy disk and no
	disk is present in the drive or the drive door is open, MS-DOS returns a
	"Not ready reading drive <letter>" message and provides the option to
	"Abort, Retry, Ignore" the error. The ISDISKIN utility on the disk enclosed
	with this Application Note is a binary file that provides an alternative
	method of dealing with this situation. A FoxPro application can call
	ISDISKIN to determine the status of the drive and, if necessary, provide a
	more appropriate message for the user.
	
	NOTE: .BIN routines cannot be used in the Windows environment.
	
	To install ISDISKIN
	-------------------
	
	NOTE: If you are using the multiuser version of FoxPro 1.02 or 2.0,
	ISDISKIN.BIN is already installed in the FOXPRO2\GOODIES\ADDUSER directory
	by default.
	
	1. Insert the enclosed FP0779 disk in your floppy disk drive.
	
	2. Copy Isdiskin.bin to your main FoxPro directory. To do this, type
	  the following at the MS-DOS command prompt and press ENTER
	
	     copy <drive>:\isdiskin.bin <destination>
	
	  where <drive> is the floppy disk drive containing the FP0779 disk
	  and <destination> is the drive and directory where your FoxPro
	  files are located.
	
	  For example, if the FP0779 disk is in drive A, and your FoxPro
	  directory is named FOXPRO25 and is on drive C, type the following
	  command:
	
	     copy a:\isdiskin.bin c:\foxpro25
	
	To use ISDISKIN in a FoxPro program
	-----------------------------------
	
	1. If you are using FoxPro version 2.5 or later or the single-user version
	  of FoxPro version 1.02 or 2.0, issue this command:
	
	     SET DEFAULT TO <FoxPro directory>
	
	  If you are using the multiuser version of FoxPro version 1.02 or 2.0,
	  issue this command:
	
	     SET DEFAULT TO C:\FOXPRO2\GOODIES\ADDUSER
	
	2. Use the LOAD command to load the Isdiskin.bin file.
	
	3. Create a character memory variable. Set the variable to the drive
	  letter for the disk drive to test. For example, create a memory
	  variable called <pvalue> and set it equal to "A:".
	
	4. Use the CALL command to invoke the Isdiskin.bin file with the
	  character memory variable as a parameter.
	
	ISDISKIN returns one of the following values to indicate the status of
	the disk drive:
	
	  Return value     Meaning
	  ----------------------------------------------------------------------
	
	  A:               Drive A tested and a disk is present in drive A.
	  B:               Drive B tested and a disk is present in drive B.
	  0: (zero)        No disk is present in the tested drive.
	
	NOTE: Isdiskin.bin must be loaded each time the drive requires testing. If
	multiple calls are made without reloading and the return value has changed
	from A: to 0:, reinserting a disk will not cause A: to be returned; the
	return value will remain 0:. To use the function reliably, reload it before
	every call.
	
	SAMPLE PROGRAM
	==============
	
	  * If you are using the multiuser version of FoxPro 1.02 or 2.0, use
	  * SET DEFAULT TO C:\FOXPRO2\GOODIES\ADDUSER instead of the
	  * following line.
	  SET DEFAULT TO <FoxPro directory>
	  LOAD isdiskin.bin
	  pvalue = "A:"
	  CALL isdiskin.bin WITH pvalue
	  DO CASE
	  CASE pvalue = "A:"
	     RUN DIR A:
	  CASE pvalue = "0:"
	     WAIT WINDOW "Please put a disk into drive A:"
	  ENDCASE
	
	
	Additional query words: FoxDos AppNote FP0779 softlib kbfile
	
	======================================================================
	Keywords          : kbcode kbfile kbSample kbDSupport 
	Technology        : kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS
	Version           : MS-DOS:2.0,2.5,2.5a,2.5b,2.6
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
