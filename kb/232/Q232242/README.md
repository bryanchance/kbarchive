---
layout: page
title: "Q232242: SMS: Audit16 Stops Responding on Removable Media Drive"
permalink: /kb/232/Q232242/
---

## Q232242: SMS: Audit16 Stops Responding on Removable Media Drive

{% raw %}

	Article: Q232242
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Audit16 stops responding when attempting to audit an Iomega Corp. Zip or Jaz
	drive when no media is in the drive. The following message is displayed
	
	  Unable to read drive x: Abort, Retry, Ignore
	
	where x is the drive letter for the removable media drive. If you insert a disk
	and press the R key to retry, Audit will continue.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date     Time                Size    File name     Platform
	  -----------------------------------------------------------
	
	  5/3/99   9:35pm            135,248   Audit16.exe   x86
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, ensure that a disk is in the removable media drive
	before performing an Audit.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, replace the Audit16.exe file in the
	<SMS_root>\Primsite.srv\Audit\Package\X86.bin directory on the site server
	with the hotfixed version.
	
	NOTE: You can do this automatically by using Hotfix.exe with the provided
	Hotfix.ini file.
	
	Any previous Audit packages that have been distributed will need to be
	refreshed.
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Additional query words: prodsms audit iomega jazz hang hangs hung crash crashed crashes
	
	======================================================================
	Keywords          : kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
