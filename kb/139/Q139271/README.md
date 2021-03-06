---
layout: page
title: "Q139271: FIX: Changing Keyboard Compatibility Fails to Update Some Keys"
permalink: /kb/139/Q139271/
---

## Q139271: FIX: Changing Keyboard Compatibility Fails to Update Some Keys

{% raw %}

	Article: Q139271
	Product(s): Microsoft C Compiler
	Version(s): 4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbide kbVC kbVC400bug kbVC410bug kbVC420bug kbVC500fix kbGrpDSTools
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 4.0, 4.1, 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you install Visual C++ version 4.0 or later to include the Developer Studio
	keyboard compatibility, and you then switch to Visual C++ 2.0 compatibility and
	back again, several of the key settings do not revert to Developer Studio.
	
	For example, the Edit category in the Main editor should have CTRL+Y assigned to
	the Redo function for Developer Studio and CTRL+A for Visual C++ 2.0
	compatibility. However, if you change from Developer Studio to 2.0 and back,
	CTRL+A remains the key sequence for the Redo function. In addition, the Compile
	function is CTRL+F7 in the Developer Studio and CTRL+F8 in Visual C++ 2.0. Other
	keys may also be affected.
	
	Switching from Visual C++ 2.0 compatibility to Epsilon and Brief works correctly.
	
	RESOLUTION
	==========
	
	Assuming you have selected Developer Studio as your compatibility option and you
	still have the Visual C++ 2.0 setting enabled, follow these steps:
	
	1. Reset the options to be Visual C++ 2.0 in the Compatibility tab of the
	  Options dialog box, and click the OK button to accept the change.
	
	2. Reset the options to be Developer Studio.
	
	After clicking OK, you can verify the keys are set correctly by inspecting the
	Redo item in the Edit menu; Its shortcut key should be CTRL+Y.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Starting with a fresh installation of Visual C++ 4.0 or later, run the
	  Developer Studio.
	
	2. Look at the Edit menu. Redo should use CTRL+Y as its shortcut key.
	
	3. Set the keyboard compatibility to Visual C++ 2.0.
	
	4. Look at the Edit menu. Redo should use CTRL+A as its shortcut key.
	
	5. Exit Msdev.exe.
	
	6. Restart the Developer Studio.
	
	7. Look at the Edit menu. Redo still uses CTRL+A as its shortcut key.
	
	8. Reset the keyboard compatibility to Developer Studio.
	
	9. Look at the Edit menu. Redo should use CTRL+Y as its shortcut key, but it
	  still uses CTRL+A.
	
	Additional query words: kbVC400bug
	
	======================================================================
	Keywords          : kbide kbVC kbVC400bug kbVC410bug kbVC420bug kbVC500fix kbGrpDSTools 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC410 kbVC420
	Version           : :4.0,4.1,4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
