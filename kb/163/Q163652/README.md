---
layout: page
title: "Q163652: ODE97: Error Msg: ISAM Unable to Register Itself in Custom App"
permalink: /kb/163/Q163652/
---

## Q163652: ODE97: Error Msg: ISAM Unable to Register Itself in Custom App

{% raw %}

	Article: Q163652
	Product(s): Microsoft Access Distribution Kit
	Version(s): 
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 01-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	SYMPTOMS
	========
	
	If your custom application includes any of the ISAM components from the "Add
	redistributable components" screen of the Setup Wizard, you may receive the
	following error message when you run your Setup program on a computer that does
	not have the Microsoft Jet database engine version 3.5 installed:
	
	  <ISAM File> is unable to register itself in the System Registry
	
	CAUSE
	=====
	
	The ISAM drivers require the Jet database engine in order to register themselves
	during setup.
	
	RESOLUTION
	==========
	
	If you want to include ISAM drivers with your custom application, and you are
	not sure if all users who run your Setup program will have Microsoft Access 97
	or another application that uses the Jet database engine, include the Microsoft
	Access run-time version component with your setup files when you run the Setup
	Wizard.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start the Microsoft Office 97 Developer Edition Tools Setup Wizard.
	
	2. Click Next on the first wizard screen to create a new set of setup options.
	
	3. On the "Add the files" screen of the Setup Wizard, add the sample database
	  Northwind.mdb, and click to select the "Set As Application's Main File" check
	  box. Click Next.
	
	4. Click Next on the "Add the shortcuts" screen.
	
	5. Click Next on the "Add the Registry values" screen.
	
	6. On the "Add components" screen, click Xbase ISAM, and then click Finish. You
	  do not need to save the Setup template.
	
	7. After the setup image has been created, run the Setup program for this
	  application on a computer that does not have Microsoft Access 97 or another
	  application that uses the Jet database engine installed. Note that you
	  receive the error message before Setup is finished.
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: Lotus 1 2 3 123 Xbase Paradox Text Foxpro
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbOffice97DevSearch
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
