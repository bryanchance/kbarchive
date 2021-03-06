---
layout: page
title: "Q237284: WD97: Error Message: &quot;Cannot Find Installable ISAM&quot;"
permalink: /kb/237/Q237284/
---

## Q237284: WD97: Error Message: &quot;Cannot Find Installable ISAM&quot;

{% raw %}

	Article: Q237284
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word8 word97
	Last Modified: 21-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Word 97 for Windows, if you perform a mail merge with a data source
	saved as a dBase (*.dbf) file, and you select a dBase format converter [for
	example: FoxPro Files via ODBC (*.dbf)], and you have one or more of the
	following installed:
	
	- Windows NT 4.0 with Microsoft Data Access Components (MDAC) version 2.1
	
	  -or-
	
	- Windows 98 Second Edition
	
	  -or-
	
	- Windows 95 or Windows 98 with MDAC 2.1
	
	  -or-
	
	- Any other program that updates the Odbcjt32.dll file to version 4.0
	
	The following error message may appear:
	
	  Cannot Find Installable ISAM
	
	CAUSE
	=====
	
	The operating systems listed in the "Symptoms" section of this article all
	install Odbcjt32.dll version 4.0, which does not support installable ISAM
	(indexed sequential access method).
	
	WORKAROUND
	==========
	
	NOTE: This workaround details specifically using the FoxPro ODBC converters.
	However, these steps should correct the problems described in the "Symptoms"
	section of this article regardless of the source of the dBase (*.dbf) file you
	are using.
	
	
	To work around this problem, you need to do all of the following:
	
	1. To ensure that you are using Visual FoxPro ODBC driver (Vfpodbc.dll) version
	  6.0 or later, download and install Microsoft Data Access Components (MDAC)
	  version 2.1 or later.
	
	  NOTE: If you already have installed MDAC 2.1 or later, proceed to the next two
	  steps, "Download and install Wdvfpdsn.exe" and "Attach or re-attach the
	  FoxPro data source in Word".
	
	  -and-
	
	2. Download and install the Wdvfpdsn.exe file from the Microsoft Download
	  Center.
	
	  -and-
	
	3. Attach or re-attach the FoxPro data source in Word.
	
	Ensure That You Are Using Vfpodbc.dll Version 6.0 or Later
	----------------------------------------------------------
	
	Download and install MDAC 2.1 from the following Web site:
	
	  http://www.microsoft.com/Data/MDAC21info/MDAC21sp2manifest.htm
	  (http://www.microsoft.com/Data/MDAC21info/MDAC21sp2manifest.htm)
	
	Or click here:
	
	  http://www.microsoft.com/data/download.htm
	  (http://www.microsoft.com/data/download.htm)
	
	When MDAC 2.1 is installed, it does not create the necessary registry entries for
	Word to use it. To correctly allow Word to use the Visual FoxPro ODBC driver
	during a mail merge, follow the steps in the next section, "Downloading and
	Installing the Wdvfpdsn.exe File."
	
	Download and Install the Wdvfpdsn.exe File
	------------------------------------------
	
	The following file is available for download from the Microsoft Download Center:
	
	  Wdvfpdsn.exe
	  (http://download.microsoft.com/download/word97win/driver/1/WIN98/EN-US/Wdvfpdsn.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	Attach or Re-attach the Data Source
	-----------------------------------
	
	1. In Microsoft Word, open the mail merge main document, and attach or re-attach
	  the data source by clicking Mail Merge on the Tools menu and then clicking
	  Get Data.
	
	2. After you select the Microsoft FoxPro files in the Open Data Source dialog
	  box, make sure to select the Select method check box. Click Open.
	
	3. In the Confirm Data Source dialog box, select "FoxPro Files - Word via ODBC
	  (*.dbf)".
	
	NOTE: You still receive the error message if you click on the old driver, "FoxPro
	Files via ODBC (*.dbf)". To avoid this, make sure you click the correct driver
	with "Word" in the name; for example, FoxPro Files - Word via ODBC (*.dbf).
	
	MORE INFORMATION
	================
	
	ISAM is an indexing mechanism for efficient access to rows of data in a file.
	
	REFERENCES
	==========
	
	For additional information about problems relating to the Visual FoxPro ODBC
	driver, click the article numbers below to view the articles in the Microsoft
	Knowledge Base:
	
	  Q191708 BUG: Visual FoxPro ODBC Driver May Crash Client Application
	
	  Q191685 Vfp6int.exe VFP 6.0 ODBC Driver FoxPro.int Resource File
	
	
	Additional query words: fox pro
	
	======================================================================
	Keywords          : kbdta word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
