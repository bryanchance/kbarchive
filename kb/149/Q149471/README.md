---
layout: page
title: "Q149471: PRB: Conflicting Definitions of time_t Between Windows and Mac"
permalink: /kb/149/Q149471/
---

## Q149471: PRB: Conflicting Definitions of time_t Between Windows and Mac

{% raw %}

	Article: Q149471
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbinterop kbCRT kbVC
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), included with:
	   - Microsoft Visual C++, Macintosh Cross-Development Addon, versions 2.0, 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Mixing calls to both the Visual C++ C Runtime Library and native Macintosh
	functions that rely on time_t may yield incorrect results. Most of these
	functions can be found in Time.h.
	
	CAUSE
	=====
	
	Both sets of libraries define time_t as the number of seconds elapsed since
	epoch. However, Visual C++ defines epoch as 00:00:00 January 1, 1970 (GMT) and
	stores the value as a signed 32-bit long. Native Macintosh functions define
	epoch as 00:00:00 January 1, 1904 (GMT) and stores the value as an unsigned
	32-bit long.
	
	RESOLUTION
	==========
	
	If the source to the call to a time function is accessible, then offset the
	value by 2,082,844,800 or by the value computed from the call to the Mac API
	LongDateToSeconds().
	
	     LongDateToSeconds(
	         LongDateRec   lDate  // Jan 1, 1970 00:00:00
	         LongDateTime* lSecs  // time_t equivalent returned
	     )
	
	If the calling module's source is inaccessible (as in many third-party
	libraries), create an ASLM (Apple Shared Library Manager) module containing the
	third-party library linked with Apple's native CRT, and export functions to call
	the third-party library routines. This will allow you to use both CRT time
	functions without conflicts.
	
	STATUS
	======
	
	time_t has been a standard for representing time among many platforms. However,
	the epoch that this is based on has not been standardized. Apple's standard is
	different from those of Microsoft and UNIX System V.
	
	REFERENCES
	==========
	
	Books Online
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbCRT kbVC 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
