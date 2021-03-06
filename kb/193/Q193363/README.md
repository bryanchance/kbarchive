---
layout: page
title: "Q193363: BUG: DDE Paste Link with Word Fails to Update Using LinkSend"
permalink: /kb/193/Q193363/
---

## Q193363: BUG: DDE Paste Link with Word Fails to Update Using LinkSend

{% raw %}

	Article: Q193363
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0,97
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use DDE (Dynamic Data Exchange) to create a Paste link between a Visual
	Basic Picture Box and a Word document when using the LinkSend method, the Word
	document will only update with the first LinkSend method call. Subsequent
	LinkSend calls will not update the pasted link within the Word document.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Change the Application Title in the Project Properties dialog to "DDEDEMO."
	
	3. Add three CommandButtons and a PictureBox to Form1 with the following
	  properties:
	
	  Control             Name              Caption
	  ------------------------------------------------
	
	  CommandButton1     cmdClose           CLOSE
	  CommandButton2     cmdCopy            COPY
	  CommandButton3     cmdPlot            NEW TRACE
	  PictureBox1        picGraph
	
	4. Change the LinkMode Property of Form1 to "1-Source."
	
	5. Paste the following code in Form1:
	
	        Option Explicit
	
	        Const CF_LINK = &HBF00
	        Const CF_TEXT = 1
	        Const CF_BITMAP = 2
	        Const CF_METAFILE = 3
	        Const CF_DIB = 8
	        Const CF_PALETTE = 9
	
	        Const NONE = 0         ' 0 - None
	        Const LINK_SOURCE = 1    ' 1 - Source (forms only)
	
	        Dim Trace(0 To 100)  As Integer
	        Dim TraceColor As Integer
	
	        Private Sub cmdClose_Click()
	           Unload Me
	        End Sub
	
	        Private Sub cmdCopy_Click()
	           Form1.LinkMode = NONE
	           Form1.LinkTopic = "Main"
	           Form1.LinkMode = LINK_SOURCE
	           Clipboard.Clear
	           Clipboard.SetText "DDEDEMO|Main!picGraph", CF_LINK
	           Clipboard.SetData picGraph.Image, CF_BITMAP 'Image
	        End Sub
	
	        Private Sub cmdPlot_Click()
	           GenerateTrace
	           PlotTrace
	        End Sub
	
	        Private Sub Form_Load()
	           Form1.LinkMode = NONE
	           GenerateTrace
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	           End
	        End Sub
	
	        Private Sub GenerateTrace()
	           Dim I As Integer
	           For I = 0 To 100
	              Trace(I) = Int((100 - 0 + 1) * Rnd + 0)
	           Next I
	           TraceColor = Int((6 - 1 + 1) * Rnd + 1)
	        End Sub
	
	        Private Sub PlotTrace()
	           Dim I As Integer
	           Dim Y As Integer
	           Dim LastY As Integer
	           picGraph.Cls
	           picGraph.AutoRedraw = False
	           picGraph.AutoRedraw = True
	           picGraph.Scale (-10, 110)-(110, -10)
	           picGraph.DrawStyle = 0
	           picGraph.Line (0, 0)-(100, 100), , B
	           For I = 0 To 100 Step 10
	              picGraph.DrawStyle = 0
	              picGraph.Line (0, I)-(-2, I)
	              picGraph.Line (I, 0)-(I, -2)
	              picGraph.DrawStyle = 2
	              picGraph.Line (0, I)-(100, I)
	              picGraph.Line (I, 0)-(I, 100)
	           Next I
	           picGraph.DrawStyle = 0
	           For I = 1 To 100
	              picGraph.Line (I - 1, Trace(I - 1))-(I, Trace(I)), _
	              QBColor(TraceColor)
	           Next I
	           If Form1.LinkMode = 1 Then picGraph.LinkSend
	        End Sub
	
	6. Press the F5 key to run the program.
	
	7. Click COPY.
	
	8. Open an instance of Word.
	
	9. Select Paste Special from the Edit menu. In the Paste Special screen, select
	  Paste Link and Device Independent Bitmap. Note that the bitmap in the Visual
	  Basic program is copied to the Word document.
	
	10. Switch back to the running Visual Basic program. Click NEW TRACE a few
	  times. The bitmap in Word only changes the first time NEW TRACE is selected,
	  and subsequent updates fail to show up.
	
	  NOTE: In Visual Basic 4, the same situation fails on the first update with
	  the following error:
	
	  Error 293: DDE Method invoked with no channel open
	
	Additional query words: kbDSupport kbdss kbDDE kbVBp kbVBp500bug kbVBp600bug
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbWordSearch kbVBSearch kbAudDeveloper kbWord97 kbWord97Search kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0,97
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
