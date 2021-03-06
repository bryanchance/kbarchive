---
layout: page
title: "Q198135: Combat FS: Overlapping View Windows Appear When Switching to HUD"
permalink: /kb/198/Q198135/
---

## Q198135: Combat FS: Overlapping View Windows Appear When Switching to HUD

{% raw %}

	Article: Q198135
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbdisplay kbimu
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Combat Flight Simulator: WWII Europe Series, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you switch to the Heads Up Display (HUD) in Microsoft Combat Flight
	Simulator, two overlapping view windows may appear on the screen instead of the
	Heads Up Display forward view.
	
	CAUSE
	=====
	
	This behavior can occur if all of the following conditions are true:
	
	- You are running Combat Flight Simulator in a window.
	- A secondary view window is already open.
	- An AccelGraphics AccelSTAR II 3D display adapter is installed in your
	  computer.
	- You are using version 4.10.01.4700 or earlier of the Permedia video driver
	  for the AccelGraphics AccelSTAR II 3D display adapter.
	
	RESOLUTION
	==========
	
	To resolve this issue, download and install the latest Permedia video driver for
	the AccelGraphics AccelSTAR II 3D display adapter from the following
	AccelGraphics Web site:
	
	  http://www.accelgraphics.com/drivers.htm
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	Additional query words: 1.00 msgame combatfs cfs card screens multiple
	
	======================================================================
	Keywords          : kb3rdparty kbdisplay kbimu 
	Technology        : _IKkbbogus kbGamesSearch kbCombatFlightSim kbCombatFlightSimSearch kbSimSearch
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
