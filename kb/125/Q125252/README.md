---
layout: page
title: "Q125252: PC Adm: Rebuilding the Postoffice Address List"
permalink: /kb/125/Q125252/
---

## Q125252: PC Adm: Rebuilding the Postoffice Address List

{% raw %}

	Article: Q125252
	Product(s): Microsoft Mail For PC Networks
	Version(s): 2.1,3.0,3.2,3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 2.1, 3.0, 3.2, 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to rebuild a Microsoft Mail Postoffice Address List
	(POL). This may be necessary when the Postoffice Address List is corrupt and
	cannot be repaired by other means.
	
	This article requires the Microsoft Mail Database Maintenance Utilities document,
	which contains utilities used to repair and maintain the database for Microsoft
	Mail for PC Networks. The procedures described in the document apply to versions
	2.1 and later of Microsoft Mail, except where noted.
	
	To obtain the document containing the Database Maintenance Utilites, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q99419 PC DB: Database Maintenance Utilities [Complete]
	
	To obtain this document directly, you can download it at the following location:
	
	  ftp://ftp.microsoft.com/bussys/mail/pcmail-public/WA0641/
	
	MORE INFORMATION
	================
	
	NOTE: The resetting of group files can be automated. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q129500 Automating the Resetting of Group Files using GIMPORT
	
	Following are the steps to rebuild the Post Office List. The steps assume that
	all of the programs are run from the same directory(except ACCTONME.EXE, which
	must be run from the root of the Post Office). Also, the steps assume that the
	M:\ drive is mapped to the affected Post Office.
	
	1. Backup your complete Mail postoffice. You do not need to backup the MMF
	  directory.
	
	  It is recommended that the following steps be done when there are no users
	  logged in or instances of the EXTERNAL.EXE program working against your
	  production postoffice, and no changes are made to the production postoffice
	  via the ADMIN.EXE program.
	
	  The following steps make use of two programs: GIMPORT.EXE and ACCTONME.EXE.
	  These programs are part of the Database Maintenance Utilities Application
	  Note. Please read the documentation for both of these utilities before
	  proceeding. The documentation is part of the Application Note. Also, if
	  GIMPORT.EXE is run from a directory, which contains GROUPS.TXT or
	  GRPUSERS.DAT, remove those files.
	
	2. GIMPORT ADMIN -Ppassword -Ddrive -FGROUPS.TXT -I -X -Q -LGIMPORT.LOG
	
	  This extracts group information to two files (Groups.txt and Grpusers.dat) to
	  the current directory.
	
	  NOTE: Verify that there is valid information in these files before proceeding.
	  If not, or if Admin.nme is empty, restore from backup first, repeat step 2,
	  and then finish the process if information appears in the text files that
	  were created. If group information never appears, you have to read the groups
	  manually.
	
	3. GIMPORT ADMIN -Ppassword -Ddrive -R
	
	  This will reset the ADMIN.GRP and ADMINSHD.GRP to 8 bytes and GROUP.GLB and
	  GRPMEM.GLB to 4 byte files.
	
	4. REN M:\NME\ADMIN.NME M:\NME\ADMIN.BAK
	
	  This will backup the Post Office List.
	
	5. TYPE "NUL > M:\NME\ADMIN.NME" (without the quotation marks)
	
	  This will create an empty Post Office List.
	
	6. ACCTONME.EXE
	
	  Run this from the root of the PO, so that it sees all 19 Post Office
	  subdirectories. This will create a new version of the Post Office List based
	  on information in the local mail accounts files(ACCESS*.GLB).
	
	7. COPY M:\NME\ADMIN.NME M:\NME\ADMINSHD.NME
	
	  This will copy the Post Office List to its shadow file.
	
	8. IMPORT ADMIN -Ddrive -Ppassword -FGRPUSERS.DAT -A
	
	  This will add the extracted external user information from the file
	  GRPUSERS.DAT, which was created in the second step, back into the Post Office
	  List.
	
	9. GIMPORT ADMIN -Ddrive -Ppassword -FGROUPS.TXT -LGIMPORT.LOG -V
	
	  This will add the extracted group information from the file GROUPS.TXT, which
	  was created in the second step, back into the Post Office List.
	
	10. Groups on the affected PO must be modified to participate in dirsync,
	  regardless of former participation. This can be done by running the Mail
	  Administrator program, selecting the Local Admin - Groups - Modify command
	  and selecting Enter through each prompt until asked, "Include in group in
	  Directory Synchronization?". Select "Yes". In order for the Global Address
	  List to reflect changes made to the Post Office List, REBUILD.EXE -F -Ddrive
	  must be run. In order for remote users to see updated address lists, run
	  ADMIN.EXE and select the Remote - Regenerate command. Remote users must then
	  update their address lists.
	
	
	
	Additional query words: 2.10 3.00 3.20 saving restoring groups pol corrupt pcmailfaq
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN300 kbMailPCN350 kbMailPCN210
	Version           : :2.1,3.0,3.2,3.5
	
	=============================================================================
	

{% endraw %}
