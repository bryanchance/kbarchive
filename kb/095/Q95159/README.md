---
layout: page
title: "Q95159: TrueType Font Pack 2 - Font Assistant's Database"
permalink: /kb/095/Q95159/
---

## Q95159: TrueType Font Pack 2 - Font Assistant's Database

{% raw %}

	Article: Q95159
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): 3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-SEP-2001
	
	3.10 3.11
	WINDOWS
	kbusage
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft TrueType Font Pack 2 for Windows 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Font Assistant manages all TrueType fonts on the system. To do this, it creates
	the FAST.INI file in the Windows directory (usually C:\WINDOWS). When the Font
	Assistant loads, it indicates that it is "Reading font database..."; FAST.INI is
	the font database. FAST.INI consists of three sections: [FONTS], [GROUPS], and
	[PREF].
	
	MORE INFORMATION
	================
	
	[FONTS] Section
	===============
	
	The [FONTS] section consists of two types of entries: Count and Fn.
	
	Count      = The number of TrueType fonts that are on the system,
	            starting from 0.
	
	Fn         = Font information for each font on the system, with the
	            first font that is loaded given a starting number of F0.
	
	Example
	-------
	
	[Fonts]
	count=2
	F0="Arial", "Arial", C:\WIN31\SYSTEM\ARIAL.FOT, 02110604020202020204,
	0001000000000000, 00bf  , 00000000  , 01900040
	F1="Courier New","Courier
	New",C:\WIN31\SYSTEM\COUR.FOT,02070309020205020404,80c9000000000000,0
	bf,00000000,01900040
	
	Explanation
	-----------
	
	Fn=name, logname, FOTpath, ajPANOSE, awGroup[4], wFlags,
	dwFileSize,wWt:wSeln
	
	Fn         = The order in the list in which the font was loaded.
	
	name       = The name that the TrueType font uses in the font menus.
	
	logname    = The TrueType font group that the font is a member of. For
	            example, all Arial fonts (Arial, Arial Bold, Arial
	            Narrow, Arial Narrow Bold) will show as Arial.
	
	FOTpath    = Path to the .FOT file.
	
	ajPANOSE   = 10 2-digit decimal numbers that represent the 10-digit
	            hexidecimal PANOSE ID number. For example, the TrueType
	            font Arial has the PANOSE ID number
	
	               02110604020202020204
	
	            which is read by the Font Assistant as:
	
	               2B64222224
	
	awGroup    = Which group(s) that the font belongs to.
	
	wFlags     = This is a number that Font Assistant uses to see if:
	
	            1. The font was found in WIN.INI during a resync.
	            2. The font is active.
	            3. The font record is dirty and needs to be rewritten.
	            4. It has found a PANOSE ID number in the TrueType file.
	            5. The record contains a valid PANOSE number.
	            6. The font can be embedded.
	            7. The font can be edited.
	            8. The font can be installed.
	       9. The font supports a particular type of embedding.
	               Normally the embedding type is none, print, or preview.
	
	dwFileSize = The size of the TrueType file. Not currently used.
	
	
	wWt        = The weight of the font; bold, thin, and so on.
	
	wSel n     = Selection from TrueType OS/2 table.
	
	[GROUPS] Section
	================
	
	The [GROUPS] section consists of two types of entries, Count and Gn,
	where "n" equals the group number.
	
	Example
	-------
	
	[Groups]
	Count=2
	G0= "<all font>",    00,     1d,     03
	G1="New Group 1",    01,      3,     03
	
	Explanation
	-----------
	
	Gn=name,wGRNUM, WFonts, wFlags
	
	name       = Group name.
	
	wGRNUM     = When the group was created in relationship with the other
	            groups.
	
	wFonts     = The number of fonts in the group.
	
	wFlags     = Tests to see if the group is active or inactive.
	
	[PREF] Section
	=============
	
	The [PREF] section consists of eleven types of entries.
	
	Example
	-------
	
	[PREF]
	Scale=0
	Show Sample=1
	Sample Size=18
	Sort By=0
	Show Fonts As=1
	PANOSE Sort Name=
	Sample=PANOSE A B C D E F G H I J K L M N O P Q R S T U V W X Y Z  a
	b c d e f g h i j k l m n o p q r s t u v w x y z 1 2 3 4 5 6 7 8 9 0
	! ? . , ; : @ # $ % ^ & * ( ) { } [ ] < >
	Left=101
	Top=122
	Right=698
	Bottom=477
	
	Explanation
	-----------
	
	Scale      = If Scale is 0, Font Assistant verifies that a matching
	            .FOT file is available for each font. If it is not 0,
	            Font Assistant assumes that every font has a matching
	            .FOT file and doesn't perform the search.
	
	Show Sample= If Show Sample is 0, the Sample Window is off. If it is
	            not 0, the Sample Window is on.
	
	Sample Size= The point size of the fonts that are displayed in the
	            Sample window.
	
	Sort By    = 0 = Sort by name.
	            1 = Sort by family*.
	            2 = Sort by serif.
	            3 = Sort by weight*.
	            4 = Sort by width.
	            5 = Sort by contrast*.
	            6 = Sort by X-height*.
	            7 = Sort by PANOSE ID number.
	            8 = Sort by ability to be embedded.
	
	            * These numbers can be set by editing the FAST.INI file.
	
	Show Font
	As         = If Show Font As is 0, only the active fonts are listed.
	            If it is not 0, all the fonts are listed. To change
	            this number, you need to edit the FAST.INI file.
	
	Left       = Windows coordinates when Font Assistant was last shut down.
	
	Top        = Windows coordinates when Font Assistant was last shut down.
	
	Right      = Windows coordinates when Font Assistant was last shut down.
	
	Bottom     = Windows coordinates when Font Assistant was last shut down.
	
	PANOSE
	Sort Name = This name is used to sort the fonts by similarity, if the
	           last sort was a PANOSE sort.
	
	Sample    = Text of editable Sample window. Carriage return/linefeed is
	           encoded as "\377\377". Use this code to fit multiple sample
	           lines on the "Sample=" line.
	
	Additional query words: 3.10 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311 kbTTFontSearch
	Version           : :3.1,3.11
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
