---
layout: page
title: "Q88884: Leaving Routine in ON ERROR in FoxBASE+ or FoxPro"
permalink: /kb/088/Q88884/
---

## Q88884: Leaving Routine in ON ERROR in FoxBASE+ or FoxPro

{% raw %}

	Article: Q88884
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:1.0,1.01,1.02,1.21,2.0,2.1,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxBASE+ for MS-DOS, versions 1.21, 2.1 
	- Microsoft FoxPro for MS-DOS, versions 1.0, 1.01, 1.02, 2.0, 2.5, 2.5a 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can use the following methods to leave the routine specified in an ON ERROR
	command:
	
	- Use the RETURN TO MASTER command to return to the highest level program. For
	  example, if the Run menu pad is present on the FoxPro system menu bar
	  (FOXSTART.APP was executed on startup), the RETURN TO MASTER command returns
	  control to FOXSTART.APP.
	
	- Use the RETURN command to return to the program that had the error and
	  continue execution on the next line. For example, the RETURN command
	  terminates execution of a program or a user-defined function (UDF) and
	  returns control to either the calling program, the highest level calling
	  program, another program, or the Command window.
	
	  Using a RETURN command at the end of a program or a user-defined function is
	  optional because an implicit RETURN command automatically follows the last
	  statement in a program file. Private memory variables are released when the
	  RETURN command is executed.
	
	- Use the RETRY command to return to the program that had the error and execute
	  the line that had the error. For example, the RETRY command returns control
	  to the calling program and reexecutes the last line that was executed in that
	  program. The RETRY command is similar to the RETURN command except that the
	  RETURN command causes the next line in the calling program to be executed
	  rather than reexecuting the most recently executed line. RETRY is especially
	  useful in error-handling routines or when a set of commands should be
	  repeated until a certain condition is true.
	
	  In FoxPro/LAN (the networked version of FoxPro), the RETRY command is
	  frequently used to repeat a command until a record or file becomes available
	  for use. The SET REPROCESS command can be used to control the number of times
	  a command is repeated when it is unable to access a record or a file. In most
	  network situations, the SET REPROCESS command is preferred.
	
	MORE INFORMATION
	================
	
	The ON ERROR command traps errors that occur during program execution. When an
	error occurs, the trap is triggered and the specified command is executed. An ON
	ERROR routine may be deactivated by issuing another ON ERROR command that does
	not specify a command to run.
	
	If the command specified in the ON ERROR command is DO <program>,
	specifying the ERROR(), LINENO(), MESSAGE(), and PROGRAM() functions as
	parameters passes the cause of the error, the line number where the error
	occurred, the error message, and the name of the program that had the error to
	the error handling function. This information can be valuable during the process
	of debugging an application.
	
	After the ON ERROR routine completes, program execution resumes on the line
	immediately following the line that causes the error. However, if the specified
	command is DO <program> and the <program> ends with a RETRY command,
	execution resumes on the line on which the error occurred.
	
	In FoxPro/LAN, an ON ERROR routine may be used to trap for errors created when a
	command that attempts to lock a record or a file is unsuccessful. If an ON ERROR
	routine is not in effect, FoxPro displays an error message that indicates why
	the record lock or file lock is unsuccessful (for example, "Record is in use by
	another"). If an ON ERROR routine is in effect, FoxPro does not display an error
	message and it executes the ON ERROR routine. Note that an unsuccessful lock
	attempt by the explicit locking functions [FLOCK(), LOCK(), and RLOCK()] does
	not trigger an ON ERROR routine or cause an error message to be displayed.
	Instead, these functions return a logical truth value (.F. or .T.) to indicate
	the failure or success of the lock attempt.
	
	Sample Code
	-----------
	
	     ON ERROR DO errhand WITH ;
	        ERROR(), MESSAGE(), MESSAGE(1), PROGRAM(), LINENO()
	
	     *** The next line should cause an error. ***
	
	     USE nodatabase
	
	     PROCEDURE errhand
	     PARAMETER merror, mess, mess1, mprog, mlineno
	     ? 'Error number: ' + LTRIM(STR(merror))
	     ? 'Error message: ' + mess
	     ? 'Line of code with error: ' + mess1
	     ? 'Line number of error: ' + LTRIM(STR(mlineno))
	     ? 'Program with error: ' + mprog
	
	Additional query words: VFoxWin FoxDos FoxWin 1.00 | fox base plus 1.x 2.x
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250 kbFoxPro250a kbFoxBASE210DOS kbFoxBASE121DOS kbFoxBASESearch kbVFP300
	Version           : MS-DOS:1.0,1.01,1.02,1.21,2.0,2.1,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	
	=============================================================================
	

{% endraw %}
