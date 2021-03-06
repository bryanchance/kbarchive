---
layout: page
title: "Q153199: HOWTO: Use BCP to Move Large Amounts of Data to SQL Server"
permalink: /kb/153/Q153199/
---

## Q153199: HOWTO: Use BCP to Move Large Amounts of Data to SQL Server

{% raw %}

	Article: Q153199
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.6a,3.0,3.0b,6.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbinterop kbODBC kbvfp300 kbvfp300b kbvfp600 kbvfp260
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 6.0 
	- Microsoft FoxPro for Windows, version 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to use the Bulk Copy Program (BCP), a stand- alone
	utility that ships with SQL Server. If you need to move large amounts of data
	from Visual FoxPro to SQL Server, the Upsizing Wizard may be too slow. The Bulk
	Copy Program utility only transfers the data, it does not create the tables. You
	can use the Upsizing Wizard to create the tables or create them yourself in
	ISQL/W. In order to prepare SQL Server to accept the data using the "fast"
	version of BCP, you must execute the sp_dboption system procedure and set the
	select into/bulkcopy option to true.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	Following are sample steps using the BCP utility to transfer data from an ASCII
	file to SQL Server:
	
	1. Execute from SQL Server:
	
	  " sp_dboption Mydatabase,bulkcopy,true " (without the quotation marks)
	
	2. Create a tab-delimited ASCII file from the Visual FoxPro Table. For example,
	  use a low-level routine to output your fields into a text file:
	
	        =FPUTS(fhandle, emp_id + CHR(9) + ;
	               last_name + CHR(9) + ;
	               first_name + CHR(9) + ;
	               title + CHR(9) + ;
	               PADR(DTOC(birth_date)+' '+'12:00AM',16,' ') + CHR(9) + ;
	               PADR(DTOC(hire_date)+' '+ '12:00AM',16,' ') + CHR(9) + ;
	               address + CHR(9) + ;
	               city + CHR(9) + ;
	               region + CHR(9) + ;
	               postalcode + CHR(9) + ;
	               STR(salary,12,2)  )
	
	3. Create a bcp Format file necessary to transfer data. For example, from the
	  bin directory under SQL Server:
	
	  bcp mydatabase.dbo.employee out c:\temp\emp.txt /Sservename /Usa /Ppassword
	
	  NOTE: This command should be on one line.
	
	4. Follow the prompts, and type "\t" (without the quotation marks) for the field
	  terminator for each field.
	
	5. When prompted, save the format file with a meaningful name such as
	  employee.fmt.
	
	6. Edit the format file with an MS-DOS editor.
	
	7. Change the second column for each row to SYBCHAR as in the following example
	  using employee.fmt:
	
	     6.0
	     11
	     1       SYBCHAR       0       6       "\t"       1       emp_id
	     2       SYBCHAR       0       20      "\t"       2       last_name
	     3       SYBCHAR       0       10      "\t"       3       first_name
	     4       SYBCHAR       0       30      "\t"       4       title
	     5       SYBCHAR       0       16      "\t"       5       birth_date
	     6       SYBCHAR       0       16      "\t"       6       hire_date
	     7       SYBCHAR       0       60      "\t"       7       address
	     8       SYBCHAR       0       15      "\t"       8       city
	     9       SYBCHAR       0       15      "\t"       9       region
	     10      SYBCHAR       0       10      "\t"      10       postalcode
	     11      SYBCHAR       0       8       "\r\n"    11       salary
	
	8. Change the 5th column for the last row to "\r\n" as the end of file marker.
	
	9. Transfer the ASCII file into SQL Server using BCP as follows:
	
	  bcp mydatabase.dbo.employee in c:\temp\employ.txt /femployee.fmt
	  /Sservernamec /Usa /P""
	
	10. When completed, set the Bulkcopy option back to FALSE using Step 1 with the
	  FALSE parameter.
	
	
	REFERENCES
	==========
	
	For additional information, please see the SQL Server System Administrator's
	Guide.
	
	Additional query words: upsize upsized
	
	======================================================================
	Keywords          : kb3rdparty kbinterop kbODBC kbvfp300 kbvfp300b kbvfp600 kbvfp260 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro260a kbVFP300 kbVFP300b kbVFP600
	Version           : WINDOWS:2.6a,3.0,3.0b,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
