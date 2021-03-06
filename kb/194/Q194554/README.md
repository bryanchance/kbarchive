---
layout: page
title: "Q194554: WD97: Error Running WinFax Macros in SR-2"
permalink: /kb/194/Q194554/
---

## Q194554: WD97: Error Running WinFax Macros in SR-2

{% raw %}

	Article: Q194554
	Product(s): Word 97 for Windows
	Version(s): Service Release 2
	Operating System(s): 
	Keyword(s): kb3rdparty kbdta
	Last Modified: 23-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows, version Service Release 2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install Microsoft Word 97 Service Release 2 (SR-2), you may find that
	WinFax Pro is unable to find the fax number in the document when you attempt to
	use the fax macros supplied with WinFax Pro.
	
	CAUSE
	=====
	
	There has been a change in the nature of the selection in a table,
	
	resulting from a change in the Find and Replace functionality in Word. This
	
	change in functionality has caused the WinFax macros (which are written in
	WordBasic) to malfunction.
	
	
	WORKAROUND
	==========
	
	To work around this issue, use either of the following methods.
	
	Method 1
	--------
	
	Make sure the fax number is not inside a table cell.
	
	Method 2
	--------
	
	Use Visual Basic for Applications to rewrite the WinFax Pro macros.
	
	NOTE: The current WinFax macros are converted WordBasic macros, using the
	WordBasic object. It is only with the WordBasic object that this problem exists.
	This problem would not exist in Visual Basic for Applications.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Word 97 Service
	Release 2 (SR-2).
	
	This problem was fixed in Word 2000.
	
	MORE INFORMATION
	================
	
	WinFax macros are run when you use the Find feature (on the Edit menu, click
	Find) to look through the document for the fax number. The fax number must be
	formatted with the WfxFaxNum style and cannot be inside a table.
	
	In the following situations, you may receive an error message when you run WinFax
	Macros.
	
	Scenario 1
	----------
	
	If the fax number is not formatted with the WfxFaxNum style, you get the
	following error message:
	
	  Error, The WfxFaxNum style has not been applied to this document. The Macro
	  cannot continue.
	
	Scenario 2
	----------
	
	If you have a blank cell formatted with the WfxFaxNum style, you get the
	following error message:
	
	  Error 1: DDE Syntax Error: "Fax number must be specified"
	
	Scenario 3
	----------
	
	If you have a fax number formatted with the WfxFaxNum style in a table, you get
	the following error message (only occurs in SR-2):
	
	  DDE Syntax Error: "Fax number must be specified"
	
	  or
	
	  (WordBasic) "503: Process failed in other application"
	
	NOTE: If you have a fax number formatted with the WfxFaxNum style outside of a
	table, the macro runs correctly.
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbdta 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2 kbWord97SR2
	Version           : :Service Release 2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
