---
layout: page
title: "Q42925: Activating Hercules Card on a Dual-Monitor System"
permalink: /kb/042/Q42925/
---

## Q42925: Activating Hercules Card on a Dual-Monitor System

{% raw %}

	Article: Q42925
	Product(s): See article
	Version(s): 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist5.10 S_QUICKC | mspl13_c
	Last Modified: 17-MAY-1989
	
	Part 3 of the Microsoft C Optimizing Compiler Version 5.10 README.DOC
	states the following:
	
	  If you have both a Hercules monochrome card and a color video
	  card, you should invoke MSHERC.COM with the /H (/HALF) option.
	  The /H option causes the driver to use one instead of two
	  graphics pages. This prevents the two video cards from
	  attempting to use the same memory. You do not have to use the
	  /H option if you have only a Hercules card.
	
	The /H option fails to work correctly on a system with two video
	cards, where one of the cards is a compatible Hercules card.
	
	This is not a problem with MSHERC.COM. The source of the problem lies
	in the graphics library provided with Microsoft C Optimizing Compiler
	Version 5.10 and QuickC Version 1.01.
	
	This problem has been corrected in QuickC Version 2.00. The QuickC
	Version 2.00 include files, libraries, and linker are fully compatible
	with C 5.10. Upgrades are available for the C Optimizing Compiler and
	prior versions of QuickC. Information on upgrades is available from
	Customer Service.
	
	You also must use the DOS MODE command to activate the monochrome card
	prior to sending output to the Hercules display adapter.
	
	Microsoft is researching this problem and will post new information as
	it becomes available.

{% endraw %}
