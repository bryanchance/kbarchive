---
layout: page
title: "Q185377: Users Cannot Access FTP or Web Site"
permalink: /kb/185/Q185377/
---

## Q185377: Users Cannot Access FTP or Web Site

{% raw %}

	Article: Q185377
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Users cannot open an FTP or Web site.
	
	NOTE: A sampling of specific error messages you may receive is listed in the
	"MORE INFORMATION" section of this article.
	
	CAUSE
	=====
	
	User rights in the Windows NT User Manager or the Internet Service Manager (ISM)
	are not set up properly.
	
	WORKAROUND
	==========
	
	The information in this "Workaround" section about troubleshooting User Rights,
	Anonymous Authentication, and Basic Authentication was taken from the Windows NT
	Option Pack online Product Documentation.
	
	NOTE: To view this entire topic, open the following in the product
	documentation's table of contents:
	
	- Microsoft Internet Information Server
	
	- IIS Installation
	
	- Troubleshooting
	
	User Rights
	-----------
	
	If a user is having trouble viewing your published files (that is, he or she is
	receiving HTTP "403; Forbidden" or similar HTTP errors when attempting to
	request a Web page), then there is most likely a problem related to the user
	rights that are configured on your Web site. In order to give users access to
	your published files, check the following items.
	
	1. Find the specific file, directory, or virtual directory which the user cannot
	  access in Internet Service Manager.
	
	2. View the properties for that file, directory, or virtual directory.
	
	3. Select the File property sheet (if viewing properties of a file) or Directory
	  property sheet (if viewing the properties of a directory or virtual
	  directory). Ensure that the directory or file has Read access permissions
	  (the Read check box should be selected).
	
	4. Select the File Security or Directory Security property sheet.
	
	5. Ensure that the user has either anonymous access, basic authentication
	  permissions, or Windows NT Challenge/Response permissions that will allow him
	  or her to view the content by clicking the Edit button in the Anonymous
	  Access and Authentication Control field.
	
	6. Click the Edit button in the TCP/IP and Domain Name Restrictions field to
	  ensure that the client's computer, group of computers, or domain name has not
	  been restricted from accessing your resource.
	
	Anonymous Authentication
	------------------------
	
	If an anonymous user cannot access your site, check the following.
	
	Ensure that the anonymous user's password is the same in both Internet Service
	Manager and User Manager:
	
	1. In ISM, select the Web site, virtual directory, directory, or file on which
	  you need to check anonymous access and view its properties.
	
	2. Select the File Security property sheet (if viewing properties of a file) or
	  Directory Security property sheet (if viewing properties of a Web site,
	  virtual directory, or directory) and click the Edit button in the Anonymous
	  Access and Authentication Control field.
	
	3. In the Authentication Methods dialog box, make sure that the Allow Anonymous
	  Access check box is selected.
	
	4. Click the Edit button to view the user name and password that are used when
	  an anonymous user connects to your site. In order to enable your Web site to
	  automatically synchronize your anonymous password settings with those set in
	  Windows NT, select the Enable Automatic Password Sychronization check box (it
	  is selected by default for all resources that allow anonymous access).
	
	Ensure that the anonymous user has Log on locally rights in Windows NT User
	Manager for Domains:
	
	1. Launch User Manager from the Microsoft Management Console (MMC) toolbar.
	
	2. In User Manager, select User Rights in the Policies menu.
	
	3. Choose the right Log On Locally and make sure IUSR_ (or your anonymous
	  account) shows up in the list.
	
	If you are having trouble PREVENTING an anonymous user from accessing your site,
	please check the following:
	
	1. Select the File Security property sheet (if viewing properties of a file) or
	  Directory Security property sheet (if viewing properties of a Web site,
	  virtual directory, or directory) and click the Edit button in the Anonymous
	  Access and Authentication Control field.
	
	2. In the Authentication Methods dialog box, make sure that the Allow Anonymous
	  Access check box is not selected.
	
	Basic Authentication
	--------------------
	
	If users with Basic Authentication rights are having trouble accessing your site,
	please check the following.
	
	Ensure that the login user has Log on locally rights in Windows NT User Manager
	for Domains:
	
	1. Launch User Manager from the Microsoft Management Console (MMC) toolbar.
	
	2. In User Manager, select User Rights in the Policies menu.
	
	3. Choose the right Log On Locally and make sure IUSR_ (or your anonymous
	  account) shows up in the list.
	
	Make sure that you specify a Default Logon Domain for the user: in the
	Authentication Methods dialog box, click Edit in the Basic Authentication field
	and enter the Domain Name.
	
	If you are concerned about the safety of transmitting passwords in clear text (an
	industry standard that applies to Basic Authentication), use Secure Sockets
	Layer (SSL) to secure clear text passwords. You can configure SSL Client
	authentication by launching the Secure Communications dialog box from the
	Directory Security (or File Security) property sheet. Use Key Manager to create
	Key requests and the Secure Communications dialog box to enable an SSL
	Authentication scheme.
	
	MORE INFORMATION
	================
	
	Default Anonymous User Account
	------------------------------
	
	During installation of IIS, the anonymous user account is set to
	IUSR_<computername> by default.
	
	Sampling of Specific Error Messages
	-----------------------------------
	
	The following is a list of some of the errors generated by Internet Explorer,
	Netscape Navigator, or the Windows NT FTP utility when a site cannot be opened:
	
	  HTTP "403; Forbidden
	
	  HTTP Error 401
	  401.1 Unauthorized: Logon Failed
	
	  This error indicates that the credentials passed to the server do not match
	  the credentials required to log on to the server.
	
	  Please contact the Web server's administrator to verify that you have
	  permission to access the requested resource.
	
	  Internet Explorer cannot open the Internet site
	  ftp://<domain_name>.
	
	  The login request was denied
	
	  530 User Anonymous cannot log in.
	
	  Login failed.
	
	  User mozilla@ cannot log in.
	
	More Information in Product Documentation
	-----------------------------------------
	
	For more information about anonymous access, open the following in the Product
	Documentation's table of contents:
	
	- Microsoft Internet Information
	
	- Server Administration
	
	- Security
	
	- Access Control
	
	- Configuring the Anonymous Access Account
	
	For more information about basic authentication, open the following:
	
	- Microsoft Internet Information
	
	- Server Administration
	
	- Security
	
	- Authentication
	
	- Enabling Basic Authentication
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Kevin
	Zollman, Microsoft Corporation.
	
	
	Additional query words: Access Control List ACL IUSR_<machinename> IUSR_<machine_name> IUSR_<computer_name> denied ie privileges logon locally akz
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
