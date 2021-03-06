---
layout: page
title: "Q150003: FIX: &#95;&#95;vfptr Elements Are Not Properly Displayed in Debugger"
permalink: /kb/150/Q150003/
---

## Q150003: FIX: &#95;&#95;vfptr Elements Are Not Properly Displayed in Debugger

{% raw %}

	Article: Q150003
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbDebug kbide kbVC500fix
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Integrated Debugger, used with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 4.0, 4.1, 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you view the theApp variable in an AppWizard-generated MFC application, the
	element values of __vfptr are not properly displayed in the debugger. For an
	example, please see the "More Information" section of this article.
	
	RESOLUTION
	==========
	
	Drag the address of __vfptr into the memory window, view the data in long-hex
	format, and notice that the addresses to which the __vfptr variable points
	appear.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	Example
	-------
	
	1. Create a default AppWizard MFC application. In the InitInstance(), view the
	  theApp variable in the watch window.
	
	2. Expand the theApp variable to view the following tree structure:
	
	     theApp
	      CWinApp
	       CWinThread
	        CCmdTarget
	         CObject
	           __vfptr = 0x00405118   // This is correct
	
	Under Windows NT:
	
	            [0] CXX0030: Error: expression cannot be evaluated
	            [1] CXX0030: Error: expression cannot be evaluated
	            [2] CXX0030: Error: expression cannot be evaluated
	            [3] CXX0030: Error: expression cannot be evaluated
	            [4] CXX0030: Error: expression cannot be evaluated
	
	Under Windows 95 (All values are incorrect):
	
	            [0] 0xf000e681
	            [1] 0xf000ff47
	            [2] 0xf000ff47
	            [3] 0xf000ff47
	            [4] 0xf000ff47
	
	Additional query words: kbVC400bug
	
	======================================================================
	Keywords          : kbDebug kbide kbVC500fix 
	Technology        : kbVCsearch kbAudDeveloper kbIntegratedDebugger
	Version           : winnt:
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
