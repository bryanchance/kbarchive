---
layout: page
title: "Q253118: SMS: The &quot;Gold Key&quot; Button May Not Respond"
permalink: /kb/253/Q253118/
---

## Q253118: SMS: The &quot;Gold Key&quot; Button May Not Respond

{% raw %}

	Article: Q253118
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbsetup kbClient kbMMC _IK964 kbsms200 kbCollections kbHelpDesk kbsmsAdmin kbUpgrade kb
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Gold Key button in the Remote Control Quick Viewer window may not respond.
	This button is used to send a CTRL+ALT+DEL key sequence to a Microsoft Windows
	NT-based client computer during a remote control session.
	
	You can use the Gold Key button to log on to a computer that you want to control
	remotely if no users are currently logged on to that client, or if the logon
	screen saver is running. During a remote control session to a Windows NT-based
	client, the Gold Key button may not respond, even though the mouse works for
	other desktop selections on the administrative console computer.
	
	CAUSE
	=====
	
	This behavior can occur if your computer contains an incorrect file version or
	if your computer has an unloaded driver.
	
	WORKAROUND
	==========
	
	To work around this behavior, verify the following items on a Windows NT-based
	client:
	
	1. Verify that the Remote Control components are installed and that the client
	  has restarted.
	
	2. From the client, click Devices in Control Panel. Verify that the Systems
	  Management Server (SMS) Remote Control Keyboard driver runs and is set to
	  automatically start. If not, start this driver and restart the client. If
	  third-party mouse drivers are running on the computer, unload them.
	
	3. On the client, examine the date and version of both the Kbstuff.sys and
	  Rchelp.sys files.
	
	4. The Kbstuff.sys file is located in the <Windir>\System32\Drivers
	  folder. Make sure that this file is version 2.00.1239.0000 or later, with a
	  last-modified time and date stamp of 12-18-1998.
	
	  If this computer has been a client of an SMS version 1.2 site, an earlier
	  version of the Kbstuff.sys file (version 3.51, dated 6-27-1996) may be
	  located in the <Windir>\System32\Drivers folder. An earlier version of
	  the Kbstuff.sys file can disable the functions of a mouse, even if the Gold
	  Key button works.
	
	  The Rchelp.sys file is located in the <Windir>\System32\Drivers folder.
	  Make sure that this file is version 4.0 or later, with a time and date stamp
	  of 6-25-1999. The earlier version of the Rchelp.sys file is 2.0, dated
	  10-6-1997.
	
	  If there are out-of-date files, replace them with files from a computer that
	  has a functioning Gold Key button, and then restart the computer.
	
	5. Verify the existence of the following registry keys and the registry value of
	  the Image Path (the correct value is System32\Drivers):
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Kbdclass
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Kbstuff
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Rchelp
	
	6. If you have the Kbstuff.sys file (dated: 4-15-2000, from SMS version 2
	  Service Pack 2 [SP2]) and your computer is running Windows NT 4.0 Service
	  Pack 4 (SP4), you must replace it with the Kbstuff.sys file (dated: 6-25-1999
	  from SMS version 2 Service Pack 1 [SP1]).
	
	Additional query words: prodsms remctrl kbstuff.sys rchelp.sys
	
	======================================================================
	Keywords          : kbsetup kbClient kbMMC _IK964 kbsms200 kbCollections kbHelpDesk kbsmsAdmin kbUpgrade kbRemoteProg 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
