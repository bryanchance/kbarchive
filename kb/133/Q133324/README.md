---
layout: page
title: "Q133324: PRB: Potential Limit of 64 Different .OCX Files per Process"
permalink: /kb/133/Q133324/
---

## Q133324: PRB: Potential Limit of 64 Different .OCX Files per Process

{% raw %}

	Article: Q133324
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbole kbActiveX kbCOMt kbCtrlCreate kbMFC kbVC100 kbGrpDSMFCATL
	Last Modified: 02-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft OLE Control Developer's Kit (CDK) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Attempting to create or insert an OLE control may generate the following
	assertion message:
	
	  Assertion Failed: <application>: File ctlmodul.cpp, Line 192
	
	CAUSE
	=====
	
	The assertion is the function _AfxGetCtlModuleStatics and is the following:
	
	     ASSERT(_afxCtlTlsIndex != NULL_TLS);
	
	The assertion fails because the process creating the OLE control has used up all
	of its available thread-local storage (TLS) slots.
	
	RESOLUTION
	==========
	
	To avoid the problem, do one of the following:
	
	- Package more than one OLE control per .OCX file. A TLS slot is allocated when
	  a process first attaches to an .OCX file. Implementing more than one OLE
	  control per .OCX file will use only one TLS slot per .OCX file while still
	  allowing the process to use each of the OLE controls associated with the .OCX
	  file.
	
	-or-
	
	- Design the containing application in such a way that it does not need to be
	  able to create so many OLE controls simultaneously.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The 32-bit MFC implementation of OLE controls uses TLS to store control module
	state information. One TLS slot is allocated every time a process attaches to a
	new OLE control (.OCX) file. One process may allocate up to
	TLS_MINIMUM_AVAILABLE TLS slots. TLS_MINIMUM_AVAILABLE is guaranteed to be at
	least 64 slots on all systems.
	
	NOTE: TLS_MINIMUM_AVAILABLE is a Win32 limitation rather than an MFC limitation.
	
	This problem will occur when a process tries to access more than
	TLS_MINIMUM_AVAILABLE TLS slots, whether they are used for control module state
	information or for some other purpose. TLS_MINIMUM_AVAILABLE is the maximum
	number of different .OCX files (packages that contain OLE controls) that may be
	loaded before the assertion occurs. Depending on how your container uses thread
	local storage, you may encounter the assertion after loading a fewer number of
	.OCX files.
	
	NOTE: This does not restrict the number of OLE Controls that can be placed in a
	container simultaneously. As long as your process uses no more than
	TLS_MINIMUM_AVAILABLE TLS slots, the number of controls that can be created is
	constrained only by available memory.
	
	TLS allocation and usage was changed with MFC version 4.0 and the limit on the
	number of simultaneous OLE controls has effectively been removed.
	
	REFERENCES
	==========
	
	Richter, Jeffrey, Advanced Windows NT: The Developer's Guide to the Win32
	Application Programming Interface, Chapter 8, "Thread-Local Storage."
	
	Additional query words: 2.0 2.00 2.1 2.10 2.2 2.20
	
	======================================================================
	Keywords          : kbole kbActiveX kbCOMt kbCtrlCreate kbMFC kbVC100 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
