---
layout: page
title: "Q43062: Incorrect Code Generated with Conditional Operator"
permalink: /kb/043/Q43062/
---

## Q43062: Incorrect Code Generated with Conditional Operator

{% raw %}

	Article: Q43062
	Product(s): See article
	Version(s): 5.00 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist5.10 | mspl13_c
	Last Modified: 16-JAN-1990
	
	Using the conditional with incremental operators on pointers can
	generate incorrect code. The following routine should reset ptr to the
	beginning of the list if the end of the list has been reached. If the
	end of the list has not been reached, ptr should be incremented. The
	code generated does not increment ptr as expected; ptr is actually
	reset to itself, i.e., ptr = ptr.
	
	Replacing the ternary operator (? :) with an if -- else construct
	corrects the problem.
	
	Microsoft is researching this problem and will post new information as
	it becomes available.
	The following routine illustrates this behavior:
	
	test()
	{
	        char *ptr,*str,*end;
	
	        ptr = ((ptr == end)? str: ptr++);
	
	}

{% endraw %}
