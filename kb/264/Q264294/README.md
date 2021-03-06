---
layout: page
title: "Q264294: Streets and Trips 2001: Information That You Need to Import Data"
permalink: /kb/264/Q264294/
---

## Q264294: Streets and Trips 2001: Information That You Need to Import Data

{% raw %}

	Article: Q264294
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbtool kbimu
	Last Modified: 12-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MapPoint 2002 
	- Microsoft MapPoint 2001 
	- Microsoft Streets & Trips 2002, version 1.0 
	- Microsoft Streets and Trips 2001 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the information that you need to use the Import Data
	Wizard in Microsoft Streets and Trips 2001 or Microsoft MapPoint 2001.
	
	MORE INFORMATION
	================
	
	The Import Data Wizard requires the source file to contain the following
	information to place records on a map:
	
	- Location information
	- Data fields
	
	When you use the Import Data Wizard to import addresses in Microsoft Streets and
	Trips 2001 or Microsoft MapPoint 2001, the program examines your source file for
	the information it needs to place your records on the map.
	
	Location Information
	--------------------
	
	Streets and Trips 2001 or MapPoint 2001 uses location information to match your
	records to a location on the map. Streets and Trips 2001 or MapPoint 2001
	attempts to assign column names based on the contents of your data.
	
	For example, the following column headings are used to identify a geographic
	location:
	
	- Address
	- City
	- Country
	- County
	- Latitude
	- Longitude
	- Province
	- State
	- ZIP or Postal Code
	
	NOTE: You must use one of the headings provided in the Import Data Wizard for any
	column in your data that contains location information, and you must confirm
	that the heading for the column accurately corresponds to the contents of that
	column.
	
	Data Fields
	-----------
	
	Data fields contain all types of data other than location information. The
	information in data fields is displayed in pushpin balloons.
	
	The columns available for data fields are:
	
	- Name: Data in this column is displayed in the Name field of the pushpin
	  balloon.
	
	- Name2: Data in this column is combined with the data in the Name column and
	  is displayed in the Name field of the pushpin balloon.
	
	- Information: Data in this column is displayed in the Note field of the
	  pushpin balloon. You can include any information in this field, including
	  hyperlinks.
	
	NOTE: If your data source does not contain the Name or Name2 column heading, the
	Name field in the pushpin balloon uses the location information that was used to
	match the record to the map.
	
	How to Select or Change Column Headings
	---------------------------------------
	
	To select or change column headings:
	
	1. If you import data from a text file or from Microsoft Excel, and the first
	  row of your file does not include column headings, click to clear the "First
	  row contains column headings" check box.
	
	2. In the Country/Region box, click the correct country for your data.
	
	  If your data contains records from more than one country, click Multi/Other,
	  and make sure that the Country heading is matched to the column that contains
	  the country names.
	
	3. At the top of each column, type or select a descriptive heading as necessary.
	  If you do not want to make the data in this column available on the map,
	  click Skip Column.
	
	  NOTE: You cannot use the same descriptive heading in more than one column.
	
	4. Make sure that the following information is correct:
	
	   - The column names.
	
	   - The results message, which indicates that your data is mapped according to
	     the type of geographic feature that you want.
	
	5. Repeat steps 2 through 4 for each column.
	
	Additional query words: mp2001 map point st2001 importing push pin located position header
	
	======================================================================
	Keywords          : kbtool kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbExpediaSearch kbMapptSearch kbMapPoint2001 kbExpediaStreets2001 kbExpediaStreets2002 kbMapPoint2002
	Version           : :1.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
