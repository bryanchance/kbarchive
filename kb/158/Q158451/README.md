---
layout: page
title: "Q158451: HOWTO: How To Call Automation Methods with Variable Argument Lis"
permalink: kb/158/Q158451/
---

## Q158451: HOWTO: How To Call Automation Methods with Variable Argument Lis

	Article: Q158451
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbole kbActiveX kbAutomation kbCOMt kbMFC kbVC400 kbVC420 kbGrpDSMFCATL
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	OLE Automation allows you to create methods on your server that can take a
	variable-length list of arguments. This is a simple procedure in Visual Basic.
	However, there are special considerations when you call such a method from a
	client written in C/C++.
	
	MORE INFORMATION
	================
	
	Visual Basic
	------------
	
	You can create a method on your OLE Automation server that takes a variable-
	length list of arguments, such as the following:
	
	     Function MyFunc1(ByVal p1 As Long, ParamArray p2()) As String
	
	     myfunc1 = "String returned"
	     End Function
	
	The ParamArray parameter p2 allows the caller of this function to pass any number
	of parameters in addition to the required parameter, p1. Visual Basic retrieves
	additional parameters by locating the array of VARIANTS contained in the
	variable p2. The type information generated by Visual Basic for the MyFunc1
	function will look like this:
	
	     [id(0x60030020), vararg]
	     HRESULT _stdcall MyFunc1(
	                     [in] long p1,
	                     [in, out] SAFEARRAY(VARIANT)* p2,
	                     [retval] BSTR* );
	
	The vararg attribute in the type information for the MyFunc1 function tells
	callers that it accepts a variable-length list of arguments for this function.
	The [in, out] SAFEARRAY(VARIANT)* p2 parameter tells callers that a SAFEARRAY
	pointer, representing an array of variants, must be passed to this function. The
	array of variants is the list of optional parameters that will be passed into
	this function.
	
	If your Automation client is a Visual Basic client, then the call is made by
	passing however many parameters the caller wishes to pass beyond the one
	required parameter. The following is an example of a call to MyFunc1 in Visual
	Basic:
	
	     MyObj.MyFunc1(x,y,z,"Some String",q);
	
	In this example, x is passed as the required parameter to MyFunc1. All other
	parameters are packaged into an array of variants internally by Visual Basic.
	This array is then passed to the automation method.
	
	C or C++
	--------
	
	If you are calling this method from a C or C++ client, more work is necessary to
	package the call. If you are calling this function from an MFC client
	application and you use ClassWizard to generate a wrapper class for the
	automation object that contains MyFunc1, ClassWizard will not generate a wrapper
	function for MyFunc1 or any function that takes a variable-length list of
	arguments. This behavior occurs because the MFC implementation of
	COleDispatchDriver, which is responsible for packaging and invoking automation
	calls, does not understand how to package the SAFEARRAY type. This is not a bug,
	but rather an MFC limitation. Therefore, if you use ClassWizard to generate a
	wrapper class for an automation object that contains a method with a
	variable-length list of parameters, you have to write the wrapper to invoke that
	function.
	
	The following Visual C++ function shows how to invoke the MyFunc1 automation
	method:
	
	     CString _Class1::InvokeMyFunc1(long p1,VARIANT *pVar,int cElems)
	     {
	         //pVar is an array of variants.
	         //cElems is the number of variants in pVar.
	         //p1 is a required long parameter.
	         HRESULT hr;
	
	         VARIANT returnval;
	         EXCEPINFO Excepinfo;
	         unsigned int uArgErr;
	         DISPPARAMS dp;
	
	         VariantInit(&returnval);
	
	         //Create the rgvarg member of the DISPPARAMS struct.
	         //Make it big enough to hold the number of VARIANTS in the
	         //pVar array + an extra variant to hold the required parameter.
	          dp.rgvarg = new VARIANTARG[cElems+1];
	
	         //Because the variable length parameter list is the last argument
	         //to the function, it gets copied to dp.rgvarg first.
	         memcpy(dp.rgvarg,pVar,sizeof(VARIANT)*cElems);
	
	         //Add the required parameter (p1) to the array.
	         dp.rgvarg[cElems].vt = VT_I4;
	         dp.rgvarg[cElems].lVal = p1;
	
	         //Set cArgs to the total number of arguments passed.
	         dp.cArgs = cElems+1;
	         dp.cNamedArgs = 0;
	
	         //Make the call.
	         hr = m_lpDispatch->Invoke(0x6003001C,
	                             IID_NULL,
	                             LOCALE_SYSTEM_DEFAULT,
	                             DISPATCH_METHOD,
	                             &dp,
	                             &returnval,
	                             &Excepinfo,&uArgErr);
	         //Delete the memory you allocated above for dp.rgvarg.
	          delete[] dp.rgvarg;
	
	         //Return the string as a Cstring.
	         CString strRet(returnval.bstrVal);
	         VariantClear(&returnval);
	         return strRet;
	     }
	
	Although the type information for the MyFunc1 function specifies that a
	SAFEARRAY* be passed in, a SAFEARRAY was not created and passed to the invoke
	call by the caller. The caller passes an array of variants along with the one
	required parameter and the total count of all arguments in the DISPARAMS
	structure. The implementation of Invoke in the server will create a SAFEARRAY,
	package the passed-in array of variants into the SAFEARRAY, and then pass the
	SAFEARRAY pointer to the server's method. Therefore, the responsibility for
	creating the SAFEARRAY to pass to MyFunc1 does not fall on the caller. The
	caller needs to package all of the extra parameters it wishes to pass in a flat
	array (contained in the DISPARAMS struct) and invoke the method.
	
	Additional query words: 4.00 4.10 4.20 kbdsi ParamArray
	
	======================================================================
	Keywords          : kbole kbActiveX kbAutomation kbCOMt kbMFC kbVC400 kbVC420 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.0,4.1,4.2
	Issue type        : kbhowto
	
	=============================================================================
	