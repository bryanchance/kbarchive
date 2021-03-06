---
layout: page
title: "Q150476: MSB Ocean: Hangs at the Beach After Playing About 30 Times"
permalink: /kb/150/Q150476/
---

## Q150476: MSB Ocean: Hangs at the Beach After Playing About 30 Times

{% raw %}

	Article: Q150476
	Product(s): Microsoft Home Kids Products
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbimukbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you run Magic School Bus Explores the Ocean (MSB Ocean) version 1.0
	successfully approximately 30 times, it may hang at the beach just after Ms.
	Frizzle says, "Let's hit the beach!" or just prior to this on the sand dunes.
	
	CAUSE
	=====
	
	This problem is related to the way MSB Ocean caches information in the Bd01.fcs
	file. This file can become damaged over time.
	
	RESOLUTION
	==========
	
	To resolve this problem, install the updated version of MSB Ocean version 1.01.
	This file is available from Microsoft at (425) 635-7140. When you receive MSB
	Ocean version 1.01, use the following steps to install the program:
	
	Windows 95/98
	-------------
	
	1. Insert the MSB Ocean compact disc into your CD-ROM drive.
	
	  NOTE: Hold down the SHIFT key when you insert the compact disc to prevent
	  Setup from starting automatically.
	
	2. Click Start, and then click Run.
	
	3. Type the following line, and then press ENTER:
	
	  <cd-rom drive>:\setup
	
	  where <cd-rom drive> is the letter of your CD-ROM drive.
	
	4. Click OK, and then follow the Setup instructions on the screen.
	
	Windows 3.1
	-----------
	
	1. Insert the MSB Ocean compact disc into your CD-ROM drive.
	
	2. In Program Manager, click Run on the File menu.
	
	3. Type:
	
	  d:\setup
	
	  Or, if your CD-ROM drive letter is not D, substitute the letter of your CD-ROM
	  drive.
	
	4. Click OK, and follow the directions.
	
	If you still encounter problems after installing the updated version 1.01 of MSB
	Ocean, you may need to delete the existing MSB Ocean files prior to installing
	the update. (Please note that deleting the installation also deletes all your
	saved divers licenses and fish cards.)
	
	To remove your existing version of MSB Ocean:
	
	Windows 95/98
	-------------
	
	1. Click Start, point to Programs, and then click Windows Explorer.
	
	2. Open the Mskids folder on the hard disk (usually drive C).
	
	3. Right-click the Msbocean folder, and then click Delete.
	
	4. Close Windows Explorer.
	
	To reinstall MSB Ocean, follow the Windows 95/98 installation instructions
	earlier in this article.
	
	Windows 3.1
	-----------
	
	1. In Program Manager, go to the Main group, and then run File Manager.
	
	2. Locate the Mskids folder on your hard drive (usually on drive C) and then
	  locate the Msbocean folder.
	
	3. Select the Msbocean folder.
	
	4. On the File menu, click Delete. Click OK in the Delete dialog box.
	
	5. Click Yes To All in the Confirm File Delete dialog box.
	
	6. Close File Manager.
	
	To reinstall MSB Ocean, follow the Windows 3.1 installation instructions earlier
	in this article.
	
	MORE INFORMATION
	================
	
	To obtain MSB Ocean version 1.01, contact Microsoft Technical Support at (425)
	635-7140.
	
	For information about how to determine which version of MSB Ocean you currently
	have installed on your computer, please see the following article(s) in the
	Microsoft Knowledge Base:
	
	  Q151465 MSB Ocean: How to Determine Which Version You Have
	
	
	WORKAROUND
	----------
	
	Use the following steps to resolve this problem until you receive the updated
	version of MSB Ocean:
	
	1. Locate the Bd01.fcs file in the Mskids\Msbocean\System\Fc folder.
	
	2. Delete Bd01.fcs.
	
	3. Run MSB Ocean.
	
	If the problem persists, use these steps:
	
	1. Delete the entire Mskids\Msbocean folder.
	
	2. Run Scandisk and note any errors. (See your Windows printed documentation or
	  online Help for information about using Scandisk.)
	
	3. Reinstall MSB Ocean, then run the program.
	
	Additional query words: 1.00 kids mskids schoolbus msb frizz msbocean ocean
	
	======================================================================
	Keywords          : kbimu kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kbScholasticOcean kbMSBSearch
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
