---
layout: page
title: "Q42074: ESC Key Aborts Only the Compile Process in QC Environment"
permalink: /kb/042/Q42074/
---

## Q42074: ESC Key Aborts Only the Compile Process in QC Environment

{% raw %}

	Article: Q42074
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 2-MAY-1989
	
	The inside cover of the "Microsoft QuickC Up and Running" manual
	states that the ESC key stops the compiler and linker from continuing.
	This is only partially correct. The ESC key only aborts the compile
	stage of the QuickC compiler. During the link stage, the ESC key is
	ignored.
	
	Pressing CTRL+C or CTRL+BREAK aborts the compile or link (or ilink)
	processes, though it may take repeated attempts. However, pressing
	CTRL+C or CTRL+BREAK during the compile process can result in an
	incomplete object file that will not link properly. Pressing CTRL+C or
	CTRL+BREAK during the link process may result in a bad executable
	file. Attempting to run the bad .EXE may hang your machine.

{% endraw %}
