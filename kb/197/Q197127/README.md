---
layout: page
title: "Q197127: HOWTO: Add a Custom Font Property to a User Control"
permalink: /kb/197/Q197127/
---

## Q197127: HOWTO: Add a Custom Font Property to a User Control

{% raw %}

	Article: Q197127
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbCtrlCreate kbPropSheet kbGrpDSUser kbVBp500 kbVBp600
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you create a user control, you can add a custom property page that allows
	the user to set some or all of the properties you have created. This article
	describes a sample that demonstrates how to create a custom font property so
	that you can filter which fonts the user can select. It uses a custom property
	page from which you call the Font common dialog box so that it allows your users
	to select only from fixed pitch fonts.
	
	MORE INFORMATION
	================
	
	You can create the properties you want and then you can either set them directly
	from the Property Page dialog box, or you can load a form or call the
	CommonDialog from the property page to set them. In steps 1 through 12 of the
	following example, you can create a version that requires going through one
	additional screen, the property page, but otherwise works substantially like the
	built-in Font property of the intrinsic controls. The instructions beginning
	with step 13 add code that hides the property page so that the effect is more
	like the built-in Font property.
	
	Step-by-Step Procedures
	-----------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. From the Project menu, add a new UserControl Project. UserControl1 is created
	  by default.
	
	3. Add a TextBox and a Label to UserControl1.
	
	4. Paste the following code into the UserControl code window:
	
	        Option Explicit
	        Private UseFont As String
	        Private UseFontSize As Long
	
	        Public Property Let MyFont(NewFont As String)
	           Dim Ctrl As Control
	           UseFont = NewFont
	           PropertyChanged "MyFont"
	           On Error Resume Next   ' For Controls without a Font property
	           For Each Ctrl In Controls
	              Ctrl.Font.Name = NewFont
	           Next
	        End Property
	
	        Public Property Get MyFont() As String
	           MyFont = UseFont
	        End Property
	
	        Public Property Get MyFontSize() As Long
	           MyFontSize = UseFontSize
	        End Property
	
	        Private Property Let MyFontSize(NewValue As Long)
	           Dim Ctrl As Control
	           UseFontSize = NewValue
	           PropertyChanged "MyFontSize"
	           On Error Resume Next   ' For Controls without a Font property
	           For Each Ctrl In Controls
	              Ctrl.Font.Size = NewValue
	           Next
	        End Property
	
	5. From the Project menu, add a new Property Page.
	
	6. From the Project menu, click Components, click Microsoft Common Dialog
	  Control, and click OK.
	
	7. Add a CommonDialog, a CommandButton, and two TextBoxes (named txtMyFont and
	  txtMyFontSize) to the Property Page.
	
	8. Add the following code to the PropertyPage1 code window:
	
	        Option Explicit
	
	        Private Sub Command1_Click()
	           CommonDialog1.Flags = cdlCFBoth Or cdlCFFixedPitchOnly
	           CommonDialog1.FontName = SelectedControls(0).MyFont
	           CommonDialog1.FontSize = SelectedControls(0).MyFontSize
	           CommonDialog1.ShowFont
	           txtMyFont.Text = CommonDialog1.FontName
	           txtMyFontSize.Text = CommonDialog1.FontSize
	        End Sub
	
	        Private Sub txtMyFont_Change()
	           Changed = True
	        End Sub
	
	        Private Sub txtMyFontSize_Change()
	           Changed = True
	        End Sub
	
	        Private Sub PropertyPage_ApplyChanges()
	           SelectedControls(0).MyFont = txtMyFont.Text
	           SelectedControls(0).MyFontSize = txtMyFontSize.Text
	        End Sub
	
	        Private Sub PropertyPage_SelectionChanged()
	           If SelectedControls(0).MyFont = "" Then
	               txtMyFont.Text = "Courier"     ' Default
	           Else
	               txtMyFont.Text = SelectedControls(0).MyFont
	           End If
	           If SelectedControls(0).MyFontSize > 0 Then
	               txtMyFontSize.Text = SelectedControls(0).MyFontSize
	           Else
	               txtMyFontSize.Text = 8     ' Default
	           End If
	        End Sub
	
	9. Select the UserControl and click the PropertyPages property. Click the
	  ellipsis button ("..."), select PropertyPage1, and click OK. This associates
	  the Property Page you created with UserControl1.
	
	10. Click the UserControl to make sure it is selected. From the Tools menu,
	  click Procedure Attributes and select MyFont from the Name drop-down list.
	  Click Advanced and select PropertyPage1 from the list under Use this Page in
	  Property Browser:. This makes an ellipsis button ("...") appear when the
	  user selects the MyFont property.
	
	11. Close all design windows except for Form1. Add the UserControl to Form1.
	
	12. When the UserControl has the focus, you will see a MyFont property in the
	  Properties Window. Click MyFont to get the ellipsis button. Click the
	  ellipsis button to go to the property page. From here the CommandButton
	  brings up the filtered Font common dialog where you can choose your font. If
	  you click OK or Apply, you set these properties. To demonstrate that this
	  works, it also applies these settings to the TextBox and Label. You can also
	  get to this dialog box by right-clicking on the UserControl and clicking
	  Properties, or through the (Custom) property in the Properties Window.
	
	Follow the instructions below to skip the intermediate property page and go
	straight to the Font dialog from the ellipsis button. Note that you would only
	want to consider this feature if this were the only property you were setting
	through the property page.
	
	1. Using the previous example, add a timer to the property page and add the
	  following code to the top of the timer code window, just under Option
	  Explicit:
	
	        Private Declare Function GetParent Lib "user32" _
	          (ByVal hwnd As Long) As Long
	
	        Private Declare Function SetWindowPos Lib "user32" _
	          (ByVal hwnd As Long, ByVal hWndInsertAfter As Long, _
	          ByVal x As Long, ByVal y As Long, ByVal cx As Long, _
	          ByVal cy As Long, ByVal wFlags As Long) As Long
	
	        Private Declare Function PostMessage Lib "user32" Alias _
	          "PostMessageA" (ByVal hwnd As Long, ByVal wMsg As Long, _
	          ByVal wParam As Long, ByVal lParam As Long) As Long
	
	        Private Const HWND_TOP = 0
	        Private Const SWP_NOSIZE = &H1
	        Private Const SWP_HIDEWINDOW = &H80
	        Private Const WM_CLOSE = &H10
	
	        Dim hwndPP As Long
	
	        Private Sub PropertyPage_Paint()
	           Dim lresult As Long
	           lresult = GetParent(PropertyPage.hwnd)   ' Work back to the
	           hwndPP = GetParent(lresult)              ' dialog window.
	           lresult = SetWindowPos(hwndPP, HWND_TOP, 200&, 200&, &O0, &O0, _
	              SWP_HIDEWINDOW Or SWP_NOSIZE)
	        End Sub
	
	        Private Sub Timer1_Timer()
	           Dim lRet As Long
	           Timer1.Enabled = False     ' You will not need the Timer again.
	           Command1.Value = True      ' Click the CommandButton.
	           PropertyPage_ApplyChanges  ' Apply the new settings.
	           lRet = PostMessage(hwndPP, WM_CLOSE, 0, 0) ' Close the dialog box.
	        End Sub
	
	2. Select the timer and set the Interval property to 1, then close all design
	  windows.
	
	3. Open the design window for Form1 and click the UserControl to give it focus.
	  A MyFont property appears in the Properties window. Click on the MyFont
	  property. An ellipsis button appears. If you click it, a filtered Font common
	  dialog box appears (you never see the actual property page). This is fairly
	  smooth, but there is a brief flicker as the dialog box opens and closes.
	
	REFERENCES
	==========
	
	Visual Basic Help, version 6.0; search on: ProperyPage Object
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Chris E. Jolley, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbCtrlCreate kbPropSheet kbGrpDSUser kbVBp500 kbVBp600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
