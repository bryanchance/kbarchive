---
layout: page
title: "Q274806: Browser Loops When User Password Expires"
permalink: /kb/274/Q274806/
---

## Q274806: Browser Loops When User Password Expires

{% raw %}

	Article: Q274806
	Product(s): Internet Information Server
	Version(s): 2.0,5.0
	Operating System(s): 
	Keyword(s): kbenv kbtool kbOSWin2000
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Proxy Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a user's password expires, and the user tries to access a Uniform Resource
	Locator (URL) through a secured server that is running Microsoft Proxy Server
	(MPS) 2.0, the browser goes into a loop instead of redirecting the user to the
	IISADMPWD virtual folder to allow them to change their user password.
	
	CAUSE
	=====
	
	This behavior occurs if you are running MPS 2.0 under Internet Information
	Services (IIS) 5.0, and if you are using proxy authentication to validate user
	access. There is a functionality change in IIS 5.0 in how IIS handles password
	expiration notification: an HTTP 302 redirect message is sent back to the
	client.
	
	
	The redirect path that is sent back to the client is the one that is specified in
	the metabase. By default, this is specified as a relative path. For example, the
	path that is sent back to the client when you are using secure password changes
	is /IISADMPWD/Aexp.htr; therefore, the client tries to reconnect by appending
	the redirect path to the originally requested URL. Because the server will then
	check the logon credentials (which have expired) another HTTP 302 redirect call
	is made, and this continues to occur, which causes the browser request to enter
	into a loop.
	
	RESOLUTION
	==========
	
	To resolve this behavior, change the relative path that is specified in the
	metabase to an absolute path. Use the Mdutil.exe utility that is included with
	the Windows NT 4.0 Service Pack 6a (SP6a) source files, to set the appropriate
	value in the metabase.
	
	NOTE: Do not use the version that is included in the Windows NT Option Pack 4.0.
	Also, this utility is not included in Windows 2000.
	
	Change the appropriate metabase value based on whether you have set up the
	computer to allow secured password changes or unsecured password changes. If you
	are using secured password change pages, run the following command:
	
	  mdutil.exe SET w3svc/AuthExpiredUrl
	  "http://<servername>/iisadmpwd/aexp.htr"
	
	If you are using unsecured password change pages, run the following command
	
	  mdutil.exe SET w3svc/AuthExpiredUnsecureUrl
	  "http://<servername>/iisadmpwd/aexp3.htr"
	
	where <servername> is the computer name of your proxy server or a Fully
	Qualified Domain Name (FQDN) of the proxy server.
	
	NOTE: The quotation marks in these commands are not optional; they are used to
	set a string value in the metabase.
	
	After you have set the appropriate value, restart the IIS services by running the
	Iisreset.exe command-line utility on the server.
	
	Additional query words: iis 5 proxy iisadmpwd loop
	
	======================================================================
	Keywords          : kbenv kbtool kbOSWin2000 
	Technology        : kbiisSearch kbAudDeveloper kbiis500 kbProxyServSearch kbProxyServ200
	Version           : :2.0,5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
