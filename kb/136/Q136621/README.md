---
layout: page
title: "Q136621: Description of Full, Incremental, and Differential Backups"
permalink: /kb/136/Q136621/
---

## Q136621: Description of Full, Incremental, and Differential Backups

{% raw %}

	Article: Q136621
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kbtool win95
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes full, incremental, and differential backups. The Backup
	tool in Windows 95 supports full and incremental backups. Differential backups
	are not supported.
	
	Backup uses backup file sets to help you manage backing up drives, folders, or
	files. Incremental and differential backups rely on an initial full backup of
	the drives, folders, or files in question.
	
	MORE INFORMATION
	================
	
	Many Windows 3.1-based backup programs use the archive bit to mark files that
	have been backed up. Backup does not use the archive bit in any way. The
	decision as to whether or not a file should be backed up in an incremental
	backup is based on the filename, its last modified date, and the date of the
	last incremental backup, all of which are stored in the file set.
	
	Full Backup (or Reference Backup)
	---------------------------------
	
	When you set the Backup Type setting to Full, all the files and folders on the
	drive are backed up every time you use that file set. To set the backup type,
	click Options on the Settings menu, and then click the Backup tab.
	
	Example:
	
	1. In Backup, click the drives, files, or folders to back up, and then click
	  Next Step.
	
	2. Click the destination (where you want the files backed up to).
	
	3. On the Settings menu, click Options, click the Backup tab, click "Full:
	  backup of all selected files," and then click OK.
	
	4. On the File menu, click Save As and name your backup set. Once saved, click
	  Start Backup.
	
	5. Provide a name for the selected drive, files, or folders in the Backup Set
	  Label dialog box, and then click OK.
	
	Advantages:
	
	- All files from the selected drives and folders are backed up to one backup
	  set.
	
	- In the event you need to restore files, they are easily restored from the
	  single backup set.
	
	Disadvantages:
	
	- A full backup is more time consuming than other backup options.
	
	- Full backups require more disk, tape, or network drive space.
	
	Incremental Backup
	------------------
	
	An incremental backup provides a backup of files that have changed or are new
	since the last incremental backup. To start the process, a file set with the
	incremental option selected is used to perform a backup. You can select the
	backup type by clicking Options on the Settings menu, and then clicking the
	Backup tab.
	
	For the first incremental backup, all files in the file set are backed up (just
	as in a full backup). If you use the same file set to perform a incremental
	backup later, only the files that have changed are backed up. If you use the
	same file set for a third backup, only the files that have changed since the
	second backup are backed up, and so on.
	
	In Backup, you can select files and/or folders to be backed up. If you select a
	folder, all the files and folders within that folder are selected. In an
	incremental backup, if you select a folder, files that are added to the folder
	are included during the next backup. If you select specific files, files that
	are added to the folder are not included during the next backup.
	
	Example:
	
	Monday - Perform the first incremental backup of selected files and/or
	        folders using a file set with the Incremental option enabled.
	
	Tuesday - Perform another backup with the backup file set you created
	         Monday. Only files that have changed since Monday's backup are
	         backed up.
	
	Wednesday - Perform another backup with the backup file set you created
	           Monday. Only files that have changed since Tuesday's
	           incremental backup are backed up.
	
	To reset a file set so that the next backup backs up all files, and not just
	files that are new or have changed, follow these steps:
	
	1. On the File menu, click Open File Set. Click the file set you want to use,
	  and then click Open. Click Next Step.
	
	2. Click the destination (where you want the files backed up to).
	
	3. On the Settings menu, click Options, click the Backup tab, click "Full:
	  backup of all selected files," and then click OK.
	
	4. On the File menu, click Save to save your backup set.
	
	5. Repeat steps 1 and 2.
	
	6. On the Settings menu, click Options, click the Backup tab, click
	  "Incremental: backup of selected files that have changed since the last full
	  backup," and then click OK.
	
	Advantages:
	
	- Backup time is faster than full backups.
	
	- Incremental backups require less disk, tape, or network drive space.
	
	- You can keep several versions of the same files on different backup sets.
	
	Disadvantages:
	
	- In order to restore all the files, you must have all of the incremental
	  backups available.
	
	- It may take longer to restore a specific file since you must search more than
	  one backup set to find the latest version of a file.
	
	Differential Backup (Not Supported in Backup)
	---------------------------------------------
	
	A differential backup provides a backup of files that have changed since a full
	backup was performed. A differential backup typically saves only the files that
	are different or new since the last full backup, but this can vary in different
	backup programs. Together, a full backup and a differential backup include all
	the files on your computer, changed and unchanged.
	
	Example:
	
	Monday - Perform a full backup and save the file set.
	
	Tuesday - Perform a differential backup using the same file set. All files
	         that have changed since the full backup are backed up in the
	         differential backup.
	
	Wednesday - Perform a differential backup using the same file set. All the
	           files that have changed since Monday's full backup are backed
	           up.
	
	Advantages:
	
	- Differential backups require even less disk, tape, or network drive space
	  than incremental backups.
	
	- Backup time is faster than full or incremental backups.
	
	Disadvantages:
	
	- Restoring all your files may take considerably longer since you may have to
	  restore both the last differential and full backup.
	
	- Restoring an individual file may take longer since you have to locate the
	  file on either the differential or full backup.
	
	Additional query words: described explained
	
	======================================================================
	Keywords          : kbtool win95 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
