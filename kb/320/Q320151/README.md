---
layout: page
title: "Q320151: HOW TO: Determine Dependencies with InstallShield Express"
permalink: /kb/320/Q320151/
---

## Q320151: HOW TO: Determine Dependencies with InstallShield Express

{% raw %}

	Article: Q320151
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbfile kbSample kbsetup kbAppSetup kbGrpDSFox kbDSupport kbCodeSnippet kbHOWTOmaster
	Last Modified: 25-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Sample Program to Use with Dependency Walker
	- Check Your Application for Dependencies
	- Include Dependencies in InstallShield
	
	- REFERENCES
	
	SUMMARY
	=======
	
	InstallShield Express - Visual FoxPro Limited Edition is included with Visual
	FoxPro 7.0. With this version you cannot determine the dependencies of a Visual
	FoxPro 7.0 application. This article discusses how to use the Dependency Walker
	tool to determine the dependencies for a sample Visual FoxPro application, and
	how to incorporate them into an InstallShield project. For more information
	about how to install Dependency Walker, see the "References" section of this
	article.
	
	Sample Program to Use with Dependency Walker
	--------------------------------------------
	
	1. Paste the following code in a program (.prg) file, and then run the program
	  from the Command window::
	
	  LOCAL cMain
	
	  SET SAFETY OFF
	
	  cMain = "WAIT WINDOW 'Press Any Key To Exit'"
	
	   * Save the string cMain to Main.Prg.
	  STRTOFILE(cMain, "Main.Prg")
	
	  CREATE PROJECT DependSample NOWAIT
	  _VFP.ActiveProject.Files.Add("Main.Prg")
	
	  * Compile the project into an executable.
	  _VFP.ActiveProject.Build("DependSample.Exe",3,.T., .T.)
	
	2. This creates DependSample.exe, which is used later in this article.
	
	Check Your Application for Dependencies
	---------------------------------------
	
	1. Start Dependency Walker. For additional information about how to use this
	  program, see Help in Dependency Walker.
	
	2. On the File menu, click Open, or press CTRL+0.
	
	3. Find DependSample.exe that you created in the "Sample Program to Use with
	  Dependency Walker" section, and then click Open.
	
	4. On the Profile menu, click Start Profiling. The Profile Module dialog box
	  appears. Accept the default options, and then click OK. When the Wait Window
	  appears, press any key to quit the application and return to Dependency
	  Walker.
	
	The Module Dependency Tree View contains a list of files that the sample
	application depends on. Some of the files listed here are system files and
	should not be distributed with your application. The following are examples of
	system files:
	
	   - Kernel32.dll
	   - User32.dll
	   - Advapi32.dll
	
	5. All of the files may not be listed as parent items in the tree. Expand the
	  dependencies that are not system files to make sure that you include any
	  files that have dependencies to the main files.
	
	6. In this example you see Msvcr70.dll. Because Msvcr70.dll is not a system
	  file, include it. If you expand Msvcr70.dll, you see Kernel32.dll.
	  Kernel32.dll is a system file, therefore, it does not have to be included.
	  Also note that Vfp7r.dll is in the list. This is one of the FoxPro runtime
	  DLLs. If you expand Vfp7r.dll, you see several files that are system files.
	  Vfp7renu.dll is not a system file.
	
	7. One method that may help to determine which files are system files and which
	  files are not, is to right-click the file in question and then click
	  Properties. The Properties dialog box appears. Click the Version tab, and
	  then view the Product Name. The files that are system files may say Microsoft
	  Windows Operating System, or something similar.
	
	This application has dependencies on the following three files:
	
	   - Msvcr70.dll
	   - Vfp7r.dll
	   - Vfp7renu.dll
	
	Include Dependencies in InstallShield
	-------------------------------------
	
	This section discusses how to include those files that were determined to have
	dependencies in an InstallShield setup.
	
	1. Start InstallShield Express and create a new project, or open an existing
	  project.
	
	2. There are two ways that files can be included in InstallShield: Under Specify
	  Application Data, click either Files or click Objects/Merge Modules.
	
	  NOTE: In this example, use Objects/Merge Modules because there are merge
	  modules for both the Msvcr70.dll and the Visual FoxPro Runtime DLLs.
	
	3. Click Objects/Merge Modules, and then click Microsoft Visual C++ 7 Runtime
	  Library (MSVCR70.msm), and Microsoft Visual FoxPro 7 Runtime Libraries
	  (Vfp7Runtime.msm) from the Objects/Merge Modules list.
	
	4. If you do not have a merge module for files that have to be included, you can
	  add them. To do this follow these steps:
	
	  a. Under Specify Application Data, click Files.
	
	  b. In the Source computer's folders pane and the Source computer's files
	     pane, locate the files that you have to include.
	
	  c. Drag the files to the folder in Destination Computer in the Destination
	     computer's folders pane where you want the files installed.
	
	5. If you install files that have to be registered, you can have InstallShield
	  register these files for you. To do this follow these steps:
	
	  a. In Destination Computer in the Destination computer's folders pane, find
	     the file that has to be registered.
	
	  b. Right-click the file in the Destination computer's files pane, and then
	     click Properties.
	
	  c. Click the Advanced tab, and then in the Registration Type list, click
	     Self-registration. Click OK.
	
	This registers the file for you when it is installed. Note that some files do not
	have to be or cannot be registered, and the Self-registration selection will not
	be available.
	
	6. Build and distribute your setup as you normally would.
	
	REFERENCES
	==========
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  DownloadDownload Dependsia64version2.1.3623.exe now
	  (http://download.microsoft.com/download/visualfoxpro7/Utility/2.1/W9X2KMeXP/EN-US/Dependsia64version2.1.3623.exe)
	
	  DownloadDownload Dependsx86version2.1.3623.exe now
	  (http://download.microsoft.com/download/visualfoxpro7/Utility/2.1.3623/W9X2KMeXP/EN-US/Dependsx86version2.1.3623.exe)
	
	Release Date: June 25, 2002
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	Additional query words: depends.exe
	
	======================================================================
	Keywords          : kbfile kbSample kbsetup kbAppSetup kbGrpDSFox kbDSupport kbCodeSnippet kbHOWTOmaster 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP700
	Version           : :7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
