---
layout: page
title: "Q189400: BUG: VBComponents Add Method Cannot Add a Form"
permalink: /kb/189/Q189400/
---

## Q189400: BUG: VBComponents Add Method Cannot Add a Form

{% raw %}

	Article: Q189400
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When attempting to add a Form to a Visual Basic project through the
	IDTExtensibility model, you receive the following error:
	
	  Runtime error '-2147467259 (800004005)':
	  System Error &h80004005(-2147467259). Unspecified error
	
	CAUSE
	=====
	
	This error can occur if you use the Add method of the VBComponents object and
	pass vbext_ct_MSForm as the component type.
	
	vbext_ct_MSForm is not a valid component type; it corresponds to Form3 designers,
	which Visual Basic does not support.
	
	RESOLUTION
	==========
	
	Use the VBComponents AddFromTemplate method. See the MORE INFORMATION Section of
	this article for additional information.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a New Add-In Project in Visual Basic. A form "frmAddIn" will be created
	  automatically, with two command buttons, OK and Cancel.
	
	2. Add the following line to the Click event of the OKButton:
	
	        VBInstance.VBProjects(1).VBComponents.Add (vbext_ct_MSForm)
	
	3. If using Visual Basic 5.0, type "ADDTOINI" in the Immediate (debug) window
	  and press the ENTER key. This step is not necessary if you are using Visual
	  Basic 6.0.
	
	4. Press the F5 key to run the project.
	
	5. Start another instance of Visual Basic with a new standard EXE project.
	
	6. Under the Add-Ins menu, select Add-In Manager, and then select "My AddIn"
	  from the list.
	
	7. Select the "My AddIn" item from the Add-Ins menu.
	
	8. Click OK on the Add-In Form. You will get the error:
	
	  Run-time error '-2147467259 (800004005)':
	  System Error &h80004005(-2147467259). Unspecified error.
	
	Steps To Work Around the Problem
	--------------------------------
	
	1. Add a new form to the add-in project and save it in the Template folder under
	  the Visual Basic folder as Form1.frm. (For example, C:\Program
	  Files\DevStudio\VB\Template), and then remove the form from the project.
	
	2. Change the code in the OKButton_Click event in step 2 above to the following
	  code shown below.
	
	        Private Sub OKButton_Click()
	          VBInstance.VBProjects(1).VBComponents.AddFromTemplate _
	          ("C:\Program Files\DevStudio\VB\Template\Form1.frm")
	        End Sub
	
	  NOTE: Modify the path as appropriate for your environment. In Visual Basic
	  5.0, the default Visual Basic installation path is C:\Program
	  Files\DevStudio\VB. In Visual Basic 6.0, the default path is C:\Program
	  Files\Microsoft Visual Studio\VB98.
	
	3. Repeat steps 3 through 8 in the "Steps to Reproduce the Problem" section.
	  This time a form should be added to your project each time you click OK.
	
	REFERENCES
	==========
	
	Books Online for Microsoft Visual Basic, versions 5.0 and 6.0
	
	Additional query words: kbAddIn kbDSupport KBdSS kbVBp500bug kbVBp600bug kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
