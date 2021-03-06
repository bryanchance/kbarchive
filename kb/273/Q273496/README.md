---
layout: page
title: "Q273496: PRB: IIS 5.0 Hangs with Application.Lock and Application.Unlock"
permalink: /kb/273/Q273496/
---

## Q273496: PRB: IIS 5.0 Hangs with Application.Lock and Application.Unlock

{% raw %}

	Article: Q273496
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbASP kbASPObj kbCOMt kbOSWin2000 kbVBp600 kbWebClasses kbWebServer kbGrpDSASP kbDSuppo
	Last Modified: 25-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you debug a Visual Basic WebClass application within the Visual Basic
	Integrated Developer Environment (IDE) on a Microsoft Windows 2000-based
	computer, and you call the Application.Lock and Application.UnLock methods, the
	Web server may stop responding (hang).
	
	CAUSE
	=====
	
	With the introduction of COM+, Internet Information Server (IIS) 5.0 takes
	advantage of the Thread-Neutral Apartment (NA) when you access the Application
	object. As a result, when you explicitly call Application.Lock and
	Application.UnLock from a component, you encounter a deadlock scenario that
	causes the server to stop responding under certain situations.
	
	RESOLUTION
	==========
	
	Do not use Application.Lock and Application.UnLock in your WebClass code when
	you debug.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start Visual Basic. In the New Project dialog box, select IIS Application,
	  and then click Open.
	
	2. In the Project window, click to expand the Designers folder. Right-click
	  WebClass1, and then click View Code from the shortcut menu.
	
	3. Add the following code to the WebClass_OnStart event:
	
	  Application.Lock
	  Application("myvar") = "hello world"
	  Application.UnLock
	
	4. Save the WebClass.
	
	5. On the Debug menu, click Start to run the WebClass. Internet Explorer stops
	  responding, and the page is never displayed in the browser.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q271787 PRB: Application.Lock and Application.UnLock Causes Server to Hang in
	  IIS 5.0
	
	Additional query words:
	
	======================================================================
	Keywords          : kbASP kbASPObj kbCOMt kbOSWin2000 kbVBp600 kbWebClasses kbWebServer kbGrpDSASP kbDSupport kbiis500 
	Technology        : kbVBSearch kbiisSearch kbAudDeveloper kbZNotKeyword6 kbiis500 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
