---
layout: page
title: "Q130865: How to Place Totals on Report's Last Page in Page Footer"
permalink: /kb/130/Q130865/
---

## Q130865: How to Place Totals on Report's Last Page in Page Footer

{% raw %}

	Article: Q130865
	Product(s): Microsoft FoxPro
	Version(s): 2.50x 2.60 2.60a 3.00 | 2.50x 2.
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When using the Report Writer, you can use the Summary band to place information
	at the end of the report on the bottom of the last page where the page footer is
	located.
	
	By design, the Summary band places information at the end of a report, but the
	information is positioned right after the last record printed. However, you may
	want to place the information at the bottom of the page where the page footer is
	located. This article describes how to accomplish this.
	
	MORE INFORMATION
	================
	
	Do not use the Summary band. Instead, place the expressions that hold the
	summary information on the page footer with a conditional IIF statement in the
	expression that checks for the last record of the table. Below are the steps
	needed to place the summary information in the page footer section.
	
	Before creating or running the report, ensure that the rectotal variable used in
	the conditional IIF below is already set to the total number of records that
	need to be printed. To do this, type the following command in the Command window
	to get the total number of records in a table:
	
	     rectotal=RECCOUNT()
	
	If the report is going to use a FOR clause, use the same FOR condition in the
	COUNT command to store the number of records to be printed in the rectotal
	variable. For example, use this command:
	
	     COUNT FOR fieldname="whatever" TO rectotal
	
	Step-by-Step Example
	--------------------
	
	Method 1 for FoxPro for Windows versions 2.x
	--------------------------------------------
	
	1. Open the report.
	
	2. Make a field expression by choosing the AB tool that enables you to make a
	  report expression.
	
	3. In the report expression box, type:
	
	        IIF(rectotal=counter, "Yes we are at the end!","")
	
	4. Select Variables from the Report menu.
	
	5. In the variable text box, type this variable name:
	
	        counter
	
	6. In the Value to Store text box, type this number:
	
	        1
	
	7. Select the Sum option in the Calculate text box.
	
	8. Make sure that the Reset selection is at "End of Report."
	
	9. From the Report menu, select Page Review.
	
	You will see the phrase "Yes we are at the end!" located in the page footer of
	the last page only. This simulates a Summary band that puts information at the
	bottom of the last page of a report.
	
	NOTE: If you are using Visual FoxPro and the Print Area is set to "Whole Page" in
	the Page Setup dialog box, the information in the page footer may not appear.
	Sliding the Page Footer bar down one or more lines in the Report Designer makes
	the Page Footer information appear.
	
	Method 2 for FoxPro for Windows version 3.x
	-------------------------------------------
	
	1. Open the report.
	
	2. Create a field expression by selecting the AB tool from the Report Controls
	  toolbar that allows you to create a report expression.
	
	3. In the report expression box, type the following:
	
	        "Yes we are at the end of this Visual FoxPro 3.0 report!"
	
	4. Select the Print When command button.
	
	5. In the Print Only When Expression Is True text box, type:
	
	        recno()=reccount()
	
	  NOTE: This expression does not work in FoxPro 2.x.
	
	6. From the Report Menu, select Page Review and you now see the phrase "Yes we
	  are at the end of this Visual FoxPro 3.0 report!" located in the page footer
	  of the last page only.
	
	  NOTE: This simulates a Summary band that puts information at the bottom of the
	  last page of a report.
	
	To print a calculation you may substitute a calculation expression for the text
	expression.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300
	Version           : 2.50x 2.60 2.60a 3.00 | 2.50x 2.
	
	=============================================================================
	

{% endraw %}
