---
layout: page
title: "Q244519: XADM: How to Restore Multiple X.400 Addresses"
permalink: /kb/244/Q244519/
---

## Q244519: XADM: How to Restore Multiple X.400 Addresses

{% raw %}

	Article: Q244519
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 07-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you troubleshoot a problem in a mailbox, distribution list, or custom
	recipient, the X.400 address for an object may be missing. You can re-create the
	X.400 address manually. If many objects are missing the X.400 address, you may
	need to perform a directory import of the mailboxes to re-create the X.400
	addresses.
	
	NOTE: In Exchange Server versions 5.0 and 5.5 you cannot remove the X.400 address
	type from multiple recipients by clicking to clear the address type in the Site
	Addressing property page. You can only remove the X.400 address type from
	individual recipients.
	
	MORE INFORMATION
	================
	
	If the X.400 addresses are removed from recipients, you can re-create them by
	performing a simple export and import of the directory.
	
	NOTE: The new X.400 addresses are built on the current information in the
	directory. This process does not rebuild custom X.400 addresses.
	
	To re-create the X.400 addresses:
	
	1. In the Exchange Server Administrator program, on the Tools menu, click
	  Directory Export.
	
	2. Click Export File, and then in the File Name box, type a name for the .csv
	  file that you want to create (for example, Export.csv). If you are prompted
	  to create the file, click Yes.
	
	3. Click Container, and then click the container that holds the recipients that
	  have missing X.400 addresses. If appropriate, click Include Subcontainers.
	
	4. Under Export Objects, be sure that Mailboxes, Distribution Lists, and Custom
	  Recipients are selected.
	
	5. Click Export. When the export process is finished, click OK.
	
	6. In the Exchange Server Administrator program, on the Tools menu, click
	  Directory Import.
	
	7. Click Import File, and then click the .csv file that you created in step 2.
	
	8. Click Import.
	
	The import process re-creates the X.400 address for each recipient that doesn't
	have one. The import process doesn't change any other attributes, unless the
	Export.csv file was edited in the time between the export process and import
	process.
	
	Additional query words: deleted e-mail addresses tab X400
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
