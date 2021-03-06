---
layout: page
title: "Q165914: XCLN: Troubleshooting the Free/Busy Connector"
permalink: /kb/165/Q165914/
---

## Q165914: XCLN: Troubleshooting the Free/Busy Connector

{% raw %}

	Article: Q165914
	Product(s): Microsoft Exchange
	Version(s): 4.0 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Schedule+ Free/Busy Connector is installed with the Microsoft Mail
	Connector. Only one Schedule+ Free/Busy Connector will be installed in a
	Microsoft Exchange Site. To make free/busy information available to all Sites in
	your Microsoft Exchange Organization, you must replicate the directories between
	Sites and replicate the Schedule+ Free/Busy Information public folder on every
	Server that has the Schedule+ Free/Busy Connector installed. Use the Schedule+
	Free/Busy Connector Options property page to configure Microsoft Exchange Server
	to replicate Microsoft Schedule+ Free/Busy information between Microsoft
	Exchange Server Sites and Microsoft Mail postoffices. Once you have configured
	the Schedule+ Free/Busy Connector, you can start it by choosing the Services
	icon from the Control Panel. There are very few parts to the gateway and if the
	following methodical approach is followed, most, if not all, issues relating to
	both the Microsoft Mail Schedule distribution process and the Microsoft Exchange
	Server Free/Busy connector should work.
	
	MORE INFORMATION
	================
	
	1. Verification of proper connector setup: There are two Microsoft Knowledge
	  Base articles to reference when troubleshooting the connector:
	
	  Q147698 XADM: Configuring the Schedule+ Free/Busy Connector
	
	  Q141755 PC WSPlus: How to Setup Schedule Distribution
	
	  Also look at the README.WRI file on the Microsoft Exchange Server compact
	  disk.
	
	2. Things to check on the Microsoft Exchange Server:
	
	  a. Verify that Mail flows between the Microsoft Exchange server and Microsoft
	     Mail postoffices.
	
	  b. Verify that Directory Synchronization (DirSync) is functioning.
	
	  c. Verify that the distribution list being used contains the ADMINSCH
	     Accounts for all PO's to be included in the Free/Busy Process.
	
	  d. Verify that the Sending time for the Free/Busy connector is set to 15
	     minutes or greater.
	
	  e. Set logging on the Free/Busy connector to External or higher.
	
	3. Things to Check on Microsoft Mail:
	
	  a. Run Adminsch.exe (from the Schedule+ diskette that ships with Microsoft
	     Mail).
	
	  b. Verify that the Microsoft Exchange Server is listed (so the adminsch
	     account can receive information).
	
	  c. Verify that the default sending time is set to 15 minutes or greater.
	
	  d. Verify that Schdist.exe is running against all Microsoft Mail postoffices
	     included in Schedule Distribution but not against the Microsoft Exchange
	     Proxy postoffice.
	
	  e. Use the -V and -l<path>\logname.log command line switch to have
	     Schdist.exe create a log file.
	
	  f. Do not run a Windows Mail client using the adminsch account, use a DOS
	     client instead.
	
	4. What to do when things go wrong:
	
	  If free/busy information is not being seen on the Microsoft Exchange Server:
	
	  a. Verify that mail is flowing between Microsoft Exchange and Microsoft Mail.
	
	  b. Verify, in Adminsch.exe, that the Microsoft Mail postoffice is sending to
	     the Microsoft Exchange Server.
	
	  c. Verify that Schdist.exe is being run against the postoffice in question.
	
	  d. On the Microsoft Exchange Server computer, review the Event Log for Event
	     ID's. 1004 (MSExchangeFB) refers to a message being received from the
	     Schdist process.
	
	  If Free Busy information is not being seen on MS Mail:
	
	  a. Verify, in Adminsch.exe, that the Microsoft Exchange Server Proxy
	     postoffice is listed and that the Last received time is current.
	
	  b. Review the logs created by Schdist.exe, looking for errors processing
	     messages.
	
	  c. Verify that Schdist.exe is being run against the Microsoft Mail
	     postoffice.
	
	  d. Verify that the Adminsch account for the Microsoft Mail postoffice is
	     listed in the Distribution list used by the Free/Busy connector.
	
	  e. Review the Microsoft Exchange Server computer's Event Log for 1002 errors.
	
	5. When all else fails:
	
	  a. Reset the Admin.prf and .pof files on one Microsoft Mail postoffice by
	     copying them to a safe location and then deleting them from the CAL
	     directory.
	
	     Note: Resetting these files will cause missing Free/Busy information for
	     individuals until those individuals log into Schedule + and make a change
	     to their schedule. At that point, the client will write all free busy
	     information to the 00000000.POF For Resources, someone will have to log in
	     as the resource and make a change to the schedule in order to have the
	     Free/Busy re-populated. The Admin.prf file is recreated when Adminsch.exe
	     is run and postoffices are added.
	
	  b. On the Microsoft Exchange Server, run the Microsoft Administrator program
	     and bring up the properties of the Free/Busy Connector. Instead of using
	     the Distribution List which contains all the Microsoft Mail postoffices,
	     only use the Adminsch account on the postoffice listed above.
	
	  c. Set logging on the Free/Busy connector to External or higher.
	
	  d. Set logging on the Schdist.exe using -v and -l.
	
	  e. Make a change to a Microsoft Mail schedule.
	
	  f. Start Schdist.exe against the single postoffice only. You should see a
	     message being generated destined to the Microsoft Exchange Server.
	
	  g. Wait for the message from Schdist to be picked up and delivered to
	     Microsoft Exchange. Increase the Logging on the MSMI to view this.
	
	  h. Once delivered you should see the 1004 event in the Microsoft Exchange
	     Server computer's Event log.
	
	  i. On Microsoft Exchange, have a user create an appointment.
	
	  j. After waiting 15 minutes, you should see event id 1003, which will show
	     the F/B gateway sending a message.
	
	  k. Start Schdist.exe on the Microsoft Mail side and you should see the
	     message being received.
	
	  l. Verify in Adminsch.exe that the last received time is current.
	
	  m. Check a client on both the Microsoft Mail and Microsoft Exchange side,
	     verifying the Free/Busy information for the users is being displayed.
	
	  n. At this time, add back the Microsoft Mail postoffices, one at a time.
	
	Additional query words: quick reference guide ref
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : 4.0 5.0
	
	=============================================================================
	

{% endraw %}
