---
layout: page
title: "Q74527: HOWTO: Designing Applications for High Screen Resolutions"
permalink: /kb/074/Q74527/
---

## Q74527: HOWTO: Designing Applications for High Screen Resolutions

{% raw %}

	Article: Q74527
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbDlg kbSDKPlatform kbSysSettings kbWndw
	Last Modified: 10-JUN-1999
	
	3.00 3.10
	WINDOWS
	kbprg
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Every day, the Microsoft Windows graphical environment is run at greater screen
	resolutions and sizes with more colors. This article outlines several guidelines
	to follow to ensure that an application runs well on all video configurations.
	
	MORE INFORMATION
	================
	
	Avoid the following three pitfalls:
	
	- Hard-coded screen sizes. The VGA 640 by 480 standard resolution screen will
	  not be around forever. If more screen area lets the application display more
	  data, let the window grow as big as the user demands. If screen dimensions
	  are important to the application, use the GetSystemMetrics function with the
	  SM_CXSCREEN and SM_CYSCREEN constants to obtain the screen size.
	
	- Scaling all screen output proportional to resolution. Many users prefer high
	  screen resolutions for the extra screen "real estate" they allow, not just
	  for improved readability.
	
	- Centering dialog boxes relative to the screen. On a very large,
	  high-resolution monitor, many applications can run simultaneously without
	  overlapping. Because users expect dialog boxes and notifications to appear
	  near the main application window, position dialog boxes relative to the main
	  application window.
	
	Perform the following five steps:
	
	1. Test the application at all screen sizes. Watch out for poorly scaled objects
	  that may require fine-tuning, oversized windows, and hard-to-read fixed-size
	  text.
	
	2. Take advantage of leftover screen real estate. For example, if an application
	  document does not require the full screen, allow users the option of filling
	  the remaining space with multiple windows, toolbars and other controls, help
	  information, and so forth.
	
	3. Use scaled graphical screen resources where possible. If the application uses
	  a toolbar, icons, pictures, and so forth, Windows metafiles are likely to be
	  more versatile than bitmaps (although perhaps slower). Scaling based on
	  screen resolution is more effective than scaling based on application window
	  size.
	
	4. Use the WM_GETMINMAXINFO message to help Windows decide how big the maximized
	  application window needs to be. Maximizing a text editor application to the
	  full 2048 x 2048 screen size is probably not useful. Maximizing an
	  application at startup is particularly impolite.
	
	5. Optimize window redraws. If a window contains a lot of information, try to
	  redraw the entire window as infrequently as possible. Use the InvalidateRect
	  function to coalesce window update regions into a single repaint. Even if
	  there is not much to draw, many application windows may be open on a
	  high-resolution screen.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly kbDlg kbSDKPlatform kbSysSettings kbWndw 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
