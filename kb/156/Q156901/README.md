---
layout: page
title: "Q156901: INFO: STL Sample for the inplace_merge Function"
permalink: /kb/156/Q156901/
---

## Q156901: INFO: STL Sample for the inplace_merge Function

{% raw %}

	Article: Q156901
	Product(s): Microsoft C Compiler
	Version(s): 4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbVC420 kbVC500 kbVC600 kbDSupport
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ NET (2002) supported both the managed code model that is provided by the .NET Framework and the unmanaged native Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	The sample code below illustrates how to use the inplace_merge and the begin and
	end STL functions in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     <algorithm>
	
	Prototype
	---------
	
	     template<class BidirectionalIterator> inline
	
	         void inplace_merge(BidirectionalIterator first,
	                            BidirectionalIterator middle,
	                            BidirectionalIterator last)
	
	NOTE: The class/parameter names in the prototype do not match the original
	version in the header file. They have been modified to improve readability.
	
	Description
	-----------
	
	The inplace_merge algorithm merges two sorted sub-sequences: [first..middle) and
	[middle..last) in place into a single sorted sequence [first..last). This
	version assumes that the ranges [first..middle) and [middle..last) are sorted
	using operator<. If both ranges contain equal values, the value from the
	first range will be stored first.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: /GX
	  // 
	  // inplace_merge.cpp : Illustrates how to use the inplace_merge
	  //                     function.
	  // 
	  // Functions:
	  // 
	  //   inplace_merge : Merge two sorted sub-sequences in place into a
	  //                   single sorted list.
	  // 
	  //   begin - Returns an iterator that points to the first element in a
	  //           sequence.
	  // 
	  //   end - Returns an iterator that points one past the end of a sequence.
	  // 
	  // Written by Kalindi Sanghrajka
	  // of Microsoft Product Support Services,
	  // Software Core Developer Support.
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  // disable warning C4786: symbol greater than 255 character,
	  // okay to ignore
	
	  #pragma warning(disable: 4786)
	
	  #include <iostream>
	  #include <algorithm>
	  #include <functional>
	  #include <vector>
	
	  #if _MSC_VER > 1020   // if VC++ version is > 4.2
	     using namespace std;  // std c++ libs implemented in std
	     #endif
	
	  void main()
	
	  {
	
	      const int VECTOR_SIZE = 8 ;
	
	      // Define a template class vector of int
	      typedef vector<int, allocator<int> > IntVector ;
	
	      //Define an iterator for template class vector of strings
	      typedef IntVector::iterator IntVectorIt ;
	
	      IntVector Numbers(VECTOR_SIZE) ;
	
	      IntVectorIt start, end, it ;
	
	      // Initialize vector Numbers
	      Numbers[0] = 4 ;
	      Numbers[1] = 10;
	      Numbers[2] = 70 ;
	      Numbers[3] = 10 ;
	      Numbers[4] = 30 ;
	      Numbers[5] = 69 ;
	      Numbers[6] = 96 ;
	      Numbers[7] = 100;
	
	      start = Numbers.begin() ;   // location of first
	                                  // element of Numbers
	
	      end = Numbers.end() ;       // one past the location
	                                  // last element of Numbers
	
	      cout << "Before calling inplace_merge\n" << endl ;
	
	      // print content of Numbers
	      cout << "Numbers { " ;
	      for(it = start; it != end; it++)
	          cout << *it << " " ;
	      cout << " }\n" << endl ;
	
	      //merge the elements of Numbers in place
	      inplace_merge(start, start + 3, end) ;
	
	      cout << "After calling inplace_merge\n" << endl ;
	
	      // print content of Numbers
	      cout << "Numbers { " ;
	      for(it = start; it != end; it++)
	          cout << *it << " " ;
	      cout << " }\n" << endl ;
	
	  }
	
	Program Output is: Before calling inplace_merge
	
	Numbers { 4 10 70 10 30 69 96 100  }
	
	After calling inplace_merge
	
	Numbers { 4 10 10 30 69 70 96 100  }
	
	REFERENCES
	==========
	
	Visual C++ Books On Line: Visual C++ Books:C/C++:Standard C++ Library Reference.
	
	Additional query words: STL inplace_merge begin end STLSample kbSTL kbTemplate
	
	======================================================================
	Keywords          : kbcode kbVC420 kbVC500 kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC500 kbVC600 kbVC32bitSearch kbVCNET kbVC500Search
	Version           : :4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
