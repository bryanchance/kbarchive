---
layout: page
title: "Q183633: XADM: High CPU in Store.exe w/ Incorrectly Formatted Attachment"
permalink: /kb/183/Q183633/
---

## Q183633: XADM: High CPU in Store.exe w/ Incorrectly Formatted Attachment

{% raw %}

	Article: Q183633
	Product(s): Microsoft Exchange
	Version(s): 5.0,5.5
	Operating System(s): 
	Keyword(s): kbExchange500preSP3fix
	Last Modified: 21-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you monitor the activity of Store.exe using various tools, including
	Performance Monitor, Store.exe runs near or at 100 percent CPU usage.
	
	CAUSE
	=====
	
	The messaging client is improperly formatting a message containing a MIME
	attachment. This can occur for messages containing attachments that contain a
	left parenthesis "(" within the file name but without the right or closing
	parenthesis ")". This is interpreted as a comment rather then the file name, and
	the store continuously searches for the closing parenthesis.
	
	For example:
	
	  --PART.BOUNDARY.mailhub.4aba.34918213.0001
	  Content-Type: application/octet-stream
	  Content-Transfer-Encoding: base64
	  Content-Disposition: attachment; filename=(JPEG-IM.BMP <-HERE *****
	  Content-Description: (JPEG-IM.BMP
	  FTBP-Modification-Date: 12 Dec 2017 10:02:00 Z
	  FTBP-Object-Size: 167710
	
	It is possible to check the files in the IMCDATA\IN or IMCDATA\OUT subdirectories
	for the presence of messages that contain attachments with a ( in the file name.
	These files are text files. There is no need to check the archive directories
	underneath IN or OUT.
	
	
	RESOLUTION
	==========
	
	Exchange Server 5.0
	-------------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Exchange Server version 5.0
	service pack that contains this fix.
	
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
	
	Component: Information Store
	
	+--------------------------+
	| File name  | Version     | 
	+--------------------------+
	| Mdbmsg.dll | 5.0.1461.91 | 
	+--------------------------+
	| Store.exe  | 5.0.1461.91 | 
	+--------------------------+
	
	
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Microsoft Exchange
	Server version 5.5. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Information Store
	
	+------------------------+
	| File name | Version    | 
	+------------------------+
	| Store.exe | 5.5.2144.0 | 
	+------------------------+
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	versions 5.0 and 5.5. This problem was first corrected in Microsoft Exchange
	Server version 5.5 Service Pack 1.
	
	Additional query words: spin hog
	
	======================================================================
	Keywords          : kbExchange500preSP3fix 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : :5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
