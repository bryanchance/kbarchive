---
layout: page
title: "Q179813: Underlining Shifted to the Left When Printing from Applications"
permalink: /kb/179/Q179813/
---

## Q179813: Underlining Shifted to the Left When Printing from Applications

{% raw %}

	Article: Q179813
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Underlining may be shifted to the left when you print from applications like
	Microsoft Word for Windows using a Printer Control Language (PCL) driver.
	
	This problem does not occur with PostScript drivers.
	
	CAUSE
	=====
	
	Windows NT 4.0 Graphical Device Interface (GDI) was designed to use device fonts
	to determine scaling and positioning of printed output. The results of
	calculating the width of the underlined text can be truncated with certain point
	sizes. This causes visible differences in the printed document where the
	underlining may be shifted to the left of the actual text by several pixels.
	
	Future version of Windows NT will use True Type fonts to determine positioning
	and scaling of printed output.
	
	RESOLUTION
	==========
	
	Print Text As Graphics is an option that tells the GDI to use True Type fonts
	for determining the positioning and scaling of printed output.
	
	To resolve this problem on a document by document basis in an application such as
	Microsoft Word for Windows, perform the following steps:
	
	1. From the File menu, click Print.
	
	2. Click Properties, then click the Advanced tab.
	
	3. Click the plus sign to expand the folder list for Document Options, then
	  select Print Text As Graphics and click the ON radio button.
	
	To change the document default for all new documents for a specific printer,
	perform the following steps:
	
	1. Click the Start button, point to Settings, and then click Printers.
	
	2. Right-click on the desired printer.
	
	3. Click Document Defaults.
	
	4. Click the plus sign to expand the folder list for Document Options, then
	  select Print Text As Graphics and click the ON radio button.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
