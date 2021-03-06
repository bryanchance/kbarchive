---
layout: page
title: "Q252821: XGEN: Read Contact Properties from ASP Page with VBScript"
permalink: /kb/252/Q252821/
---

## Q252821: XGEN: Read Contact Properties from ASP Page with VBScript

{% raw %}

	Article: Q252821
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Operating System(s): 
	Keyword(s): exc55 exc55sp1 exc55sp2 exc55sp3
	Last Modified: 26-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides an example of how to use VBScript to retrieve the
	information for a contact in the Contacts folder.
	
	MORE INFORMATION
	================
	
	The following is an example of VBScript that retrieves and displays several, but
	not all, of the properties of a contact:
	
	  <%@ LANGUAGE="VBSCRIPT" %>
	
	  <HTML>
	  <HEAD>
	  <META NAME="GENERATOR" Content="Microsoft FrontPage 4.0">
	  <META HTTP-EQUIV="Content-Type" content="text/html;charset=iso-8859-1">
	  <TITLE>Document Title</TITLE>
	  </HEAD>
	  <BODY>
	
	  <%
	  CONST strServer = "server_name"
	  CONST strMailbox = "mailbox_name"
	
	  CONST CdoPR_GIVEN_NAME = &H3A06001F 'First Name
	  CONST CdoPR_INITIALS = &H3A0A001E 'Initials
	  CONST CdoPR_SURNAME = &H3A11001E 'Last Name
	  CONST CdoPR_DISPLAY_NAME = &H3001001F 'Display Name
	  CONST CdoPR_ACCOUNT = &H3A00001E 'Alias
	  CONST CdoPR_TITLE = &H3A17001F 'Title
	  CONST CdoPR_COMPANY_NAME = &H3A16001F 'Company
	  CONST CdoPR_BUSINESS_TELEPHONE_NUMBER = &H3A08001F
	  'BusinessTelephoneNumber
	
	  Dim objSession
	  Dim objMessages
	  Dim objMessage
	  Dim objFilter
	  Dim strProfileInfo
	
	  Response.Write ("<B><BR><Center>Contacts Information
	  Demo</center></B><BR>")
	
	  strProfileInfo = strServer & vbLf & strMailbox
	  Set objSession = CreateObject("MAPI.Session")
	  objSession.Logon , , False, False, , True, strProfileInfo
	
	  Set objFolder = objSession.GetDefaultFolder(5)
	
	  Set objMessages = objFolder.Messages
	  Set objFilter = objMessages.Filter
	
	  For Each objMessage In objMessages
	
	  if objMessage.Type = "IPM.Contact" then
	
	  Response.Write("<B> First Name:</B> " &
	  objMessage.Fields(CdoPR_GIVEN_NAME).Value & "<br>")
	
	  Response.Write("<B>Initials:</B> " &
	  objMessage.Fields(CdoPR_INITIALS).Value & "<br>")
	
	  Response.Write("<B>Last Name: </B>" &
	  objMessage.Fields(CdoPR_SURNAME).Value & "<br>")
	
	  Response.Write("<B>Display Name: </B>" &
	  objMessage.Fields(CdoPR_DISPLAY_NAME).Value & "<br>")
	
	  Response.Write("<B>Alias: </B>" &
	  objMessage.Fields(CdoPR_ACCOUNT).Value & "<br>")
	
	  Response.Write("<B>Title: </B>" &
	  objMessage.Fields(CdoPR_TITLE).Value & "<br>")
	
	  Response.Write("<B>Company: </B>" &
	  objMessage.Fields(CdoPR_COMPANY_NAME).Value & "<br>")
	
	  Response.Write("<B>Business Tel: </B>" &
	  objMessage.Fields(CdoPR_BUSINESS_TELEPHONE_NUMBER).Value & "<br>")
	
	  end if
	
	  Response.Write("<HR>")
	  Next
	
	  objSession.Logoff
	  Set objFilter = Nothing
	  Set objAddrEntries= Nothing
	  Set objSession = Nothing
	  %>
	  </BODY> </HTML>
	
	Additional query words: VBScript ActMsg CDO ASP
	
	======================================================================
	Keywords          : exc55 exc55sp1 exc55sp2 exc55sp3 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3
	Version           : winnt:5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
