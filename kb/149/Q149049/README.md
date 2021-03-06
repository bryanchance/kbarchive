---
layout: page
title: "Q149049: PRB: Compiled In-Process Server Used Before IDE Server"
permalink: /kb/149/Q149049/
---

## Q149049: PRB: Compiled In-Process Server Used Before IDE Server

{% raw %}

	Article: Q149049
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbVBp400 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A request for an object provided by both a compiled OLE server dynamic-link
	library (DLL) and an instance of the OLE server running in the Visual Basic for
	Windows integrated design environment (IDE) is filled by the compiled DLL.
	
	WORKAROUND
	==========
	
	It is possible to test the execution of what will become an OLE DLL in the IDE
	when you have a previously compiled DLL. To accomplish this functionality
	temporarily unregister the previously compiled DLL using Regsvr32.exe. Then
	reregister the DLL by using Regsvr32.exe. For example:
	
	Unregister the previously compiled DLL as follows:
	
	  regsvr32.exe -u DLLName.DLL
	
	Reregister the DLL as follows:
	
	  regsvr32.exe DLLName.DLL
	
	If you make a new DLL while still working, Visual Basic for Windows registers it
	when the DLL is made with the "Make OLE DLL" command.
	
	Steps to reproduce problem
	--------------------------
	
	1. Start an instance of the 32-bit edition of Visual Basic 4.0 for Windows.
	
	2. Click Class Module on the Insert menu to add a class module to the project.
	
	3. Change the following properties on the new class module to the following:
	
	        Instancing: 2 - Creatable Multiuse<BR/>
	        Public:     True
	
	4. Add the following code to the class module:
	
	        Public Sub Test()
	           MsgBox "In DLL"
	        End Sub
	
	5. Click Module on the Insert menu to insert a new code module.
	
	6. Add the following code to the code module:
	
	        Public Sub Main()
	           'do nothing
	        End Sub
	
	7. Click Options on the Tools menu to open the Options dialog box. Switch to the
	  Project tab and change the following settings:
	
	  Startup Form: Sub Main
	  Project Name: DLLandIDE
	  Startmode: OLE Server
	
	8. Click "Make OLE DLL File..." on the File menu to create a compiled OLE DLL.
	
	9. Click Options on the Tools menu to again open the Options dialog box. Switch
	  to the Project tab and type in the name of the DLL generated in step 8 in the
	  Compatible OLE Server text box.
	
	10. Click "Make OLE DLL File..." to recompile the DLL.
	
	11. Change the line of code in the Test subroutine contained in the class module
	  from "In DLL" to "In IDE."
	
	12. Press F5 or click Start on the Run menu to run the server in the IDE.
	
	13. Start another instance of the 32-bit edition of Visual Basic for Windows,
	  and add the following code in the Form_Click event to the default form,
	  Form1:
	
	         Private Sub Form_Click()
	            Dim MyObj As Object
	
	            Set MyObj = CreateObject("DLLandIDE.Class1")
	            MyObj.Test
	         End Sub
	
	14. Step through the code in the client program and see that the text of the
	  message box displayed by the Test method contains "In DLL" and not "In IDE."
	
	MORE INFORMATION
	================
	
	Generally, OLE automation clients receive objects from an instance of an OLE
	server running in the Visual Basic for Windows IDE before they receive objects
	from a compiled server. Visual Basic for Windows accomplishes this functionality
	by temporarily adding or modifying registry keys when an IDE server is started
	and then restoring the original settings when the server is stopped. This was
	done to make debugging of OLE servers as easy as possible. However, if a server
	has previously been compiled into an OLE DLL, then objects are provided from
	that compiled DLL before they are provided by a server running in the IDE.
	
	The reason for this behavior is rooted in the search path OLE uses when
	attempting to create an object. This search path is listed below:
	
	- Inprocess server of same bitness
	
	- 32-bit local server (for 16-bit clients under a Microsoft Win32 operating
	  system)
	
	- Local server of same bitness
	
	- Local server of other bitness
	
	Servers running in the IDE are always out-of-process. When a request for an
	object is made, OLE encounters the previously compiled in-process server before
	it encounters the one running in the IDE, and so it creates the object from that
	DLL.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : WINDOWS:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
