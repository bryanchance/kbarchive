---
layout: page
title: "Q308175: DOC: Broken Links in ASP Help Files"
permalink: /kb/308/Q308175/
---

## Q308175: DOC: Broken Links in ASP Help Files

{% raw %}

	Article: Q308175
	Product(s): Internet Information Server
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocerr
	Last Modified: 10-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you click the following links on the following IIS Help pages, the expected
	page does not appear in the browser:
	
	Page                              Link
	-----------------------------------------------------------
	Installable Components for ASP    Logging Utility Component
	Response Object                   CodePage
	Response Object                   LCID
	ASP Tutorial                      IIS snap-in
	
	MORE INFORMATION
	================
	
	The following four files are missing from the Winnt/Help/Iishelp/Iis/Htm/Asp
	directory:
	
	- Comp6i5w.htm
	
	- Vbob150l.htm
	
	- Vbob055w.htm
	
	- Iisbuti.htm
	
	To resolve this problem, paste the data for each of the missing files in Notepad,
	and then name the files as specified.
	
	Page 1: Installable Components for ASP:
	
	- Page: Installable Components for ASP
	
	- Link: Logging Utility Component
	
	- Directory and file name: Winnt/Help/Iishelp/Iis/Htm/Asp/Comp6i5w.htm
	
	Paste the following code in Notepad, name the file Comp6i5w.htm, and then save
	the file in the Winnt/Help/Iishelp/Iis/Htm/Asp directory:
	
	  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
	  <HTML DIR="LTR"><HEAD>
	  <META HTTP-EQUIV="Content-Type" Content="text/html; charset=Windows-1252">
	  <TITLE>Logging Utility Component</TITLE>
	  <style>@import url(coua.css);</style>
	  <link disabled rel="stylesheet" href="cocss.css"><META NAME="DESCRIPTION" CONTENT="Internet Information Services reference information">
	  </HEAD>
	  <body topmargin=0 id="bodyID">
	
	  <TABLE CLASS="buttonbarshade" CELLSPACING=0><a name="top"></a><TR><TD>&#xa0;</TD></TR></TABLE>
	  <TABLE CLASS="buttonbartable" CELLSPACING=0>
	  <TR ID="hdr"><TD CLASS="runninghead">Platform&#xa0;SDK:&#xa0;Internet&#xa0;Information&#xa0;Services&nbsp5.1</TD></TR>
	  </TABLE>
	
	  <H1><A NAME="_logging_utility_component"></A>Logging Utility Component</H1>
	
	  <P>The IIS Log component is used to create an <B>IISLog </B>object, which enables your applications to read from the IIS log. 
	  This component allows you to quickly create, for example, ASP scripts or VB components that programmatically walk through 
	  daily log files so that certain types of information can be extracted.</P>
	
	  <P class=indent><B><B>Important</B></B></P>
	
	  <P class=indent>The user accessing the ASP script that instantiates the <B>IISLog</B> component must be authenticated as an 
	  Administrator or Operator on the server on which IIS is running. If the user is only Anonymous, the IIS Log component will not 
	  function properly.</P>
	
	  <P><B>File Names</B></P>
	  <table>
	
	  <TR VALIGN="top">
	  <TD width=50%>Logscrpt.dll</TD>
	  <TD width=50%>The Logging Utility component</TD>
	  </TR>
	  </table>
	
	  <P><B>Syntax</B></P>
	
	  <PRE class="syntax"><B>Set </B><I>oIISLog</I><B> = Server.CreateObject( MSWC.IISLog ) </B>
	  <B> </B></PRE>
	
	  <P><B>Parameters</B>
	
	  <DL>
	  <DT><I>oIISLog</I></DT>
	
	  <DD>Specifies the name that can be used as a reference to the <B>IISLog </B>component.</dd>
	  </DL>
	
	  <P><B>Methods</B></P>
	  <table>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp4rzb.htm">AtEndOfLog</A></TD>
	  <TD width=50%>Indicates whether all records have been read from the log file.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp5dtf.htm">CloseLogFiles</A></TD>
	  <TD width=50%>Closes all open log files.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp6hnp.htm">OpenLogFile</A></TD>
	  <TD width=50%>Opens a log file for reading or writing.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp1cqa.htm">ReadFilter</A></TD>
	  <TD width=50%>Filters records from the log file by date and time.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp6jms.htm">ReadLogRecord</A></TD>
	  <TD width=50%>Reads the next available log record from the current log file.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp4290.htm">WriteLogRecord</A></TD>
	  <TD width=50%>Writes a log record to the current log file.</TD>
	  </TR>
	  </table>
	
	  <P><B>Properties</B></P>
	  <table>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp6xt0.htm">BytesReceived</A></TD>
	  <TD width=50%>Indicates the bytes received.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp7dv8.htm">BytesSent</A></TD>
	  <TD width=50%>Indicates the bytes sent.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp4d2o.htm">ClientIP</A></TD>
	  <TD width=50%>Indicates the client's host name.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp8wf9.htm">Cookie</A></TD>
	  <TD width=50%>Indicates the client's cookie.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp7k37.htm">CustomFields</A></TD>
	  <TD width=50%>Indicates an array of custom headers</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp5smd.htm">DateTime</A></TD>
	  <TD width=50%>Indicates the date and time in GMT.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp0xpg.htm">Method</A></TD>
	  <TD width=50%>Indicates the operation type.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp735f.htm">ProtocolStatus</A></TD>
	  <TD width=50%>Indicates the protocol status.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp0g8e.htm">ProtocolVersion</A></TD>
	  <TD width=50%>Indicates the version string.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp3epe.htm">Referer</A></TD>
	  <TD width=50%>Indicates the referrer page.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp7ohc.htm">ServerIP</A></TD>
	  <TD width=50%>Indicates the server's IP address.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp4dk5.htm">ServerName</A></TD>
	  <TD width=50%>Indicates the server name.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp6ulw.htm">ServerPort</A></TD>
	  <TD width=50%>Indicates the port number.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp32g5.htm">ServiceName</A></TD>
	  <TD width=50%>Indicates the service name.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp052m.htm">TimeTaken</A></TD>
	  <TD width=50%>Indicates the total processing time.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp254p.htm">URIQuery</A></TD>
	  <TD width=50%>Indicates any parameters passed with the request.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp3u7h.htm">URIStem</A></TD>
	  <TD width=50%>Indicates the target URL.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp20hg.htm">UserAgent</A></TD>
	  <TD width=50%>Indicates the user agent string.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp2vc5.htm">UserName</A></TD>
	  <TD width=50%>Indicates the user's name.</TD>
	  </TR>
	
	  <TR VALIGN="top">
	  <TD width=50%><A HREF="comp6yer.htm">Win32Status</A></TD>
	  <TD width=50%>Indicates the Win32 status code.</TD>
	  </TR>
	  </table>
	
	  <P class=indent><B><B>Note</B></B></P>
	
	  <P class=indent>The following steps are necessary to use the IIS Log component effectively:
	
	  <UL>
	  	<LI>Use the OpenLogFile method to specify from which log file or files the IISLog component should read.</li>
	
	  	<LI>Use the ReadLogRecord to read the appropriate log records.</li>
	
	  	<LI>Use the IIS Log component properties to retrieve specific information from the log records.</li>
	  </UL>
	
	  <P class=indent><B><B>Important</B></B></P>
	
	  <P class=indent>Only log files created by logging modules that support log file reading will be accessible through this component. 
	  The four built-in logging modules that come with IIS support log-file reading, but if you are using a custom or third-party 
	  logging module, you will need to enhance the logging module. See <A HREF="logg40mr.htm">Extending IIS Logging Capabilities</A> 
	  for more information.</P>
	  <!-- Info Task Footer -->
	  <DIV CLASS="itfBorder"><IMG SRC="tiny.gif" WIDTH="1" HEIGHT="1"></DIV>
	  <DIV CLASS="itf"><B>Platform SDK Release: <FONT COLOR="#ddaa00">January 2002</FONT></B>
	  <TABLE CELLPADDING="0" CELLSPACING="0"><TR><TD WIDTH="43%">
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com"><IMG SRC="sendfdbk.gif" BORDER="0"/></A>&#xa0; 
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com">Contact Platform SDK</A></TD>
	  <TD><A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" TITLE="Order a CD online.">
	  <IMG SRC="download.gif" BORDER="0"/></A>&#xa0;
	  <A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" 
	  TITLE="Order a CD online.">Order a Platform SDK CD Online</A></TD></TR></TABLE></DIV>
	  <P>&#xa0;</P>
	  </BODY>
	  </HTML>
	
	Page 2: Response Object:
	
	- Page: Response Object
	
	- Link: CodePage
	
	- Directory and file name: Winnt/Help/Iishelp/Iis/Htm/Asp/Vbob150l.htm
	
	Paste the following code in Notepad, name the file Vbob150l.htm, and then save
	the file in the Winnt/Help/Iishelp/Iis/Htm/Asp directory:
	
	  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
	  <HTML DIR="LTR"><HEAD>
	  <META HTTP-EQUIV="Content-Type" Content="text/html; charset=Windows-1252">
	  <TITLE>CodePage</TITLE>
	  <style>@import url(coua.css);</style>
	  <link disabled rel="stylesheet" href="cocss.css"><META NAME="DESCRIPTION" CONTENT="Internet Information Services reference information">
	  </HEAD>
	  <body topmargin=0 id="bodyID">
	
	  <TABLE CLASS="buttonbarshade" CELLSPACING=0><a name="top"></a><TR><TD>&#xa0;</TD></TR></TABLE>
	  <TABLE CLASS="buttonbartable" CELLSPACING=0>
	  <TR ID="hdr"><TD CLASS="runninghead">Platform&#xa0;SDK:&#xa0;Internet&#xa0;Information&#xa0;Services&nbsp5.1</TD></TR>
	  </TABLE>
	
	  <H1><A NAME="_response_codepage"></A>CodePage</H1>
	
	  <P>The <B>CodePage</B> property specifies how strings are encoded in the intrinsic objects. A codepage is a character set that 
	  can include numbers, punctuation marks, and other glyphs. Codepages are not the same for each language. Some languages such as 
	  Japanese and Hindi have multi-byte characters, while others like English and German only need one byte to represent each 
	  character. The <B>CodePage</B> property is read/write.</P>
	
	  <P><B>Syntax</B></P>
	
	  <PRE class="syntax"><B>Response.CodePage </B>[<B>=</B> <I>CodePageID </I>]
	  </PRE>
	
	  <P><B>Parameters</B>
	
	  <DL>
	  <DT><I>CodePageID</I></DT>
	  </DL>
	
	  <P>An integer representing the character formatting codepage. You can find codepage integers at 
	  <a href="http://go.microsoft.com/fwlink/?LinkId=1756" target=_blank><b>MSDN Web Workshop</b></a> 
	  under the column for FamilyCodePage.</P>
	
	  <P><B>Notes</B></P>
	
	  <P>Setting Response.CodePage explicitly affects a single page, where Session.CodePage affects all responses in a session. </P>
	
	  <P>If Response.CodePage is not explicitly set in a page, it is implicitly set by Session.CodePage, if sessions are enabled. 
	  If sessions are not enabled, Response.CodePage is set by @CodePage, if @CodePage is present in the page. If there is no 
	  @CodePage in the page, Response.CodePage is set by the AspCodePage metabase property. If the AspCodePage metabase property is 
	  not set, or set to 0, Response.CodePage is set by the system ANSI codepage.</P>
	
	  <P>There can be only one codepage per response body, otherwise incorrect characters are displayed. If you set the codepage 
	  explicitly in two pages where one is called by the other with #include, Server.Execute, or Server.Transfer, usually the parent 
	  page decides the codepage. The only exception is if Response.CodePage is explicitly set in the parent page of a Server.Execute call. 
	  In that case, an @CodePage command in the child page overrides the parent codepage.</P>
	
	  <P>Literal strings in a script are still encoded using @CodePage (if present) or the AspCodePage metabase value (if set), 
	  or the system ANSI codepage. If you set Response.CodePage or Session.CodePage explicitly, do so before sending 
	  non-literal strings to the client. If you use literal and non-literal strings in the same page, make sure the codepage of 
	  @CodePage matches the codepage of Response.CodePage, or the literal strings are encoded differently from the non-literal strings 
	  and display incorrectly.</P>
	
	  <P>If the codepage of your Web page matches the system defaults of the Web client, you do not need to set a codepage in your Web page. 
	  However, setting the value is recommended.</P>
	
	  <P>If the codepage is set in a page, then <B>Response.Charset</B> should also be set. The codepage value tells IIS how to encode 
	  the data when building the response, and the charset value tells the browser how to decode the data when displaying the 
	  response. The <I>CharsetName</I> of Response.Charset must match the codepage value, or mixed characters will be displayed 
	  in the browser. Lists of <I>CharsetNames</I> and matching codepage values can be found at 
	  <a href="http://go.microsoft.com/fwlink/?LinkId=1756" target=_blank><b>MSDN Web Workshop</b></a> under the columns for Preferred 
	  Charset Label and FamilyCodePage.</P>
	
	  <P>The file format of a Web page must be the same as the @CodePage used in the page. Notepad.exe allows you to save files in 
	  UTF-8 format or in the system ANSI format. For example, if @CodePage is set to 65001 indicating UTF-8, the Web file must be 
	  saved in UTF-8 format. If @CodePage is set to 1252 indicating English or German, the Web file must be saved in ANSI format 
	  on an English or German system. If you want to save a page in the ANSI format for a language other than your system language, 
	  you can change your default System Locale in Regional Options from the Control Panel. For example, once you change your system 
	  locale to Japanese, any files you save in ANSI format are saved using the Japanese codepage and are only readable from a Japanese 
	  System Locale.</P>
	
	  <P>If you are writing and testing Web pages that use different codepages and character sets (for example, creating a multi-lingual 
	  Web site), remember that your test client-computer must have the language packs installed for each language you wish to display. You 
	  can install language packs from Regional Options in the Control Panel.</P>
	
	  <P><B>Example</B></P>
	
	  <P>The following example shows the home page of a multi-lingual site. The home page is saved in UTF-8 format so characters from all 
	  languages can be shown. The home page redirects the client to a page of their language by using the ServerVariable HTTP_ACCEPT_LANGUAGE 
	  to discern the language of the client.</P>
	
	  <P>--- Default.asp ---</P> 
	  <PRE><%@ CodePage=65001 Language="VBScript"%> <%
	  ' Default.asp
	  ' This file is saved in UTF-8 format.
	  ' The codepage of the system doesn't matter because
	  ' you are setting @CodePage, Response.CodePage, and Response.Charset.
	  ' Otherwise, the system codepage of the server would be the default.
	
	  Response.CodePage = 65001
	  Response.CharSet = "utf-8"
	
	  ' Redirect to the correct home page based on the client language.
	  Select Case Request.ServerVariables("HTTP_ACCEPT_LANGUAGE")
	
	    Case "en-us", "en", "fr", "fr-fr", "es", "es-es", "zh", "zh-cn", "zh-tw"
	      Response.Redirect Request.ServerVariables("HTTP_ACCEPT_LANGUAGE") & "Start.asp"
	
	    Case Else
	      %>
	      Welcome.  Click <a href="enStart.asp">here</a> to go to the English Web site.<BR><BR>
	      Bienvenue. Cliquetez <a href="frStart.asp">ici</a> pour aller au Web site francais.<BR><BR>
	      Recepcion. Haga clic <a href="esStart.asp">aqui</a> para ir al Web site espanol.<BR><BR>
	      [Chinese characters with a link]<BR><BR>
	      [Chinese - Taiwan characters with a link]<BR><BR>
	      <%
	
	  End Select
	
	  %></PRE>
	  <P>--- En-usStart.asp ---</P>
	
	  <PRE><%@ Language="VBScript" %>
	  <% Response.Redirect "enStart.asp" %></PRE>
	
	  <P>--- EnStart.asp ---</P>
	
	  <PRE><%@ CodePage=1252 Language="VBScript"%>
	
	  <% 
	  ' enStart.asp
	  ' This file is saved in ANSI format on US English system locale.
	  ' The language of the system doesn't matter
	  '  because you are setting @CodePage and Response.CodePage.
	  ' Otherwise, the system codepage of the server would be the default.
	
	  Response.CodePage = 1252
	  Response.CharSet = "windows-1252" 
	
	  Response.Write "<H1 align=center>News for Today</H1>"
	  %>
	
	  You can insert more content here, possibly using the <BR>
	  IIS Content Linking component, the <BR>
	  IIS Content Rotator component, or the <BR>
	  IIS Ad Rotator component.<BR></PRE>
	
	  <P><B>Applies To</B></P>
	
	  <P><A HREF="vbob5sj8.htm"><B>Response</B> Object</A></P>
	
	  <P><B>See Also</B></P>
	
	  <P><A HREF="vbob7fw4.htm"><B>Charset</B></A>, <A HREF="eadg4o37.htm">Accommodating International Clients</A></P>
	  <!-- Info Task Footer -->
	  <DIV CLASS="itfBorder"><IMG SRC="tiny.gif" WIDTH="1" HEIGHT="1"></DIV>
	  <DIV CLASS="itf"><B>Platform SDK Release: <FONT COLOR="#ddaa00">January 2002</FONT></B>
	  <TABLE CELLPADDING="0" CELLSPACING="0"><TR><TD WIDTH="43%">
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com"><IMG SRC="sendfdbk.gif" BORDER="0"/></A>&#xa0; 
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com">Contact Platform SDK</A></TD>
	  <TD><A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" TITLE="Order a CD online.">
	  <IMG SRC="download.gif" BORDER="0"/></A>&#xa0;
	  <A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" 
	  TITLE="Order a CD online.">Order a Platform SDK CD Online</A></TD></TR></TABLE></DIV>
	  <P>&#xa0;</P>
	  </BODY>
	  </HTML>
	
	Page 3: Response Object:
	
	- Page: Response Object
	
	- Link: LCID
	
	- Directory and file name: Winnt/Help/Iishelp/Iis/Htm/Asp/Vbob055w.htm
	
	Paste the following code in Notepad, name the file Vbob055w.htm, and then save
	the file in the Winnt/Help/Iishelp/Iis/Htm/Asp directory:
	
	  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
	  <HTML DIR="LTR"><HEAD>
	  <META HTTP-EQUIV="Content-Type" Content="text/html; charset=Windows-1252">
	  <TITLE>LCID</TITLE>
	  <style>@import url(coua.css);</style>
	  <link disabled rel="stylesheet" href="cocss.css"><META NAME="DESCRIPTION" CONTENT="Internet Information Services reference information">
	  </HEAD>
	  <body topmargin=0 id="bodyID">
	
	  <TABLE CLASS="buttonbarshade" CELLSPACING=0><a name="top"></a><TR><TD>&#xa0;</TD></TR></TABLE>
	  <TABLE CLASS="buttonbartable" CELLSPACING=0>
	  <TR ID="hdr"><TD CLASS="runninghead">Platform&#xa0;SDK:&#xa0;Internet&#xa0;Information&#xa0;Services&nbsp5.1</TD></TR>
	  </TABLE>
	
	  <H1><A NAME="_response_lcid"></A>LCID</H1>
	
	  <P>The <B>LCID</B> property specifies how dates, times, and currencies are formatted. LCIDs are not the same for each geographical 
	  locale. Some locales format dates as YY-MM-DD and some format dates as MM-DD-YYYY. The <B>LCID</B> property is read/write.</P>
	
	  <P><B>Syntax</B></P>
	
	  <PRE class="syntax"><B>Response.lcid </B>[<B>=</B> <I>LocaleID </I>]
	  </PRE>
	
	  <P><B>Parameters</B>
	
	  <DL>
	  <DT><I>LocaleID</I></DT>
	  </DL>
	
	  <P>An integer representing the geographical locale. You can find locale integers at <a href="http://go.microsoft.com/fwlink/?LinkId=1754" 
	  target=_blank><b>MSDN Library</b></a>.</P>
	
	  <P><B>Notes</B></P>
	
	  <P>Setting Response.LCID explicitly affects a single page, where Session.LCID affects all responses in a session. </P>
	
	  <P>If Response.LCID is not explicitly set in a page, it is implicitly set by Session.LCID, if sessions are enabled. If sessions are 
	  not enabled, Response.LCID is set by @LCID, if @LCID is present in the page. If there is no @LCID in the page, Response.LCID is 
	  set by the AspLCID metabase property. If the AspLCID property is not set, or set to 0, Response.LCID is set by the default system 
	  locale.</P>
	
	  <P>Response.LCID can be set multiple times in one Web page and used to format data each time. Some locales need the matching 
	  codepage to be set to display characters properly. For example, to display dates and times in several locales on one page, the 
	  codepage must be set to UTF-8 (65001) to show all the characters.</P>
	
	  <P>If you set Response.LCID or Session.LCID explicitly, do so before displaying formatted output. Setting Response.LCID 
	  changes the locale for both the ASP application and the scripting engine.  Using the VBScript function <B>setLocale()</B> only 
	  changes the locale for the scripting engine.</P>
	
	  <P>If the locale of your Web page matches the system defaults of the Web client, you do not need to set a locale in your Web page. 
	  However, setting the value is recommended.</P>
	
	  <P>If the locale is set in a page, and the codepage is set to display the characters properly, then <B>Response.Charset</B> should 
	  also be set. The codepage value tells IIS how to encode the data when building the response, and the charset value tells the 
	  browser how to decode the data when displaying the response. The <I>CharsetName</I> of Response.Charset must match the 
	  codepage value, or mixed characters are displayed in the browser. Lists of <I>CharsetNames</I> and matching codepage values can 
	  be found at <a href="http://go.microsoft.com/fwlink/?LinkId=1756" target=_blank><b>MSDN Web Workshop</b></a> under the 
	  columns for Preferred Charset Label and FamilyCodePage.</P>
	
	  <P>If you are writing and testing Web pages that use different locales, codepages, and character sets (for example, creating 
	  a multi-lingual Web site), remember that your test client computer must have the language packs installed for each language 
	  you wish to display. You can install language packs from Regional Options in the Control Panel.</P>
	
	  <P><B>Example</B></P>
	
	  <P>The following example displays the date, time, an amount of money, and a decimal value in different locales. The codepage is set to 
	  UTF-8 to display all the characters properly.</P>
	
	  <P>--- Response_LCID.asp ---</P>
	
	  <PRE><%
	  ' This file does not need @LCID or @CODEPAGE and
	  '  it does not need to be saved in UTF-8 format because 
	  '  there are no literal strings that need formatting or encoding.
	
	  Response.Codepage = 65001
	  Response.Charset = "utf-8"
	
	  ' See what happens when you uncomment the lines below.
	  'Response.Codepage = 1252
	  'Response.Charset = "windows-1252"
	
	  ShowDateTimeCurrency 1033, "North America"
	  ShowDateTimeCurrency 1041, "Japan"
	  ShowDateTimeCurrency 1049, "Russia"
	  ShowDateTimeCurrency 1031, "Germany"
	  ShowDateTimeCurrency 1025, "Saudi Arabia"
	  ShowDateTimeCurrency 1081, "India"
	  ShowDateTimeCurrency 2052, "China"
	  ShowDateTimeCurrency 1042, "Korea"
	
	  Sub ShowDateTimeCurrency(iLCID, sLocale)
	    Response.LCID = iLCID
	    Response.Write "<B>" & sLocale & "</B><BR>"
	    Response.Write FormatDateTime(Date, 1) & "<BR>"
	    Response.Write FormatDateTime(Time, 3) & "<BR>"
	    Response.Write FormatCurrency(1000) & "<BR>"
	    Response.Write FormatNumber(50, 3, 0, 0, -1) & " & " & FormatNumber(.02, 3, 0, 0, -1) & "<BR><BR>"
	  End Sub
	  %>
	  </PRE>
	
	  <P><B>Applies To</B></P>
	
	  <P><A HREF="vbob5sj8.htm"><B>Response</B> Object</A></P>
	
	  <P><B>See Also</B></P>
	
	  <P><A HREF="vbob7fw4.htm"><B>Charset</B></A>, <A HREF="vbob150l.htm"><B>CodePage</B></A>, <A HREF="eadg4o37.htm">Accommodating International Clients</A></P>
	  <!-- Info Task Footer -->
	  <DIV CLASS="itfBorder"><IMG SRC="tiny.gif" WIDTH="1" HEIGHT="1"></DIV>
	  <DIV CLASS="itf"><B>Platform SDK Release: <FONT COLOR="#ddaa00">January 2002</FONT></B>
	  <TABLE CELLPADDING="0" CELLSPACING="0"><TR><TD WIDTH="43%">
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com"><IMG SRC="sendfdbk.gif" BORDER="0"/></A>&#xa0; 
	  <A HREF="mailto:sdkfdbk@microsoft.com?subject=TITLE:%20The%20COM%20Library;%20RELEASE:%20June%202001;%20URL:%20com_1fuh.htm" 
	  Title="Send feedback to the Platform SDK team at sdkfdbk@microsoft.com">Contact Platform SDK</A></TD>
	  <TD><A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" TITLE="Order a CD online.">
	  <IMG SRC="download.gif" BORDER="0"/></A>&#xa0;
	  <A HREF="http://developerstore.com/devstore/toolboxselect.asp" TARGET="_blank" 
	  TITLE="Order a CD online.">Order a Platform SDK CD Online</A></TD></TR></TABLE></DIV>
	  <P>&#xa0;</P>
	  </BODY>
	  </HTML>
	
	Page 4: ASP Tutorial:
	
	- Page: ASP Tutorial
	
	- Link: IIS snap-in
	
	- Directory and file name: Winnt/Help/Iishelp/Iis/Htm/Asp/Iisbuti.htm
	
	Paste the following code in Notepad, name the file Iisbuti.htm, and then save the
	file in the Winnt/Help/Iishelp/Iis/Htm/Asp directory:
	
	  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
	  <html xmlns:IIS>
	  <head>
	  <title>IIS snap-in</title>
	  <script type="text/javascript" language="Javascript" src="iisAuthor.js">
	  </script>
	  <link type="text/css" rel="stylesheet" href="iisAuthor.css">
	
	  <meta  name="description" content="Conceptual information on the Internet Information Services snap-in utilities used to administer your server.">
	
	  <style title="FPRevisionMarks">
	  <!--
	  	.FPRevisionDel {color: red; text-decoration: line-through;}
	  	.FPRevisionIns {color: red; text-decoration: underline;}
	  	.FPRevisionDelHighlight {color: white; text-decoration: line-through; background: black;}
	  	.FPRevisionInsHighlight {color: white; text-decoration: underline; background: black;}
	  	.FPRevisionImgDel {border: 4px dashed #FF0000;}
	  	.FPRevisionImgDelHighlight {border: 8px solid #000000;}
	  -->
	  </style>
	
	  </head>
	  <body>
	  <h1><a name="Options">IIS Snap-in</a></h1>
	
	  <p>The Internet Information
	  Services (IIS) snap-in for the Microsoft Management Console (MMC) is a graphical 
	  interface for configuring your Web, FTP, SMTP, or NNTP sites. You can configure 
	  IIS security, performance, and reliability featues. You can add or delete sites; 
	  start, stop, and pause sites; backup and restore server configurations; and 
	  create virtual directories for better managing content, to name only a few of 
	  the administrative capabilities.&#xa0; In previous releases of IIS, this tool 
	  was called the Internet Service Manager. </p>
	
	  <p><b>To launch the IIS snap-in</b></p>
	  <p>From the <b>
	  Start</b> menu, click <b>Programs</b>, <b>Administrative Tools</b>, and then 
	  <b>Internet Information Services</b>. The IIS snap-in appears.</p>
	
	  <p> To launch the snap-in from the <b>Run</b> dialog box:</P>
	  <ol>
	  <li>From the <b>
	  Start</b> menu, click <b>Run</b>. The Run dialog box
	  appears.</li>
	
	  <li>In the <b>Open</b> text
	  box, type <b>inetmgr<span style="text-decoration: none">.</span></b></li>
	
	  <li>Press ENTER. The IIS snap-in appears.</li>
	  </ol>
	
	  <p>You can also access IIS
	  from the Computer Management Window. Accessing IIS in this way does
	  not give you the range of administration options offered by the IIS
	  snap-in; however, it does offer quick access and limited management
	  options for your Web sites. </p>
	  <ol>
	  <li>Click <b>
	  Start</b>, right-click <b>My Computer</b>, and click
	  <b>Manage</b> from the drop-down list. The <b>Computer
	  Management</b> window appears.</li>
	
	  <li>In the left pane, expand
	  the <b>Services and Applications</b> tree.</li>
	
	  <li>Click <b>Internet
	  Information Services</b>. The names and states of your Web sites
	  appear in the right pane. Expand the <b>Internet Information Services</b>
	  tree in the left pane and any subsequent Web site trees to see a
	  list of directories and virtual directories for that Web
	  page.</li>
	  </ol>
	
	  <p>For more information on using the IIS snap-in and administering IIS, see the 
	
	  <IIS:singlesource class="server">
	  <a href="sa_serveradmin.htm">Server Administration Guide</a></IIS:singlesource>.</p>
	
	  </body>
	  </html>
	
	Additional query words: iis, 5.1, online, documentation, xp
	
	======================================================================
	Keywords          : kbdocerr 
	Technology        : kbiisSearch kbiis510
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
