---
layout: page
title: "Q234038: Inodes and Inode Cache File(s) in Services for Unix."
permalink: /kb/234/Q234038/
---

## Q234038: Inodes and Inode Cache File(s) in Services for Unix.

{% raw %}

	Article: Q234038
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, used with:
	   - Microsoft Windows NT Services for UNIX Add-On Pack 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the inode files included in Services for UNIX Add-On
	Pack.
	
	MORE INFORMATION
	================
	
	What is an Inode?
	-----------------
	
	UNIX files do not actually reside in folders. A folder is really a file that
	contains references to other files. The folder holds two pieces of information
	about each file:
	
	- Its file name.
	
	- An inode number, which acts as a pointer to where the system can find the
	  information it needs about this file.
	
	File names are used by the system to locate a file and its inode number. This
	correspondence is called a link. To the system, the file is the inode number.
	Multiple file names can be used to refer to the same file by creating a link
	between an inode and each of the file names.
	
	What is an Inode File?
	----------------------
	
	The inode file caches pseudo-inode numbers for every file for which an NFS file
	handle is obtained in Server for NFS. Each drive letter in Server for NFS has a
	separate set of inode cache files. For example, the inode cache files for drive
	C are Drivec.nod and Drivec.ndx. The inode cache files for all drives are
	located by default in the C:\SFU\DiskShare folder.
	
	The inode file is used because 32-byte NFS file handles are not large enough to
	store entire path names. Using an inode file enables reliable recovery in the
	event of resource loss on the part of the client, the server, or the network.
	
	In large file systems, the inode file can become rather large. It can also become
	unusable, as a result of unpredictable events such as a power failure or a
	system crash. If the inode file becomes unusable or its size becomes a
	management problem because of a shortage of available free disk space, you may
	want to rebuild the inode file and restart the system.
	
	You can use the Rebuild Inodes tool (on the Server Options tab in the Server for
	NFS Configuration tool) to start a rebuild of the inode file, which prompts the
	user to restart the server. Using the Rebuild Inodes tool instructs Server for
	NFS to remove and re-create its inode file as part of the next Server for NFS
	startup. Alternatively, if Server for NFS is stopped for some reason, an
	administrator can simply delete the problem inode cache file before restarting
	the server or the Server for NFS service.
	
	NOTE: Removing or rebuilding the inode cache file and restarting Server for NFS
	requires any currently mounted clients to unmount and remount their shared
	resources. Symptoms may include error messages referring to a stale or invalid
	NFS file handle.
	
	Additional query words: sfu solar coaster
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTSsearch
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
