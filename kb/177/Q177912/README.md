---
layout: page
title: "Q177912: FIX: Access Violation When Calling COleVariant::Clear()"
permalink: /kb/177/Q177912/
---

## Q177912: FIX: Access Violation When Calling COleVariant::Clear()

{% raw %}

	Article: Q177912
	Product(s): Microsoft C Compiler
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbole kbATM kbDatabase kbMFC kbVC kbVC500bug kbVC600fix kbGrpDSVCDB kbGrpDSMDAC kbGrpDS
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When calling COleVariant::Clear(), an access violation occurs when the variant
	type is VT_DECIMAL.
	
	CAUSE
	=====
	
	There is special code in COleVariant::Clear() that checks the type of the
	variant and calls SysFreeString() if it is equal to VT_BSTRT (14). Here is the
	code:
	
	     #ifndef _UNICODE
	        if (vt == VT_BSTRT)
	               ::SysFreeString(bstrVal);
	        else
	     #endif
	        {
	               VERIFY(::VariantClear(this) == NOERROR);
	        }
	
	VT_BSTRT is used to identify ANSI BSTRs and is a special type that MFC uses
	internally. The problem is that OLE also defines VT_DECIMAL to be 14.
	
	Thus, if you call Clear() on a COleVariant, which has a variant type of
	VT_DECIMAL, an access violation will occur because the function calls
	SysFreeString() on a non-existent string.
	
	RESOLUTION
	==========
	
	Don't call COleVariant::Clear(); instead, call VariantClear() and pass in the
	COleVariant.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ version 6.0
	for Windows.
	
	MORE INFORMATION
	================
	
	The GetRows() ADO sample, which is provided with the OLE DB 1.1 SDK, contains
	code that can cause the access violation when calling Clear().
	
	Here is the DoGetRows() function from GETRDLG.CPP:
	
	     HRESULT CGetRowsDlg::DoGetRows()
	     {
	        HRESULT         hr;
	        COleVariant      vBookmark, rgvFields;
	        COleVariant      cRows;
	        COleVariant      varField, varNewField;
	        CString         strLBRow;
	        LONG         lNumOfCol, lNumRecords;
	        LONG         lIndex[2];
	        CListBox      *pListBox =
	                                 (CListBox *)GetDlgItem(IDD_GETROWSLIST);
	
	        //Perform GetRows on Employee table.
	
	        //Start from the current place
	        vBookmark.vt = VT_ERROR;
	        vBookmark.scode = DISP_E_PARAMNOTFOUND;
	
	        //Get all columns.
	        rgvFields.vt = VT_ERROR;
	        rgvFields.scode = DISP_E_PARAMNOTFOUND;
	
	     if (!m_piEmpRecordSet)
	        return E_NOINTERFACE;
	
	        hr = m_piEmpRecordSet->GetRows(   adGetRowsRest,
	                                             vBookmark,
	                                             rgvFields,
	                                             &cRows
	                                           );
	        if (FAILED(hr)) goto ErrorExit;
	
	        //Find out how many records were actually retrieved,
	        //(SafeArrays are 1-based)
	        lNumOfCol = 2;
	        SafeArrayGetUBound(cRows.parray, 2, &lNumRecords);
	
	        //Clear the listbox
	        pListBox->ResetContent();
	
	        for (lIndex[1] = 0; lIndex[1] <= lNumRecords; lIndex[1]++)
	        {
	               strLBRow.Empty();//Clear the string
	               for (lIndex[0] = 0; lIndex[0] <= lNumOfCol; lIndex[0]++)
	               {
	                 SafeArrayGetElement(cRows.parray, &lIndex[0], &varField);
	                 hr = VariantChangeType(&varNewField, &varField, 0, VT_BSTR);
	
	                 if(hr == S_OK)
	                 {
	                   strLBRow += (LPCWSTR)varNewField.bstrVal;
	                   strLBRow += _T(", ");
	                 }
	                 varField.Clear();
	                 varNewField.Clear();
	               }
	               pListBox->AddString(strLBRow);
	             }
	
	        return hr;
	
	     ErrorExit:
	        TCHAR szBuf[256];
	        wsprintf(szBuf, _T("Error: %d \n"), hr);
	        AfxMessageBox(szBuf);
	
	        return hr;
	     }
	
	NOTE: If the column type returned from the ADO source is VT_DECIMAL, the
	varField.Clear() function will crash because COleVariant::Clear() calls
	SysFreeString() on data that is not a string.
	
	To reproduce the error, add the following lines of code to the function
	CGetRowsDlg::DoGetRows():
	
	     COleVariant var10;
	
	     hr = VariantChangeType(&var10, &varField, 0, VT_DECIMAL);
	     if(hr!=S_OK)
	          AfxMessageBox("Can't VariantChangeType to decimal");
	     else
	         var10.Clear();
	
	Add the code just before the line:
	
	      varField.Clear();
	
	Additional query words: bug AV GPF
	
	======================================================================
	Keywords          : kbole kbATM kbDatabase kbMFC kbVC kbVC500bug kbVC600fix kbGrpDSVCDB kbGrpDSMDAC kbGrpDSOLEDB kbNoUpdate kbMDACNoSweep 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC32bitSearch kbVC500Search
	Version           : :5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
