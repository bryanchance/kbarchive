---
layout: page
title: "Q139547: How to Use the GetVolumeInformation API Call"
permalink: /kb/139/Q139547/
---

## Q139547: How to Use the GetVolumeInformation API Call

{% raw %}

	Article: Q139547
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): kbcode kbvfp300 kbvfp600
	Last Modified: 03-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Win32API set offers a rich collection of features that were not available to
	previous versions of FoxPro for Windows. This article shows by example how to
	call the Win32API GetVolumeInformation function.
	
	MORE INFORMATION
	================
	
	The GetVolumeInformation function returns information about a file system and
	volume whose root directory is specified in the call. While there are several
	common file systems (such as NTFS, FAT, and CDFS), new file systems may be in
	development that can affect things such as storage requirements for
	applications, so calling GetVolumeInformation may provide valuable information
	that you can use in your application. You can also use some of the information
	returned by this call to calculate disk space and file sizes. The following code
	shows how to declare and use this API call.
	
	Code Sample
	-----------
	
	  **---------------------------------------------------------------**
	  ** Program: Getvol.prg                                           **
	  ** Purpose: Demonstrates how to declare and use the Win32        **
	  **          GetVolumeInformation API.                           **
	  **---------------------------------------------------------------**
	  PUBLIC lpRootPathName, ;
	          lpVolumeNameBuffer, ;
	          nVolumeNameSize, ;
	          lpVolumeSerialNumber, ;
	          lpMaximumComponentLength, ;
	          lpFileSystemFlags, ;
	          lpFileSystemNameBuffer, ;
	          nFileSystemNameSize
	
	  lpRootPathName           = "E:\"      && Drive and directory path
	  lpVolumeNameBuffer       = SPACE(256) && lpVolumeName return buffer
	  nVolumeNameSize          = 256        && Size of/lpVolumeNameBuffer
	  lpVolumeSerialNumber     = 0          && lpVolumeSerialNumber buffer
	  lpMaximumComponentLength = 256
	  lpFileSystemFlags        = 0
	  lpFileSystemNameBuffer   = SPACE(256)
	  nFileSystemNameSize      = 256
	
	  DECLARE INTEGER GetVolumeInformation IN Win32API AS GetVolInfo ;
	          STRING  @lpRootPathName, ;
	          STRING  @lpVolumeNameBuffer, ;
	          INTEGER nVolumeNameSize, ;
	          INTEGER @lpVolumeSerialNumber, ;
	          INTEGER @lpMaximumComponentLength, ;
	          INTEGER @lpFileSystemFlags, ;
	          STRING  @lpFileSystemNameBuffer, ;
	          INTEGER nFileSystemNameSize
	
	  RetVal=GetVolInfo(@lpRootPathName, @lpVolumeNameBuffer, ;
	                    nVolumeNameSize, @lpVolumeSerialNumber, ;
	                    @lpMaximumComponentLength, @lpFileSystemFlags, ;
	                    @lpFileSystemNameBuffer, nFileSystemNameSize)
	
	  **---------------------------------------------------------------**
	  ** Return code values for file system flags. Return codes are    **
	  ** shown in parentheses.                                         **
	  **---------------------------------------------------------------**
	  ** FS_CASE_SENSITIVE     If this flag is set, the file system    **
	  **                       supports case-sensitive file names      **
	  **                       (0001h).                                **
	  **                                                               **
	  ** FS_CASE_IS_PRESERVED  If this flag is set, the file system    **
	  **                       preserves the case of file names when   **
	  **                       it places a name on disk (0002h).       **
	  **                                                               **
	  ** FS_UNICODE_ON_DISK    If this flag is set, the file system    **
	  **                       supports Unicode in file names as they  **
	  **                       appear on disk (0004h).                 **
	  **                                                               **
	  ** FS_PERSISTENT_ACLS    If this flag is set, the file system    **
	  **                       preserves and enforces ACLs. For        **
	  **                       example, NTFS preserves and enforces    **
	  **                       ACLs, but HPFS and FAT do not (0008h)   **
	  **                                                               **
	  ** FS_FILE_COMPRESSION   The file system supports file-based     **
	  **                       compression (0010h)                     **
	  **                                                               **
	  ** FS_VOL_IS_COMPRESSED  The specified volume is a compressed    **
	  **                       volume; for example, a DoubleSpace      **
	  **                       volume (8000h)                          **
	  **---------------------------------------------------------------**
	  ** The following information is pertinent to several of the      **
	  ** listed flags:                                                 **
	  **---------------------------------------------------------------**
	  ** The FS_VOL_IS_COMPRESSED flag is the only indicator of volume-**
	  ** based compression. The file system name is not altered to     **
	  ** indicate compression. This flag comes back set on a Double-   **
	  ** Space volume, for example. With volume-based compression, an  **
	  ** entire volume is either compressed or not compressed.         **
	  **                                                               **
	  ** The FS_FILE_COMPRESSION flag indicates whether a file system  **
	  ** supports file-based compression. With file-based compression, **
	  ** individual files can be compressed or not compressed.         **
	  **                                                               **
	  ** The FS_FILE_COMPRESSION and FS_VOL_IS_COMPRESSED flags are    **
	  ** mutually exclusive; both bits cannot come back set.           **
	  **---------------------------------------------------------------**
	  ** Note that the return value can be a combination of the        **
	  ** individual return values. For example, a return value of 6    **
	  ** indicates that case is preserved (FS_CASE_IS_PRESERVED) and   **
	  ** the file system supports UNICODE in file names                **
	  ** (FS_UNICODE_ON_DISK).                                         **
	  **---------------------------------------------------------------**
	
	  DEFINE WINDOW ShowInfo FROM 0,0 TO 10,70 ;
	                         FLOAT CLOSE ;
	                         TITLE "Drive Information for " + ;
	                         ALLTRIM(lpRootPathName) ;
	                         FONT "Courier",10
	
	  ACTIVATE WINDOW ShowInfo
	  MOVE WINDOW ShowInfo CENTER
	
	  **--------------------------------------------------------------**
	  ** Because several of the return values are padded with a null  **
	  ** terminator, you will need to strip off the null terminator   **
	  ** in order to get the correct value, which is what is done     **
	  ** using the LEFT, ALLTRIM, and LEN functions.                  **
	  **--------------------------------------------------------------**
	  @ 0,1 SAY "Drive & path name            : " + ;
	     ALLTRIM(lpRootPathName)
	
	  @ 1,1 SAY "Volume name                  : " + ;
	     LEFT(ALLTRIM(lpVolumeNameBuffer),LEN(ALLTRIM(lpVolumeNameBuffer))-1)
	
	  @ 2,1 SAY "Max #/chars in vol name      : " + ;
	     ALLTRIM(STR(nVolumeNameSize))
	
	  @ 3,1 SAY "Volume Serial #              : " + ;
	     ALLTRIM(STR(lpVolumeSerialNumber))
	
	  @ 4,1 SAY "Max #/chars in dir/file names: " + ;
	     ALLTRIM(STR(lpMaximumComponentLength))
	
	  @ 5,1 SAY "File System Flags            : " + ;
	     ALLTRIM(STR(lpFileSystemFlags))
	
	  @ 6,1 SAY "File System type             : " + ;
	     LEFT(ALLTRIM(lpFileSystemNameBuffer), ;
	     LEN(ALLTRIM(lpFileSystemNameBuffer))-1)
	
	  @ 7,1 SAY "File Sys Name Size           : " + ;
	     ALLTRIM(STR(nFileSystemNameSize))
	
	  ** ----------------------------< End Code >-------------------------- **
	
	  If this code is run on an NTFS partition, the following would be typical
	  output:
	
	  Drive & Path name             : E:\ 
	  Volume name                   : Scratch
	  Max #/chars in vol name       : 256
	  Volume Serial #               : 484847074
	  Max #/chars in dir/file names : 255
	  File System Flags             : 31
	  File System Type              : NTFS
	  File System Name Size         : 256
	
	  The File System Flags value of 31 is a combination of the following file
	  system attributes:
	
	  Flag                      Hex Value   Decimal Value
	  ---------------------------------------------------
	  FS_CASE_SENSITIVE             1             1
	  FS_CASE_IS_PRESERVED          2             2
	  FS_UNICODE_ON_DISK            4             4
	  FS_PERSISTENT_ACLS            8             8
	  FS_FILE_COMPRESSION          10            16
	  ---------------------------------------------------
	  Total return value:                        31
	
	The value returned for the serial number is the decimal notation of the
	hexadecimal value displayed when you use a DIR command. In the information shown
	previously in this article, the value that is displayed by the DIR command for
	this drive is 1CE6-2DE2 (hexadecimal), which corresponds to the serial number
	484847074.
	
	For additional information on this API function, please see search for
	GetVolumeInformation in the Win32API Help file. Note that this help file is
	available only on the compact disc version of Visual FoxPro; this help file is
	not shipped with the disk version. For more information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q139172 PRB: Visual FoxPro CD-ROM Compact Disc Includes Extra Files
	
	For information about the DECLARE - DLL command, please refer to the Visual
	FoxPro Help file.
	
	Additional query words: VFoxWin drive volume disk attributes
	
	======================================================================
	Keywords          : kbcode kbvfp300 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP600
	Version           : 3.00
	
	=============================================================================
	

{% endraw %}
