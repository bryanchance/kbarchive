---
layout: page
title: "Q167734: FILE: MFC Browser Library (MFC.BSC) in VC 5.0 Is Incomplete"
permalink: /kb/167/Q167734/
---

## Q167734: FILE: MFC Browser Library (MFC.BSC) in VC 5.0 Is Incomplete

{% raw %}

	Article: Q167734
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbfile kbMFC kbVC500 kbVC500bug kbVC600fix kbGrpDSMFCATL
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The MFC browser library (MFC.BSC) that ships with Visual C++ is incomplete. The
	browser cannot find some symbols in MFC (for example, References to
	CDC::m_hDC).
	
	There are two self-extracting files included in this article. They both contain
	Mfc.bsc files.
	
	Mfcbsc1.exe contains Mfc.bsc file created with Devstudio installed under the root
	directory of a drive. If you have installed Devstudio under the root directory
	of a drive, then download this file.
	
	Mfcbsc2.exe contains Mfc.bsc file created with Devstudio installed under Program
	Files directory. If you chose the default directory while installing Devstudio,
	then download this file.
	
	If you have installed Devstudio in a path that does not match any of the above
	two, then download any one of the files and put it in the
	<Drive>:\<Devstudio directory path>\vc\mfc\src directory. When you
	open the browse file and search for a symbol, the browser will not be able to
	find the sources. However, it will prompt you for the path and from then on it
	should be able to find the sources. This happens every time you open the browse
	file.
	
	Copy the .exe to the <drive>:<Devstudio directory path>\vc\mfc\src
	and execute it. It should extract mfc.bsc file in that directory.
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  MFCbsc1.exe
	  (http://download.microsoft.com/download/vc50pro/file1/2/WIN98/EN-US/MFCbsc1.exe)
	
	  MFCbsc2.exe
	  (http://download.microsoft.com/download/VC50pro/file2/2/Win98/EN-US/MFCbsc2.exe)
	
	Release Date: June 30, 2000
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ version 6.0.
	
	MORE INFORMATION
	================
	
	Alternatively, you can rebuild the MFC browser library (MFC.BSC) on your
	machine. First you must have the MFC source files installed.
	
	Follow this procedure:
	
	1. Verify that you have around 400 megabytes of free disk space on the drive
	  where Visual C++ is installed. This much space is required to build the
	  browse information. 358 megabytes is used by the .SBR files. The .SBR files
	  can be freed once the browser database has been built. Temp files require the
	  additional space. Temp files are automatically deleted.
	
	2. From a Command Prompt, run the Vcvars32.Bat which should be in the
	  <drive>:<DevStudio directory path>\vc\bin to set the proper
	  environment variables. Change to the <drive>:<Devstudio directory
	  path>\Vc\Mfc\Src directory, and build the browse information by running
	  the nmake on the makefile as follows:
	
	  nmake browseonly=1 no_pch=1 no_pdb=1 dll=2
	
	  This creates NafxeWD.bsc file and a subdirectory called $DLLD.W with .SBR
	  files.
	
	3. Provided you do not plan to rebuild the browse database frequently, remove
	  all files in the $DLLD.W directory, and then remove the directory itself. The
	  intermediate .SBR files occupy roughly 358 megabytes of disk space and are
	  not required to use the browser.
	
	4. You can rename the new browse file to Mfc.bsc from NafxeWD.bsc.
	
	To use the browser file, start Visual C++, and click Open on the File menu.
	Choose the .BSC file that you just created. Click Tools, and then click Source
	Browser. The Browser window appears and you can look up any of the MFC functions
	or data variables.
	
	REFERENCES
	==========
	
	For more information about how to build the MFC.BSC library, please see the
	following articles in the Microsoft Knowledge Base:
	
	  Q98656 Creating a Browser Library for the Foundation Classes Additional
	
	  Q138326 HOWTO: Create a Browser Library for the Common Control Classes
	
	Additional query words: mfc browser mfc.bsc
	
	======================================================================
	Keywords          : kbfile kbMFC kbVC500 kbVC500bug kbVC600fix kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC32bitSearch kbVC500Search
	Version           : winnt:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
