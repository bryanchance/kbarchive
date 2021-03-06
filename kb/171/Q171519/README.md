---
layout: page
title: "Q171519: FIX: Removing Function Causes Binary Compatibility Error"
permalink: /kb/171/Q171519/
---

## Q171519: FIX: Removing Function Causes Binary Compatibility Error

{% raw %}

	Article: Q171519
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you recompile an ActiveX DLL with binary compatibility after changing the
	interface, Visual Basic will not always warn you. However, this action will
	result in an incompatible interface.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 2, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q171554 INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 2
	
	MORE INFORMATION
	================
	
	Changing the interface to an ActiveX DLL (such as changing the arguments in a
	function or removing a function) should result in Visual Basic warning you of
	the change when you try to compile the new DLL. However, this may not happen.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new ActiveX DLL in Visual Basic 5.0.
	
	2. Cut and paste the following code to the Class1 Class Module:
	
	         Public Enum Test
	           Larry
	           Curly
	           Moe
	         End Enum
	
	         Public Sub Test()
	           ' This comment is so this sub compiles
	         End Sub
	
	3. Under the Project | Project Properties | Component menu, make sure the
	  project's version compatibility is set to "Project Compatibility." (It should
	  default to this setting.)
	
	4. Compile Project1.DLL.
	
	5. Comment out the Test Sub.
	
	6. Under the Projects | Properties | Component menu, switch the projects version
	  compatibility to "Binary Compatibility." Make sure the compatible version
	  file is Project1. (This is the default setting.)
	
	7. Compile Project1 again. This time, save the filename as Project2. Visual
	  Basic will compile the DLL without any complaints although it should raise a
	  'broken compatibility' warning dialog box.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbGrpDSVB kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
