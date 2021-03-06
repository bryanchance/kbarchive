---
layout: page
title: "Q151675: FIX: Re-throwing Exception Causes Abnormal Program Termination"
permalink: /kb/151/Q151675/
---

## Q151675: FIX: Re-throwing Exception Causes Abnormal Program Termination

{% raw %}

	Article: Q151675
	Product(s): Microsoft C Compiler
	Version(s): 4.00 4.10 4.20
	Operating System(s): 
	Keyword(s): kbCompiler kbVC500fix
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	- Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When creating a temporary object and then re-throwing an exception, as
	demonstrated in the sample code in the More Information section of this article,
	the application terminates abnormally.
	
	
	RESOLUTION
	==========
	
	See the More Information section for the sample code and the workaround.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual C++ version 5.0.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	     /* Compile options needed: /GX /O2
	     */ 
	     class aClass
	     {
	     public:
	        aClass(const char*){} ;
	        ~aClass(){} ;
	     } ;
	
	     void push(const aClass& val)
	     {
	     }
	
	     void main()
	     {
	
	        int a = 5 ;
	        try
	        {
	           try
	           {
	              throw a ;
	           }
	           catch(int)
	           {
	              //Workaround: uncomment the following 2 lines
	              //aClass aObj("ABC") ;
	              //push(aObj) ;
	              //Comment the line below
	              push("ABC") ;
	              throw ;
	           }
	           catch(...)
	           {
	           }
	        }
	        catch(...)
	        {
	        }
	     }
	
	Additional query words: kbVC400bug
	
	======================================================================
	Keywords          : kbCompiler kbVC500fix 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC410 kbVC420 kbVC32bitSearch
	Version           : 4.00 4.10 4.20
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
