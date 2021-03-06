---
layout: page
title: "Q149259: FIX: Class Not Registered Error When Starting Class Browser"
permalink: /kb/149/Q149259/
---

## Q149259: FIX: Class Not Registered Error When Starting Class Browser

{% raw %}

	Article: Q149259
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): kbenvkbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start the Class Browser, one or more of the following errors appears:
	
	  OLE error code 0x80040154: Class not registered. OLE object is being ignored.
	  Record number 13. OK, or Cancel
	
	Clicking OK and selecting a class library from the Open dialog box causes the
	following Class Browser error to appear:
	
	  Unknown member OLECLASSLIST.
	  Browser: classbrowser
	  Object: classbrowser
	  Method: setbusystate OK, or Cancel
	
	When you click OK or Cancel, the following message appears where xyz is the name
	of the class library you selected:
	
	  Unable to create class list for xyz.vcx
	
	CAUSE
	=====
	
	The Class Browser depends on the Outline Control (Msoutl32.ocx) to be registered
	correctly in the Windows 3.x Reg.dat file. The outline control registration in
	the Reg.dat file is missing or invalid.
	
	RESOLUTION
	==========
	
	Register the Msoutl32.ocx OLE control by running the following command in
	Windows:
	
	  
	
	     C:\VFP\SAMPLES\OLE\REGSVR32.EXE C:\WINDOWS\SYSTEM\MSOUTL32.OCX
	
	To run this command in Windows 95, click Run on the Start menu. To run it in
	Windows 3.x, click Run on the File menu in File Manager.
	
	If running the command does not fix the problem, rebuild the Reg.dat file, and
	run the command again.
	
	For information on how to rebuild the Reg.dat file, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q80393 How to Rebuild the Default Windows Reg.dat File
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft product listed at
	the beginning of this article. This problem was corrected in Microsoft Visual
	FoxPro 3.0b for Windows.
	
	
	MORE INFORMATION
	================
	
	This problem is specific to Visual FoxPro 3.0 running under Microsoft Windows
	3.x. When running Visual FoxPro 3.0 under Microsoft Windows 95 or Microsoft
	Windows NT, the outline control will autoregister itself if needed.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In Windows 3.x, unregister the outline control by running the following
	  command (on the File Manager File menu, click Run):
	
	  
	
	     C:\VFP\SAMPLES\OLE\REGSVR32.EXE C:\WINDOWS\SYSTEM\MSOUTL32.OCX /U
	
	2. Start Visual FoxPro, and then start the Class Browser.
	
	
	Additional query words: VFoxWin buglist3.00 fixlist3.00b
	
	======================================================================
	Keywords          : kbenv kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.00
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
