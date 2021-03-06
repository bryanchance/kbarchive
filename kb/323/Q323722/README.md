---
layout: page
title: "Q323722: User Name Mapping Does Not Seem to Work and Event ID 1003 Occurs"
permalink: /kb/323/Q323722/
---

## Q323722: User Name Mapping Does Not Seem to Work and Event ID 1003 Occurs

{% raw %}

	Article: Q323722
	Product(s): Microsoft Windows NT
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Services for UNIX, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The User Name Mapping service does not seem to work with any of the Windows
	Services for UNIX components such at Client for NFS, Server for NFS, Gateway for
	NFS, and other components. All files are still being written by using anonymous
	permissions even though you configured User Name Mapping properly.
	
	Additionally, the following event ID message may be logged in the system log if
	you are running Server for NFS:
	
	  Event Type: Warning
	  Event Source: NfsSvr
	  Event ID: 1003
	  Description:
	  Mapping information could not be obtained from Username mapping. Another
	  attempt will be made after 30 minutes.
	
	NOTE: This problem only occurs if User Name Mapping is running on a remote
	server; however, if a negative entry (represented by a dash [-]) exists in the
	.Maphosts file, this problem does not occur.
	
	CAUSE
	=====
	
	The authentication mechanism that is used by the network file system (NFS)
	protocol is based on trust relationships between host computers. That is, an NFS
	server accepts the user identifiers (UIDs) and group identifiers (GIDs) from a
	specific client computer because the server is configured to recognize the
	client computer as trustworthy.
	
	User Name Mapping acts as an intermediary between NFS servers and NFS clients on
	a network that contains UNIX hosts and Windows-based computers. To maintain the
	implicit trust relationship between the NFS client and host computers, you must
	control which computers can access User Name Mapping and act as a trusted host
	on the NFS network.
	
	To control which computers can access User Name Mapping, edit the .Maphosts file
	in the <Windows_Services_for_UNIX_folder>\Mapper folder of the server that
	is running User Name Mapping. When you add entries in this file, you can easily
	allow or deny any other computer access to User Name Mapping. If the .Maphosts
	file is present but not empty, only those computers that are allowed access by
	entries that are included in the file can access User Name Mapping. If the
	.Maphosts file is present but it does not contain host entries (it contains only
	comments, which is the default text), only the computer that is running User
	Name Mapping can access User Name Mapping; no other computers can access this
	service. If the .Maphosts file is not present, no computers can access User Name
	Mapping, including the computer that is running User Name Mapping.
	
	RESOLUTION
	==========
	
	To resolve this issue, edit the .Maphosts file in the
	<Windows_Services_for_UNIX_folder>\Mapper folder on the User Name Mapping
	server.
	
	NOTE: When User Name Mapping matches a computer that is making a request against
	the elements in the list, it searches from the top down until it finds a match.
	As a result, the order of the entries is important.
	
	To edit the .Maphosts file, add any of the following elements:
	
	- host: Use this element to specify one or more computers that can access User
	  Name Mapping. You can specify the host by using an Internet Protocol (IP)
	  address (IP version 4) or as a host name that resolves to one or more IP
	  addresses.
	
	- host -: Use this element to specify one or more computers that are denied
	  access to User Name Mapping. You can specify the host as an IP address (IP
	  version 4) or as a host name that resolves to one or more IP addresses. Note
	  that you must use at least one blank space between "host" and the dash (-).
	
	- Plus sign (+) : Use only the plus sign (+) to specify that all computers can
	  access User Name Mapping unless they are denied access by an earlier entry in
	  the list. All of the entries in the list that follow this element are
	  ignored.
	
	- Dash (-): Use only the dash (-) to specify that all computers are denied
	  access to User Name Mapping unless they are allowed by an earlier entry in
	  the list. All of the entries in the list that follow this element are
	  ignored.
	
	Additional query words: sfu
	
	======================================================================
	Keywords          :  
	Technology        : kbWinServiceUNIXSearch kbWinServiceUNIX300
	Version           : :3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
