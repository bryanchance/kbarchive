---
layout: page
title: "Q190480: PRB: SET(&quot;Century&quot;,1) Not Reporting Correct Century"
permalink: /kb/190/Q190480/
---

## Q190480: PRB: SET(&quot;Century&quot;,1) Not Reporting Correct Century

{% raw %}

	Article: Q190480
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbYear2000 kbvfp600 kbXBase kbGrpDSFox
	Last Modified: 09-JUN-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the system clock of the computer is set to a year between 2000 and 2049,
	inclusive, and the SET CENTURY TO command is issued without any additional
	arguments, the SET("Century",1) command returns 19 instead of the expected 20.
	
	RESOLUTION
	==========
	
	The following code can be used as a workaround to the SET("Century",1) command
	to return the century of the current date after a SET CENTURY TO command has
	been issued:
	
	  ROUND(VAL(LEFT(ALLTRIM(STR(YEAR(DATE()))),2)),0)
	
	Note that the SET("Century",1) command returns a numeric value. The ROUND() and
	VAL() functions have been used in the preceding code to convert the result of
	the LEFT() function to a numeric value with no decimal places. These two
	functions can be eliminated if it is acceptable for the century to be a
	character value.
	
	Alternately, the following line of code can be used in place of the SET CENTURY
	TO command to set the century to the current system clock century and set the
	ROLLOVER values back to their defaults based on the system clock:
	
	  SET CENTURY TO INT(YEAR(DATE())/100) ROLLOVER
	  MOD(YEAR(DATE())+50,100)
	
	NOTE: Prior to using this code, please refer to the MORE INFORMATION section
	below to make sure this is the behavior you want.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The Visual FoxPro Online Help file for the SET CENTURY command states the
	following:
	
	  Issue SET CENTURY TO without any additional arguments to restore the
	  default century to the current century and ROLLOVER to the default value
	  of the current year plus 50 years.
	
	Therefore, if the computer's system clock is set to a year in the 2000 range, it
	would appear that the SET("Century",1) function that returns the century should
	return 20. For years between 2000 and 2049, inclusive, it returns 19.
	
	Once the year 2000 is reached, the rollover keyword of the SET CENTURY TO command
	can be thought of as "rollback" as far as the century is concerned. When the
	computer's clock is set to a year in the twentieth century, such as 1998, the
	default rollover is the current year plus 50. Therefore, the rollover in 1998 is
	48. This allows ambiguous dates entered with year digits of 48 through 99
	inclusive assumed to be in the twentieth century - 1948 through 1999. Ambiguous
	dates entered with year digits of 00 through 47 are assumed by Visual FoxPro to
	be in the twenty-first century.
	
	When the computer's system clock is set to a year in the twenty-first century
	prior to 2050, such as 2001, the results are the same. The default rollover of
	the current year plus 50 produces a rollover of 51. There's only three years
	difference between the rollover referred to in the preceding section and when
	the system clock was in the twentieth century. Now ambiguous dates entered with
	year digits from 00 through 50 inclusive are still assumed to be in the
	twenty-first century while ambiguous dates with year digits from 51 to 99 are
	still assumed to be in the twentieth century. If the Century was set to 20 with
	a rollover of 50, the dates with years of 00 through 50 would have been assumed
	to be in the twenty-second century.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Close everything except Visual FoxPro. Failure to do so could cause
	  unexpected behavior in other programs.
	
	2. In the Control Panel dialog box, select Date/Time and set the system clock to
	  a year between 2000 and 2049, inclusive, and then click Apply.
	
	3. Start Visual FoxPro 6.0.
	
	4. In the Visual FoxPro Command window, issue the following commands:
	
	  SET CENTURY ON
	  ? DATE()             && Returns the current date, note the year.
	  SET CENTURY TO
	  ? SET("Century",1)   && Note that this returns 19.
	  ? SET("Century",2)   && This reports the Rollover value.
	
	
	REFERENCES
	==========
	
	Visual FoxPro Help, version 6.0; search on: "SET CENTURY"; topic: "Set Century"
	
	Visual FoxPro Help, version 6.0; search on: "SET()"; topic "SET()"
	
	Additional query words:
	
	======================================================================
	Keywords          : kbYear2000 kbvfp600 kbXBase kbGrpDSFox 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
