---
layout: page
title: "Q242349: 'Error 5: Access Denied' When Connecting Using PPTP"
permalink: /kb/242/Q242349/
---

## Q242349: 'Error 5: Access Denied' When Connecting Using PPTP

{% raw %}

	Article: Q242349
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP5
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to make a PPTP connection from a client computer running
	Windows NT 4.0 Service Pack 5 to a server running Windows NT 4.0 Service Pack 5
	that is running Routing and Remote Access Service (RRAS), the initial
	authentication attempt may not work and you may receive the following error
	message:
	
	  Error 5: Access Denied
	
	This problem can also occur if (RRAS) is configured to forward MSCHAP v2
	authentication requests to a Non-Microsoft Remote Authentication Dial-In User
	Service (RADIUS) server.
	
	CAUSE
	=====
	
	This problem occurs because there is a problem with negotiating MS Chap V2 with
	NON Microsoft Radius servers. We have enabled a registry setting to negotiate MS
	chap V1.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date      Time                 Size    File name     Platform
	  -------------------------------------------------------------
	  09/22/99  03:02p               60,688  RASPPPEN.dll   (x86)
	  09/22/99  03:01p               99,088  RASPPPEN.dll   (alpha)
	
	
	
	WORKAROUND
	==========
	
	None
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To disable the forwarding of MS Chap V2 requests for RRAS Server, change the
	following registry key to use the following value:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\rasman\ppp
	
	Value Name: DisableMSChapV2
	Data Type: REG_DWORD
	Value: 0 or 1 where 1 disables the option.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q240870 'Access Denied' When an SP5 RRAS Client Access an SP5 RRAS Server
	  with OfferMSCHAP
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400sp5 kbWinNTS400search kbWinNTS400
	Version           : :4.0,4.0 SP5
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
