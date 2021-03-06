---
layout: page
title: "Q142796: FIX: Program Generated by GENDBC Cannot be Run in Executable"
permalink: /kb/142/Q142796/
---

## Q142796: FIX: Program Generated by GENDBC Cannot be Run in Executable

{% raw %}

	Article: Q142796
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a program that was generated by the GENDBC utility is included in a
	distributed executable, a "Feature is not available" error message will occur
	when the program is run.
	
	CAUSE
	=====
	
	The GENDBC generated program attempts to use the APPEND PROCEDURES and COMPILE
	DATABSE commands. These commands are not supported in a distributed executable
	as the compiler is not available in the run-time version of Visual FoxPro.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Microsoft Visual
	FoxPro 3.0b for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Run GENDBC on the TASTRADE database.
	
	2. Create a new project.
	
	3. Add the GENDBC-generated program to the project.
	
	4. Build the project into an executable.
	
	5. Exit Visual FoxPro, and run the executable. The "Feature is not available"
	  error will occur.
	
	Additional query words: VFoxWin fixlist3.00b buglist3.00
	
	======================================================================
	Keywords          :  kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
