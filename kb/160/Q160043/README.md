---
layout: page
title: "Q160043: Err Msg: Error Defragmenting Drive &lt;X&gt;. Windows Could Not..."
permalink: /kb/160/Q160043/
---

## Q160043: Err Msg: Error Defragmenting Drive &lt;X&gt;. Windows Could Not...

{% raw %}

	Article: Q160043
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95; Win2000:95
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbtool scandisk win95 defrag kbDefrag kbScanDisk
	Last Modified: 01-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Plus! for Windows 95 
	- Microsoft Windows 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run Disk Defragmenter (Defrag.exe), you may receive the following error
	message:
	
	  Error Defragmenting Drive <drive>. Windows could not access part of the
	  drive. Click Help and carry out the instructions for running ScanDisk.
	  IMPORTANT: To fix this problem, you must run ScanDisk and choose the Thorough
	  option.
	  ID No: DEFRAG005
	
	Note that the "ID No: DEFRAG005" portion of the error message may be replaced by
	"ID No: DEFRAG006."
	
	CAUSE
	=====
	
	This error occurs when Disk Defragmenter is unable to read from or write to one
	or more bad sectors on the hard disk. The DEFRAG005 error message is displayed
	when Disk Defragmenter is unable to write to a sector. The DEFRAG006 error
	message is displayed when Disk Defragmenter is unable to read from a sector.
	
	RESOLUTION
	==========
	
	Before you attempt to work around this problem, you should first make a backup
	copy of any important data on your hard disk. After doing so, run ScanDisk
	(Scandskw.exe) and perform a thorough test on the hard disk. To do so, follow
	these steps:
	
	1. Click the Start button, point to Programs, point to Accessories, point to
	  System Tools, and then click ScanDisk.
	
	2. Click the hard disk referenced in the error message, and then click Thorough
	  in the Type Of Test area.
	
	3. Click Options, verify that System And Data Areas is selected, and then click
	  OK.
	
	4. Click Start to begin the test.
	
	If ScanDisk does not find any bad sectors, or if running ScanDisk does not
	correct the problem, configure ScanDisk to detect disk timeouts and check each
	cluster five times while performing a surface scan. To do so, follow these
	steps:
	
	1. Use any text editor (such as Notepad) to open the Scandisk.ini file in the
	  Windows\Command folder.
	
	2. Create an [Environment] section in the file, if the section does not already
	  exist, and then add the following lines to the section:
	
	  " ScanTimeOut=On
	  NumPasses=5 " (without the quotation marks)
	
	  Note that the "ScanTimeOut=" and "NumPasses=" lines may already exist, but
	  with different values.
	
	3. Save and then close the Scandisk.ini file.
	
	4. Click the Start button, click Shut Down, click "Restart the computer in
	  MS-DOS mode," and then click Yes.
	
	5. Type the following line and then press ENTER to run ScanDisk
	
	  " scandisk <drive>: " (without the quotation marks)
	
	  where <drive> is the drive letter of the hard disk you want to check.
	  Note that you should run a surface scan when ScanDisk prompts you to do so,
	  repair any errors that ScanDisk finds, and view and save the log file that
	  ScanDisk creates.
	
	6. When ScanDisk is finished, type "exit" (without the quotation marks) and then
	  press ENTER to return to Windows 95.
	
	7. Run Disk Defragmenter again.
	
	If you still receive the above error message, run Disk Defragmenter to
	consolidate free space only, then defragment files only, and then perform a full
	defragmentation (both files and free space). To do this, follow these steps:
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click Disk Defragmenter.
	
	2. Click the hard disk referenced in the error message, and then click OK.
	
	3. Click Advanced, click Consolidate Free Space Only, and then click OK.
	
	4. Click No when you are prompted to quit Disk Defragmenter.
	
	5. Click the hard disk referenced in the error message, and then click OK.
	
	6. Click Advanced, click Defragment Files Only, and then click OK.
	
	7. Click No when you are prompted to quit Disk Defragmenter.
	
	8. Click the hard disk referenced in the error message, and then click OK.
	
	9. Click Advanced, click "Full defragmentation (both files and free space)", and
	  then click OK.
	
	10. Click Yes when you are prompted to exit Disk Defragmenter.
	
	If ScanDisk does not find any bad sectors, or if running ScanDisk does not
	correct the problem, contact the manufacturer of your computer or hard disk to
	inquire about additional workarounds that may correct the problem.
	
	MORE INFORMATION
	================
	
	Many hard disks have sectors that are unusable. If the sectors have been marked
	as bad by ScanDisk or another disk tool, Disk Defragmenter displays the sector
	as a white box with a red line through it. This indicates that the cluster has
	been marked as bad and cannot be used to store data.
	
	If the disk tool you use is unable to detect bad sectors on your hard disk, or if
	you do not run a disk tool on a regular basis, unusable sectors that are not
	marked as bad may exist on the disk. When this occurs, you may not realize that
	the bad sectors exist until Windows 95 attempts to store data in them.
	Therefore, it is possible for bad sectors to appear while you are using the
	drive normally. If bad sectors begin to appear on a regular basis, your hard
	disk may need to be repaired or replaced.
	
	Note that you may be able to prevent the error message from being displayed by
	deleting some files on your hard disk, but doing so does not fix the problem
	that is causing the error message to appear. Disk Defragmenter does not read
	from unused sectors while defragmenting a drive. Therefore, if an unusable
	sector that does not contain any data exists on your hard disk, the problem
	described in this article may not occur.
	
	Additional query words: osr1 osr2
	
	======================================================================
	Keywords          : kbenv kberrmsg kbtool scandisk win95 defrag kbDefrag kbScanDisk 
	Technology        : kbWin95search kbWin98search kbGamesSearch kbPlusSearch kbZNotKeyword3 kbWin98 kbPlus95
	Version           : WINDOWS:95; Win2000:95
	
	=============================================================================
	

{% endraw %}
