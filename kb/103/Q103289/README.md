---
layout: page
title: "Q103289: Mac Gty: Using Auto-Propagation Versus Gateway Installer"
permalink: /kb/103/Q103289/
---

## Q103289: Mac Gty: Using Auto-Propagation Versus Gateway Installer

{% raw %}

	Article: Q103289
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.0,3.1,3.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 3.0, 3.1, 3.1a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you install access gateways on version 3.0 or later of Microsoft Mail for
	AppleTalk Networks, there are some differences between using the Gateway
	Installer and using Microsoft Mail's built-in auto-propagation feature. Some of
	these important differences are described below.
	
	Access Gateways Installed via Auto-propagation
	----------------------------------------------
	
	1. For a master gateway to support auto-propagation, the gateway developer must
	  set the FLGS resource in the gateway install file. This tells the Mail server
	  that the gateway understands how to use the Special icon for addressing
	  information and enables the "All in-site servers can access" check box at
	  gateway installation time.
	
	2. You can tell if an access gateway is installed by clicking the Special icon
	  in the Address Mail window and looking for the name of the gateway.
	  Auto-propagated access gateways are NOT displayed in the Gateway Installer.
	
	3. Custom addressing forms and custom message forms cannot propagate to access
	  servers from the master gateway. The only information that will propagate
	  from the gateway server to the access server is the gateway name, the
	  two-character ID, and the serial number of the gateway server. Additionally,
	  any gateway recipients will propagate to the access server.
	
	4. When the master gateway is removed, a MasterGone message is sent to all
	  servers in the same site. This will cause each server to remove all of its
	  resources related to the gateway.
	
	Access Gateways Installed via Gateway Installer
	-----------------------------------------------
	
	NOTE: Auto-propagation does not work across sites so you must extract and install
	access gateways with the Gateway Installer on servers in different sites than
	the master gateway.
	
	1. For gateways that require custom address forms (for example, some X.400
	  gateways), you must extract and install access gateways with the Gateway
	  Installer.
	
	2. These access gateways do show up in the Gateway Installer.
	
	3. When an access gateway is installed on a Mail server, an ENSLAVE request is
	  sent to the master gateway telling it to send gateway recipients.
	
	  When an access gateway is removed, a DESLAVE request is sent to the master
	  gateway telling the master gateway to stop sending gateway recipients.
	
	MORE INFORMATION
	================
	
	Once the relationship between the master gateway and the access gateway is
	established, the master gateway does not remember how an access gateway became
	an access gateway. It does not remember whether the access gateways were
	installed via auto-propagation or by using the Gateway Installer. This can cause
	an problem in the following scenario:
	
	1. Install a master gateway that supports auto-propagation, but also has a
	  custom form.
	
	2. Use the Gateway Installer to extract and install an access gateway on a Mail
	  server in a different site.
	
	3. Rebuild the data file of the access gateway in the different site.
	
	4. After the rebuilt Mail server and the master gateway have seen each other,
	  the master gateway will auto-propagate access gateway information, without
	  the custom form, to the server in the different site. However, the access
	  gateway will not function at full capacity because the custom form is
	  missing.
	
	NOTE: The problem in step 4 occurs because the master gateway auto-propagates
	access gateway information to the server in the DIFFERENT site.
	
	If you try to repeat step 2 above, the Gateway Installer will fail with an error
	stating that there is already a gateway with that ID installed. Version 3.1 of
	the Gateway Installer will allow you to repeat step 2, thus allowing you to
	install an access gateway that contains the custom form.
	
	Additional query words: 3.00 3.10 3.10a grey gray dim
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN310 kbMailATN310a
	Version           : WINDOWS:3.0,3.1,3.1a
	
	=============================================================================
	

{% endraw %}
