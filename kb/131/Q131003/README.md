---
layout: page
title: "Q131003: PRB: Setting DECIMALS to 15 or More Produces Incorrect Result"
permalink: /kb/131/Q131003/
---

## Q131003: PRB: Setting DECIMALS to 15 or More Produces Incorrect Result

{% raw %}

	Article: Q131003
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.6a,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, version 2.6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use SET DECIMAL to set DECIMAL to 15 or more, certain mathematical
	calculations produce an incorrect result.
	
	CAUSE
	=====
	
	Some numbers when represented in a floating point format have no exact
	representation. For example, this is 1/3 where as .33333333 is in fact slightly
	less than 1/3.
	
	However, some numbers that do have exact floating point representations still
	exhibit this behavior. See the "Steps to Reproduce Behavior" section for an
	example.
	
	STATUS
	======
	
	Microsoft is researching this issue and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Launch Visual FoxPro.
	
	2. In the Command window, enter the following, one line at a time:
	
	     SET DECIMALS TO 14
	     ? 32.16/4
	
	3. Observe the results in the active output window. You should see
	  8.04000000000000. This is exactly correct.
	
	4. Repeat step 2, but this time set decimals to 15.
	
	5. Observe the results. You should see 8.039999999999999. This is incorrect, and
	  demonstrates this problem.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro260a kbVFP300
	Version           : WINDOWS:2.6a,3.0
	
	=============================================================================
	

{% endraw %}
