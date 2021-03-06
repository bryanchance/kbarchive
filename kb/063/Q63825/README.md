---
layout: page
title: "Q63825: Application Cannot Start in Window, Yet Can Run in Window"
permalink: /kb/063/Q63825/
---

## Q63825: Application Cannot Start in Window, Yet Can Run in Window

{% raw %}

	Article: Q63825
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may get the following error message when you try to start a non-Windows
	application in a window under Microsoft Windows version 3.0:
	
	  You cannot run this application while other high-resolution applications are
	  running fullscreen. The application will be suspended until a low-resolution
	  or text application is running fullscreen. Check the PIF settings to ensure
	  they are correct.
	
	However, if you start the same application fullscreen and then switch it into a
	window (by pressing ALT+SPACEBAR), it runs without any problem.
	
	CAUSE
	=====
	
	This behavior often occurs with non-Windows applications that are text based but
	have an initial graphics logo screen. Some applications, such as PFS Write and
	PFS File, have an initial graphics screen bearing the logo of the application.
	Because of this initial graphics screen, the applications cannot start in a
	window. After the initial logo screen is displayed, these and many other
	applications switch to a text-based display. For this reason, after the initial
	graphics screen is displayed, the application can run in a window.
	
	NOTE: "Print preview" or "page preview" screens are usually graphics-type
	displays. Your application may lock up and give you the above error message if
	you attempt to use "print preview" or "page preview" type features while running
	the application in a window.
	
	WORKAROUND
	==========
	
	Unless you can disable or skip this initial logo screen, you must start the
	application in a full screen and then reduce it to a window after it is
	running.
	
	
	MORE INFORMATION
	================
	
	This problem also occurs with a program such as Microsoft Word 5.0 if it is
	started in a text mode other than 25 line mode (such as 43 line mode on an
	EGA/VGA and 50 line mode on a VGA). This is an example of an application that
	ends up in text mode but transitions first through what looks like a graphics
	mode.
	
	Additional query words: 3.00 3.0 3.0a 3.00a 3.10 dosapp
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
