---
layout: page
title: "Q175283: XADM: How to Run PerfWiz in Silent Mode or Batch Mode"
permalink: /kb/175/Q175283/
---

## Q175283: XADM: How to Run PerfWiz in Silent Mode or Batch Mode

{% raw %}

	Article: Q175283
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kbusage exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article describes how to run Performance Optimizer in silent mode or batch
	mode, which allows it to run without interaction from the user.
	
	MORE INFORMATION
	================
	
	Follow these steps to run Performance Optimizer (PerfWiz) in silent mode:
	
	1. Create a text file named Perfopt.inf in the same folder as the Perfwiz.exe
	  file. See the "Creating the INF File" section of this article.
	
	2. Run PerfWiz with the -s option. PerfWiz runs silently and finishes without
	  any user intervention. The log file is still written in the usual place.
	
	3. Run PerfWiz with the -f <inf file> option. PerfWiz runs silently and
	  finishes without any user intervention. The log file is still written in the
	  usual place. The <inf file> can be any arbitrary file that conforms to
	  the same format as the Perfopt.inf file (see the "Creating the INF File"
	  section of this article).
	
	
	Creating the INF File
	---------------------
	
	The format of the INF file should read as follows. Be careful to take note of the
	spacing between words.
	
	     [Perfwiz]
	     Users=[0|1|2|3|4|5]
	     Org Users=[0|1|2|3|4]
	     Server Type=number (see below)
	     Dont Restart=[0|1]
	     Analyze Disks=[0|1]
	     Move Files=[0|1]
	     Limit Memory Usage=number of megabytes
	
	Here is a description of each of the keys above:
	
	Users - Corresponds to the "Number of users you will host on this server"
	question.
	
	  Value Meaning
	    0   Less than 500
	    1   500 - 999
	    2   1,000 - 4,999
	    3   5,000 - 24,999
	    4   25,000 - 49,000
	    5   50,000 or more
	
	Default is set to 0 for Users.
	
	Org Users - Corresponds to the "Number of users in your organization" question.
	
	  Value Meaning
	     0  Less than 1,000
	     1  1,000 - 9,999
	     2  10,000 - 99,999
	     3  100,000 - 499,999
	     4  500,000 or more
	
	Default is set to 0 for Org Users.
	
	Server Type - Corresponds to the "What type of server will this computer be
	configured to be" question. The value can be any combination (by addition) of
	the following values (for example, if the server will serve a Private, Public,
	and Connector role, the value will be 1 + 2 + 4, which will be 7).
	
	  Value Meaning
	  Nothing Selected  = 0
	  Public  = 1
	  Private  = 2
	  Private,Public = 3
	  Connector/Directory Import = 4
	  Connector/Directory Import,Public = 5
	  Connector/Directory Import,Private= 6
	  Connector/Directory Import,Private,Public= 7
	  Multi-server = 8
	  Public,Multi-server = 9
	  Private,Multi-server = 10
	  Private,Public,Multi-server = 11
	  Connector/Directory Import,Multi-server = 12
	  Public,Multi-server,Connector/Directory Import = 13
	  Private,Multi-server,Connector/Directory Import = 14
	  Private,Public,Multi-server,Connector/Directory Import = 15
	  POP3 = 16
	
	Default is set to Private Server.
	
	NOTE: If POP3 is set, Private Server is also set; Public Server and Connector are
	cleared.
	
	The following keys can have the value FALSE (No) or TRUE (Yes) respectively.
	
	Dont Restart - Don't restart the services after running the optimizer. This is
	highly recommended to be FALSE if running in silent mode. Default is set to
	FALSE.
	
	Analyze Disks - TRUE if the disks should be analyzed by the optimizer. Set this
	to FALSE if you are sure the various Exchange Server files reside in their ideal
	locations. Default is set to TRUE.
	
	Move Files - TRUE if files should be moved after disk analysis has determined
	that they need to be moved. This is ignored if Analyze Disks is set to FALSE.
	This is highly recommended to be TRUE if Analyze Disks is TRUE when running in
	silent mode. Default is set to TRUE.
	
	You can use either of the following two command lines to run PerfWiz
	successfully:
	
	  Perfwiz -s
	
	  -or-
	
	  Perfwiz -f c:\exchsrvr\bin\perfopt.inf
	
	Run either at the command line in the root of the Exchsrvr\Bin folder. Make sure
	the Perfopt.inf file is stored at this root as well.
	
	Limit Memory Usage - If you remove the Limit Memory Usage line from the INF file,
	it removes the option to limit memory.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
