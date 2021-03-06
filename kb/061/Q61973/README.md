---
layout: page
title: "Q61973: Internal Compiler Error: gencode.c, Line 437"
permalink: /kb/061/Q61973/
---

## Q61973: Internal Compiler Error: gencode.c, Line 437

{% raw %}

	Article: Q61973
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 | mspl13_c
	Last Modified: 29-MAY-1990
	
	The sample code shown below generates the following internal compiler
	error when compiled with the /qc compiler option, in all memory
	models:
	
	   foo.c(10) : fatal error C1001: Internal Compiler Error
	               (compiler file 'gencode.c', line 437)
	               Contact Microsoft Product Support Services
	
	Sample Code
	-----------
	
	#include <stdio.h>
	#include <stddef.h>
	
	void main (void)
	{
	   char   *p1, *p2;
	   double temp;
	
	   p1 = p2 = NULL;
	
	   temp = 1 + (double)(p2-p1);  // This line causes the error
	}
	
	The following is a suggested workaround:
	
	Simplify the expression by assigning (p2-p1) to a temporary variable.
	For example:
	
	   ptrdiff_t c;
	
	   c = p2-p1;
	   temp = 1 + (double)c;
	
	Note: The error message shown above also occurs when casting "a" to a
	float.

{% endraw %}
