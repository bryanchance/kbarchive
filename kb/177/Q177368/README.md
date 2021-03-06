---
layout: page
title: "Q177368: Bookshelf 96-97: Lookup Reference Does Not Function in Word 97"
permalink: /kb/177/Q177368/
---

## Q177368: Bookshelf 96-97: Lookup Reference Does Not Function in Word 97

{% raw %}

	Article: Q177368
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf 1996-97 for Windows 
	- Microsoft Word 97 for Windows 
	- Microsoft Office 97 Professional Edition for Windows 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When you attempt to use the Lookup Reference feature in Microsoft Word 97 to
	access information in Bookshelf 96-97, you may be prompted for the location of
	the Bs96se.exe file.
	
	CAUSE
	=====
	
	This behavior can occur if both Microsoft Bookshelf Basics and Bookshelf 1996-97
	are installed on the computer. Bs96se.exe is the executable file for Bookshelf
	Basics. Bookshelf Basics is a component of Microsoft Office 97 Professional
	Edition.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove Bookshelf Basics from the computer. To do so, use
	the following steps:
	
	1. Quit all programs that are currently running. To do so, follow these steps:
	
	  a. Restart the computer. When you see the "Starting Windows 95" message,
	     press the F8 key, and then choose Command Prompt Only on the Startup menu.
	
	  b. Start Windows 95 by typing "win" (without the quotation marks) and holding
	     down the SHIFT key for the duration of Windows startup. This prevents any
	     programs from being loaded automatically when Windows starts.
	
	  c. Press CTRL+ALT+DELETE to open the Close Program dialog box.
	
	  d. Quit all programs except Explorer and Systray (which are parts of Windows
	     95). To quit a program, click the program, and then click End Task.
	
	  e. Repeat steps 3-4 until you have quit all unnecessary programs.
	
	  f. Disable any anti-virus or disk tool programs installed on the computer.
	     For information about how to disable these programs, see the printed or
	     online documentation for the program.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. Double-click Add/Remove Programs.
	
	4. On the Install/Uninstall tab, click Microsoft Office 97 Professional Edition,
	  and then click Add/Remove.
	
	5. In the Microsoft Office 97 Setup dialog box, click Add/Remove.
	
	6. In the Options box, click the Microsoft Bookshelf Basics check box to clear
	  it, and then click Continue.
	
	7. Click Yes, and then click OK until you return to Control Panel.
	
	8. Close Control Panel.
	
	MORE INFORMATION
	================
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	If these steps do not correct the problem, use Registry Editor to remove the
	following key from the registry:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ReferenceTitles\BookshelfL
	
	Additional query words: 1996-97 multi media multimedia multi-media mmtitles winword integration
	
	======================================================================
	Keywords          :  
	Technology        : kbWordSearch kbOfficeSearch kbWord97 kbWord97Search kbHomeMMsearch kbZNotKeyword2 kbOffice97Search kbBookshelfSearch kbOffice97 kbBookShelf1996 kbBookShelf1997
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
