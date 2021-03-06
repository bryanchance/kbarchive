---
layout: page
title: "Q246130: PRB: MSDN Library Problems Installing to Jazz and Zip Drives"
permalink: /kb/246/Q246130/
---

## Q246130: PRB: MSDN Library Problems Installing to Jazz and Zip Drives

{% raw %}

	Article: Q246130
	Product(s): Microsoft Developer Network
	Version(s): October 99
	Operating System(s): 
	Keyword(s): kbHTMLHelp kbMSDN kbDSupport kbGrpDSTools
	Last Modified: 05-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network (MSDN) October 99 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	This article addresses a problem installing the Microsoft Developer Network
	(MSDN) Library to an Iomega Jazz or Zip drive. This problem first appeared with
	the release of the October 1999 MSDN Library.
	
	When launching or using the MSDN Library, the following error message appears:
	
	  "Please insert the disk labeled 'Installed MSDN Collection's local directory'
	  into drive g:." (where g: is the drive letter of your Iomega Jazz drive)
	
	CAUSE
	=====
	
	The volume name of the MSDN Library CD is recorded incorrectly in the file
	Hhcolreg.dat.
	
	RESOLUTION
	==========
	
	There are two solutions for this problem:
	
	- Rename the volume of the Jazz or Zip drive.
	
	- Edit the Hhcolreg.dat to point to the volume name of the Jazz or Zip drive.
	
	Both solutions require opening the file Hhcolreg.dat with a text editor, such as
	Notepad. On Windows 95, Windows 98, and Windows NT 4.0, Hhcolreg.dat is located
	in the %WinDir%\Help directory. On Windows 2000, Hhcolreg.dat is in Documents
	and Settings\All Users\Application Data\Microsoft\HTML Help.
	
	The first and simplest solution is to change the volume label of the Jazz or Zip
	drive to match the volume label in the Hhcolreg.dat file.
	
	1. Once the Hhcolreg.dat file is open in the text editor, search for Volume
	  value=.
	
	2. Check if the TitleString value in the same section is set to Installed MSDN
	  Collection's local directory. If not, continue searching.
	
	3. Copy the Volume value. For example, the Volume value for the English October
	  1999 MSDN Library is DNQ930ENU.
	
	4. In Windows Explorer, navigate to the drive letter of the Jazz or Zip drive.
	
	5. Right-click the drive, and click Properties.
	
	6. In the Label box, paste the MSDN Library volume value. Click OK.
	
	The second method is to change the Hhcolreg.dat file itself. This method is not
	recommended because incorrect modifications of the Hhcolreg.dat can completely
	disable all MSDN Library installations.
	
	1. Once the Hhcolreg.dat file is open in the text editor, search for "Volume
	  value=".
	
	2. Check if TitleString value in the same section is set to Installed MSDN
	  Collection's local directory. If not, continue searching.
	
	3. Change the Volume value to reflect the volume label of your Jazz or Zip
	  drive.
	
	4. Save and close Hhcolreg.dat.
	
	MORE INFORMATION
	================
	
	This problem has reproduced on several different-sized Jazz and Zip drives.
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Perform a custom installation of the October 1999 MSDN Library.
	
	2. Change the path to point to an Iomega Jazz or Zip drive.
	
	3. Select the full-text search index and a few other areas to install from the
	  custom menu.
	
	Setup completes successfully, but when you attempt to launch the MSDN Library,
	the error message appears.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q216109 HOWTO: Troubleshoot MSDN Library Run-Time/Install/Uninstall Problems
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHTMLHelp kbMSDN kbDSupport kbGrpDSTools 
	Technology        : kbMSDNSearch kbZNotKeyword2
	Version           : :October 99
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
