---
layout: page
title: "Q39019: Error U2157 Filename : Cannot Access File"
permalink: /kb/039/Q39019/
---

## Q39019: Error U2157 Filename : Cannot Access File

	Article: Q39019
	Product(s): See article
	Version(s): 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | s_pascal h_fortran h_masm s_quickc s_util s_error | mspl13_c
	Last Modified: 21-DEC-1988
	
	The following error is from "LIB Error Messages" in the manual
	"CodeView and Utilities", Section C.3, Page 374, and in the "Microsoft
	QuickC Compiler Programmer's Guide," Section D.5, Page 380:
	
	U2157       filename : cannot access file
	
	            LIB was unable to open the specified file.
	
	Error messages generated by the Microsoft Library Manager, LIB, have
	one of the following formats:
	
	{filename | LIB} : fatal error U1xxx: messagetext
	{filename | LIB} : error U2xxx: messagetext
	{filename | LIB} : warning U4xxx: messagetext
	
	The message begins with the input-file name (filename), if one exists,
	or with the name of the utility. If possible, LIB prints a warning and
	continues operation. In some cases errors are fatal and LIB terminates
	processing.
	
	A hyphen (dash, - ) in a subdirectory name in the path can cause this
	error; this error occurs because of a problem in LIB.