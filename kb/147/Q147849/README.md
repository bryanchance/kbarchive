---
layout: page
title: "Q147849: MSB: &quot;Internal Error&quot; or Computer Hangs When Starting"
permalink: /kb/147/Q147849/
---

## Q147849: MSB: &quot;Internal Error&quot; or Computer Hangs When Starting

{% raw %}

	Article: Q147849
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0,95
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbtshoot kbtlc
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores Inside the Earth for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores in the Age of Dinosaurs for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Rainforest for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Solar System for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run Magic School Bus title listed above on a computer using Windows
	95/98, you may receive one or more of the following error messages:
	
	  Internal Error 300. Use Video for Windows version 1.1 or greater, not
	
	  -or-
	
	  Internal Error 416. Use Video for Windows 1.1 or greater, not
	
	Additionally, the computer may stop responding (hang) before the opening screen
	is displayed.
	
	
	CAUSE
	=====
	
	This behavior can occur if Video for Windows is not installed correctly.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, make sure the Motion Video Device (Media Control)
	setting is enabled.
	
	If the problem persists, reinstall the Motion Video Device (Media Control) and
	Video codecs that are included with Windows.
	
	Turning On Motion Video Device
	------------------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia.
	
	3. Click the Advanced or Devices tab.
	
	4. Double-click Media Control Devices.
	
	5. Click Motion Video Device (Media Control), and then click Properties.
	
	  NOTE: If the Windows 3.x Motion Video Device is installed, it is named MCI
	  Driver For AVI.
	
	6. Make sure the Use This Media Control Device option is selected.
	
	7. Click OK. Restart Windows if you are prompted to do so.
	
	8. Start the Magic School Bus title.
	
	If, after following these steps, the problem continues, reinstall the Motion
	Video Device and the Video codecs.
	
	Reinstalling Motion Video Device
	--------------------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add New Hardware.
	
	3. Click Next, click No, and then click Next.
	
	  NOTE: If you are using Windows 98, click Next, click Next, click No, and then
	  click Next.
	
	4. In the Hardware Types box, click Sound, Video And Game Controllers, and then
	  click Next.
	
	5. In the Manufacturers box, click Microsoft MCI. In the Models box, click
	  Motion Video Device (Media Control). Click Next.
	
	6. Click Finish. Restart Windows if you are prompted.
	
	For more information about MCI Devices, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q142731 How to Install and Remove Codecs and MCI Devices in Windows 95
	
	
	Reinstall Video Codecs
	----------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. Click the Windows Setup tab.
	
	4. In the Components list box, click Multimedia.
	
	5. Click Details.
	
	6. If the Video Compression option is selected, it may not be installed
	  properly, and should be removed. To remove Video Compression, do the
	  following:
	
	  a. Click the Video Compression check box to clear it, and then click OK.
	
	  b. Click OK again.
	
	  c. Repeat steps 1-5 to return to the Video Compression check box in
	     Add/Remove Programs.
	
	7. Click the Video Compression check box to select it.
	
	8. Click OK, and then click OK again.
	
	9. Follow the instructions on the screen.
	
	For more information on Video codecs, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q142946 Troubleshooting Video Codecs in Windows 95
	
	
	MORE INFORMATION
	================
	
	If, after following the above steps, you are still unable to run the Magic
	School Bus title, try the following procedure:
	
	NOTE: The following steps involve creating, editing, renaming, and deleting files
	and folders. For more information about how to accomplish these tasks in
	Windows, see your Windows printed documentation or online Help.
	
	1. Double-click My Computer.
	
	2. On the View menu, click Options or Folder Options.
	
	3. Click the View tab.
	
	4. Make sure that the Show All Files option is selected, and the Hide MS-DOS
	  File Extensions For File Types That Are Registered box is not selected.
	
	5. Click OK.
	
	6. In the Windows\System folder on your hard drive, rename the following files
	  (if they exist):
	
	  indeov.drv
	  Ir21_r.dll
	  Ir32.dll
	  Mciavi.drv
	  Msvidc.drv
	  Msrle.drv
	
	7. Reinstall the Motion Video Device and the Video codecs. To do this, please
	  follow the steps in the "RESOLUTION" section of this article.
	
	8. Delete the appropriate Magic School Bus title's folder, and then reinstall
	  the Magic School Bus program.
	
	For additional troubleshooting information, please see the following articles in
	the Microsoft Knowledge Base:
	
	  Q142179 Troubleshooting .avi File Playback Problems in Windows 95
	
	  Q139806 Err Msg: MMSYSTEM266 The Device Could Not Be Loaded...
	
	
	Additional query words: 1.00 msbsea ocean oceans frizz kbmm multimedia multi-media multi media error vfw video hand black errmsg hangs freezes earth kbfaq dinosaurs msbdinos winmsbdinos
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbtshoot kbtlc 
	Technology        : kbOSWin98 kbOSWin95 kbOSWinSearch kbHomeProdSearch _IKkbbogus kbZNotKeyword kbKidsSearch kbScholasticHuman kbScholasticOcean kbScholasticSolar kbScholasticDinosaurs kbScholasticEarth kbScholasticRainForest kbMSBSearch
	Version           : WINDOWS:1.0,95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
