---
layout: page
title: "Q126272: How to Delete Records Having Identical ID Nums from Two Tables"
permalink: /kb/126/Q126272/
---

## Q126272: How to Delete Records Having Identical ID Nums from Two Tables

{% raw %}

	Article: Q126272
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 12-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to delete records that share the same
	identification number and exist in two separate tables.
	
	You can use this method to delete duplicates that exist in two separate but
	similarly defined tables. Or you can use it, for example, to delete a customer
	from your system when that customer has records in a master table and
	transaction tables. For example, you might want to create a temporary table
	filled with customer numbers to be deleted. Then use one of the methods in this
	article to mark the duplicates for deletion from the master and transaction
	tables.
	
	MORE INFORMATION
	================
	
	The following two methods mark duplicate records in CUSTOMER.DBF for deletion,
	so make sure you have a backup copy of CUSTOMER.DBF.
	
	- SCAN...ENDSCAN loop method.
	
	- SET RELATION command method.
	
	To demonstrate these techniques, you need to create a table containing duplicate
	records. Issue the following commands to create a practice table and index file
	from the CUSTOMER.DBF table:
	
	     IF _MAC=.T.
	        SET DEFAULT TO "Hard drive:FoxPro 2.6:Tutorial:"
	     ELSE
	        SET DEFAULT TO Sys(2004)+"Tutorial"
	        && SET DEFAULT TO SYS(2004)+"Samples\Data" in Visual FoxPro
	     ENDIF
	     USE CUSTOMER.DBF
	     COPY TO TEST.DBF FOR RECNO() < 10
	     USE TEST
	     INDEX ON cno TAG cno ADDITIVE
	     && INDEX on cust_id TAG custid ADDITIVE in Visual FoxPro
	
	The TEST.DBF table now contains records from the CUSTOMER.DBF table. These
	records serve as the duplicate records for the examples listed below. A .CDX
	index also exists for the TEST.DBF.
	
	Method One: SCAN...ENDSCAN Loop Routine to Find Duplicate Records
	-----------------------------------------------------------------
	
	The following program searches the TEST.DBF file and marks the duplicate records
	in CUSTOMER.DBF for deletion:
	
	     USE Customer IN 0
	     USE Test IN 0 ORDER TAG CNO
	     SELECT Customer
	     SCAN
	     m.cno=cno
	     && m.custid=cust_id in Visual FoxPro
	     SELECT Test
	     SEEK(m.cno)
	     && SEEK (m.custid) in Visual FoxPro
	     IF FOUND()= .T.
	        SELECT Customer
	        DELETE
	     ENDIF
	     SELECT Customer
	     ENDSCAN
	
	Method Two: SET RELATION and FOUND() Function Method
	----------------------------------------------------
	
	This method sets up a one-to-one relationship between the two tables. After
	establishing the relationship, the DELETE command moves through the Customer
	table comparing records with those in the Test table. If the FOUND() function
	returns the logical value true, DELETE marks the matching record in
	CUSTOMER.DBF. After executing this code, the first nine records are deleted in
	the Customer table.
	
	     USE Customer.dbf in 0
	     USE Test.dbf IN 0 ORDER TAG cno
	     SELECT Customer
	     SET RELATION TO cno INTO Test ADDITIVE
	     DELETE ALL FOR FOUND('Test')
	
	Additional query words: VFoxWin FoxWin FoxDos FoxMac
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300
	Version           : MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a,3.0
	
	=============================================================================
	

{% endraw %}
