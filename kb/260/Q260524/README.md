---
layout: page
title: "Q260524: Error Message Running Exchange MAPI MA to Discover Mailbox"
permalink: /kb/260/Q260524/
---

## Q260524: Error Message Running Exchange MAPI MA to Discover Mailbox

{% raw %}

	Article: Q260524
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbtool
	Last Modified: 30-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services, version 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to import users by using the Microsoft Exchange MAPI management
	agent (MA), the following error message may be recorded in the operator's log:
	
	  Error 19086: DS_RC_PARENT_NOT_EXIST
	
	Each user that the MA attempts to import as a connector is not imported and
	causes error code 19086. By default, this process stops when more than a
	30-percent failure rate has occurred. This setting is configurable.
	
	CAUSE
	=====
	
	This issue can occur if you are trying to process users without processing sites
	and organizations first. When you import a user, the MA uses the distinguished
	name (DN) of the user and tries to import the user into a hierarchical structure
	in the connector space that include the container, site, and organization to
	which the user belongs in Exchange. If that parent structure has not been
	created, the connector creation does not succeed.
	
	RESOLUTION
	==========
	
	To resolve this issue, use either of the following methods:
	
	Method 1 (Preferred): Modify the Control Script to Add the -addparent Switch
	----------------------------------------------------------------------------
	
	1. In the Compass utility, select the management agent.
	
	2. On the Action panel, click Design MA.
	
	3. Under Control MA Operations, click the MA Control Script tab.
	
	4. Find the following text:
	
	  echo Synchronizing Metadirectory Users
	
	5. Add the -addparent switch to the end of the following line:
	
	  EXECUTE importt -objectClass "zcExchangeMailbox" -updateDib + -currentDn
	  "%dn%"
	
	When you are done, the line should look like:
	
	  EXECUTE importt -objectClass "zcExchangeMailbox" -updateDib + -currentDn
	  "%dn%" -addparent
	
	6. Click OK.
	
	7. Run the MA.
	
	Method 2: Enable the "Process Sites and Organizations" Option
	-------------------------------------------------------------
	
	1. In the Compass utility, select the management agent.
	
	2. On the Action panel, click Operate MA.
	
	3. Click to select the "Process Sites and Organizations" check box.
	
	4. Run the MA.
	
	MORE INFORMATION
	================
	
	Method 1 is preferred because when you enable the "Process Sites and
	Organizations" option, the MA processes and creates all containers created on
	the Exchange server. Often, this information is not necessary and creates
	additional unnecessary objects in the connector space and the metaverse. Using
	the -addparent switch is a more efficient way to bring users into the
	metadirectory. In addition, you should use the -addparent switch for hierarchy
	discovery because objects are returned from the DAPI query unordered. This can
	cause errors during hierarchy discovery.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kberrmsg kbtool 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
