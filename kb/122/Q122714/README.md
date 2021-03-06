---
layout: page
title: "Q122714: ADT: Data Outline Control Events Not Triggered"
permalink: /kb/122/Q122714/
---

## Q122714: ADT: Data Outline Control Events Not Triggered

{% raw %}

	Article: Q122714
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:2.0,7.0
	Operating System(s): 
	Keyword(s): kbinterop
	Last Modified: 25-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Access Developer's Toolkit, versions 2.0, 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Novice: Requires knowledge of the user interface on single-user computers.
	
	Code assigned to a Data Outline control's event (such as the DoRowClick,
	DoRowDblClick, or DoKeyPress event) does not run when the event occurs.
	
	CAUSE
	=====
	
	The Data Outline control's SendMouseEvents and SendKeyboardEvents properties are
	not set to True. The default for both properties is False.
	
	RESOLUTION
	==========
	
	Set the Data Outline control's SendMouseEvents and SendKeyboardEvents properties
	to True to enable the triggering of mouse and keyboard events by the Data
	Outline control. To set the SendMouseEvents and SendKeyboardEvents properties to
	True, follow these steps:
	
	1. Open the form containing the Data Outline control in Design view.
	
	2. Using the right mouse button, click the Data Outline control.
	
	3. On the shortcut menu, point to Data Outline Control Object, and then click
	  Properties.
	
	4. Click to select the SendMouseEvents and SendKeyboardEvents check boxes, and
	  then click OK.
	
	Note that you need only select the appropriate property for the type of events
	you want the Data Outline control to process. For example, if you want the Data
	Outline control to process only mouse events, click to select only the
	SendMouseEvents check box.
	
	REFERENCES
	==========
	
	For more information about the SendMouseEvents property, search for
	"SendMouseEvents," and then "SendMouseEvents Property" using the OUTL1016.HLP
	Help file included with the Microsoft Access Developer's Toolkit.
	
	For more information about the SendKeyboardEvents property, search for
	"SendKeyboardEvents," and then "SendKeyboardEvents Property" using the
	OUTL1016.HLP Help file included with the Microsoft Access Developer's Toolkit.
	
	NOTE: In the Microsoft Access Developer's Toolkit for Windows 95 version 7.0, the
	Help file is called MSDBOUTL.HLP.
	
	NOTE: The Microsoft Office 97, Developer's Edition (ODE), does not include the
	Data Outline control. However, for backward compatibility, Microsoft has
	released an Office 97-compatible version of the Data Outline control on the
	World Wide Web. This updated version has no documentation. To obtain a copy of
	the updated Data Outline control, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q162359 ACC97: Access 97 Data Outline ActiveX Control Available in Download
	  Center
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop 
	Technology        : kbAudDeveloper kbAccessSearch kbAccessDevTK200 kbZNotKeyword3 kbAccessDevTK700
	Version           : WINDOWS:2.0,7.0
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
