---
layout: page
title: "Q192050: BUG: Resource Leak with 256 Color Bitmap/UseZOrder PaletteMode"
permalink: /kb/192/Q192050/
---

## Q192050: BUG: Resource Leak with 256 Color Bitmap/UseZOrder PaletteMode

{% raw %}

	Article: Q192050
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbBitmap kbVBp kbVBp600bug kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may see a loss of System and GDI resources when repeatedly loading a picture
	if the Form's PaletteMode is set to UseZOrder and the Windows system display
	color settings are set to 256 colors. Because of the differences in the way that
	Windows 95/98 and Window NT manage memory, the consequences of this problem may
	be more apparent on a computer running Windows 95/98 than on a computer running
	Windows NT/2000.
	
	RESOLUTION
	==========
	
	Set the PaletteMode property of the form to a setting other than UseZOrder.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	These steps require that you have a 256 color bitmap. If you have a bitmap you
	would like to use, substitute it for "C:\test.bmp" in step 5. If not, create a 2
	x 2 inch bitmap using Paint or other software capable of creating a bitmap.
	
	1. On a machine running Windows 95/98, set the Windows display system color
	  setting to 256 colors.
	
	2. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	3. Add a CommandButton and an Image control to Form1.
	
	4. Set the PaletteMode property of Form1 to UseZOrder.
	
	5. Add the following code to the module of Form1:
	
	        Private Sub Command1_Click()
	        Dim b As Boolean
	        Dim i As Integer
	
	        For i = 1 To 500
	           Caption = Str(i)
	           b = Not b
	           If b Then
	              Image1.Picture = LoadPicture("c:\test.bmp")
	           Else
	              Image1.Picture = LoadPicture("")
	           End If
	        Next i
	        End Sub
	
	6. From the File menu, choose Make Project1.exe.
	
	7. Save the project and close Visual Basic.
	
	8. Start the Windows Resource Meter, and display the Resource Meter window by
	  right-clicking on the icon in the TaskBar, and selecting Details.
	
	9. Run Project1.exe and click on the CommandButton. You should see the System
	  and GDI resources decreasing. These resources are not reclaimed until you
	  exit Project1.exe.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbBitmap kbVBp kbVBp600bug kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
