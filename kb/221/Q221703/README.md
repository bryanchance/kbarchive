---
layout: page
title: "Q221703: FIX: Component Gallery Does Not Refresh After Changing Property"
permalink: /kb/221/Q221703/
---

## Q221703: FIX: Component Gallery Does Not Refresh After Changing Property

{% raw %}

	Article: Q221703
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbInternet kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox
	Last Modified: 20-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Changing the properties of a dynamic view folder in the Component Gallery will
	not be automatically reflected when the changes are applied. You must click on
	the dynamic folder in the treeview in order to see the property change in the
	Component Gallery.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start the Component Gallery.
	
	2. Make certain "Advanced editing" is enabled in the Options dialog.
	
	3. Create a new folder.
	
	4. Right-click this new folder and choose Properties.
	
	5. Select the Node tab in the Properties dialog.
	
	6. Enter a URL (such as http://www.microsoft.com) into the Dynamic folder text
	  box.
	
	7. Click OK.
	
	8. Repeat steps 4 - 7 choosing a different URL (such as http://www.msn.com) this
	  time.
	
	After changing the URL, you will notice that the dynamic view does not update to
	display the new web site. Clicking on the dynamic view folder in the treeview
	will refresh the web view to display the new URL.
	
	Additional query words: KBDSE
	
	======================================================================
	Keywords          : kbInternet kbMiscTools kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
