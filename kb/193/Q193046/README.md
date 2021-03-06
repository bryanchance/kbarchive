---
layout: page
title: "Q193046: Err Msg: Couldn't Find the Microsoft Expedia Streets 98 CD-ROM"
permalink: /kb/193/Q193046/
---

## Q193046: Err Msg: Couldn't Find the Microsoft Expedia Streets 98 CD-ROM

{% raw %}

	Article: Q193046
	Product(s): Microsoft Automap
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kb3rdparty kbenv kberrmsg kbhw kbimu kbHardwarekbfaq
	Last Modified: 25-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets 98 
	- Microsoft Expedia Trip Planner 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Expedia Streets 98 or Expedia Trip Planner 98, you may
	receive an error message similar to the following
	
	  Couldn't find the Microsoft Expedia Streets 98 CD-ROM in drive <drive>.
	  Ensure that the CD is correctly inserted in your <drive> drive, then
	  click OK (or click Cancel to exit the application).
	
	where <drive> is the letter of the CD-ROM drive containing the Expedia
	Streets 98 CD-ROM.
	
	NOTE: If you attempt to start Expedia Trip Planner 98, you receive the identical
	error message with the substitution of Trip Planner for Streets in the error
	message.
	
	CAUSE
	=====
	
	This behavior can occur if the motherboard installed in your computer is based
	on the VIA VP3 chipset. A list of computer manufacturers that use motherboards
	based on the VIA VP3 chipset is available on the following VIA Web site:
	
	  http://www.via.com.tw/support/partnersvp3.htm
	
	RESOLUTION
	==========
	
	To resolve this issue, install Microsoft Windows 98, or download and install the
	latest version of the VIA IDE Busmaster driver from the following VIA Web site:
	
	  http://www.via.com.tw/drivers/index.htm
	
	If your motherboard is based on the AGP version of the VP3 chipset, download and
	install the latest AGP driver from this Web site.
	
	NOTE: Do not install the VIA IDE Busmaster driver unless you know that your
	computer uses a VIA VP3 chipset. Contact your computer manufacturer for more
	information.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information about this issue, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q158274 Automap Err Msg: Couldn't Find Streets Plus/Trip Planner CD-ROM
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	Additional query words: multi multi-media media mm automap amap
	
	======================================================================
	Keywords          : kb3rdparty kbenv kberrmsg kbhw kbimu kbHardware kbfaq
	Technology        : kbHomeProdSearch kbExpediaSearch
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
