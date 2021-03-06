---
layout: page
title: "Q191876: No Prompt to Disconnect When Using Internet Explorer with MSN"
permalink: /kb/191/Q191876/
---

## Q191876: No Prompt to Disconnect When Using Internet Explorer with MSN

{% raw %}

	Article: Q191876
	Product(s): The Microsoft Network
	Version(s): 2.51,2.6,5,5.0,5.01,5.1,5.2,5.3,5.5
	Operating System(s): 
	Keyword(s): kbenv dun msiew95 msnetwork win98 kbDialUp
	Last Modified: 13-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Explorer versions 5, 5.01, 5.5 for Windows 95 
	- Microsoft Internet Explorer versions 5, 5.01, 5.5 for Windows 98 
	- The Microsoft Network versions 2.51, 2.6, 5.0, 5.1, 5.2, 5.3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you quit all instances of Internet Explorer, you may not be prompted to
	disconnect from MSN, The Microsoft Network.
	
	CAUSE
	=====
	
	This behavior can occur if you connect to the Internet using Internet Explorer
	rather than by using the MSN or Quick Connect icon. When you connect with
	Internet Explorer, the Dial-Up Networking connection created by MSN Setup is
	used. This connection does not automatically prompt you to disconnect when you
	quit Internet Explorer.
	
	RESOLUTION
	==========
	
	To resolve this issue, create a new connection icon for MSN using the settings
	in your current MSN connection, and then configure Internet Explorer to use the
	new connection:
	
	1. Double-click My Computer, and then double-click Dial-Up Networking.
	
	2. Right-click the MSN icon, click Properties, and write down all the
	  information in the connection, and then click OK.
	
	3. Double-click Make New Connection, type a name for the new connection, and
	  then click Next.
	
	4. Enter the local access number that you copied from the MSN phone list, click
	  Next, and then click Finish.
	
	5. Right-click the new icon, click Properties, on the Server Types tab select
	  the same properties as the original dialer, and then click Ok to return to
	  Dial-up Networking.
	
	6. Click Start, click Settings, and then click Control Panel.
	
	7. Double-click the Internet icon or the Internet Options icon and then click
	  the Connections tab.
	
	8. In the Dial-up Settings window select the new connection, select Always Dial
	  My Default Connection, and then click Set Default.
	
	9. Click Settings, under Dial-up Settings type your username as MSN/username,
	  type your MSN password in the Password box, click OK, and then click OK
	  again.
	
	
	Additional query words: autodisconnect kbimu
	
	======================================================================
	Keywords          : kbenv dun msiew95 msnetwork win98 kbDialUp 
	Technology        : kbIEsearch kbMSNSearch kbIE95Search kbIE500Search kbZNotKeyword3 kbIE98Search kbIE500Win95 kbIE550Win95 kbIE500Win98 kbIE501Win98 kbIE550Win98 kbIE501Win95 kbMSN520 kbMSN530 kbMSN510 kbMSN500 kbMSN251 kbMSN260 kbIE550Search
	Version           : :2.51,2.6,5,5.0,5.01,5.1,5.2,5.3,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
