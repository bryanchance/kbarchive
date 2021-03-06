---
layout: page
title: "Q80258: PC Gen: Contents of Modem Script File IBM5853.MDM"
permalink: /kb/080/Q80258/
---

## Q80258: PC Gen: Contents of Modem Script File IBM5853.MDM

{% raw %}

	Article: Q80258
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:2.1e
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 2.1e 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following is the contents of the Microsoft Mail version 2.1e modem script
	file IBM5853.MDM, which can be compiled with SCRCOMP.EXE:
	
	  ;*********************************************************************
	  ;
	  ;                    Microsoft Mail Script File
	  ;
	  ;       Filename: ibm5853.mdm
	  ;       Date    : March 21, 1990
	  ;       Script  : Standard script file for IBM 2400 bps modems
	  ;
	  ;     This modem has a set of 8 switches on the rear panel.  These
	  ;  switches should be set as follows:
	  ;
	  ;                      1  2  3  4  5  6  7  8
	  ;                 ON   X  X  X  X     X  X  X
	  ;                 OFF              X
	  ;
	  ;
	  ;     This script file contains the standard modem setup strings used
	  ;  by the External, Transmit and Listen programs. There are five
	  ;  procedures defined in this script file for setting up the modem and
	  ;  for connecting to a remote External machine.
	  ;
	  ;     The modem setup strings used here will be adequate for most
	  ;  people but there may be some changes required if you are dialing
	  ;  overseas and require a longer wait for Carrier Detect (S7 register)
	  ;  or if you wish to change the speaker volume. Note that if you used
	  ;  the -Innn option in version 1.0 or 2.0 that you will have to modify
	  ;  the S7 register and recompile this script file.
	  ;
	  ;     Consult your modem manual for more information on setup options.
	  ;
	  ;  Script procedures defined:
	  ;       INITIALIZE
	  ;       RESET
	  ;       CALL
	  ;       ANSWER
	  ;       DISCONNECT
	  ;
	  ;  Return codes for External, Transmit, Listen:
	  ;       0  - OK
	  ;       1  - CONNECT 300
	  ;       2  - not defined
	  ;       3  - NO CARRIER
	  ;       4  - ERROR
	  ;       5  - CONNECT 1200
	  ;       6  - not defined
	  ;       7  - BUSY
	  ;       8  - NO ANSWER
	  ;       9  - not defined
	  ;      10  - CONNECT 2400
	  ;      11  - not defined
	  ;      12  - CONNECT 9600 (high speed connection)
	  ;
	  ;
	  ;*********************************************************************
	
	  ;  Special Notes Regarding the IBM 5853 Modem:
	  ;  -------------------------------------------
	  ;
	  ;  While the line is ringing (you can here it ring), this modem will
	  ;  not accept any modem commands, including "ATA", the command
	  ;  required to answer the phone. Commands can be issued to the modem
	  ;  only when the modem stops ringing completely, or when it is in
	  ;  between rings.
	  ;
	  ;  "ATZ" cannot be issued safely between line rings, because this
	  ;  command would cause this modem to go off-hook and goes into data
	  ;  mode, and no further; modem commands are accepted until DTR is
	  ;  dropped, or 50 seconds later. ( The "ATZ" command would not reset
	  ;  the modem as well when the modem goes off-hook this way. The
	  ;  sequence "+++" would not bring the modem back to AT command mode
	  ;  either. )
	
	  INITIALIZE:
	          title "IBM 2400bps modem Script"
	
	          baud 2400                 ; set the baud rate
	          display "   Baud Rate : 2400"
	          $attempts = 5
	
	  init_retry:
	          if (ri = 1)               ; see if phone is ringing
	              goto init_retry
	
	          dtr 0                     ; make sure modem is On-Hook
	          wait 1
	          dtr 1
	
	          sendln "ATZ"              ; reset modem to default settings
	
	          wait 2
	          waitrsp 1
	
	          if ("0" isin response)
	              goto reset_okay
	
	          if ("OK" isin response)
	              {
	  reset_okay:
	              if (ri = 1)           ; see if phone is ringing
	                  goto reset_okay
	
	              sendln "ATE0M1V0X1"
	
	              wait 1
	              waitrsp 1
	
	              if ("0^M" isin response)
	                  {
	  set_options:
	                  if (ri = 1)      ; see if phone is ringing
	                      goto set_options
	
	                  sendln "ATS0=0S7=45S9=6S10=50S12=50"
	
	                  waitrsp 1
	                  if (response = "0^M")
	                      return 0
	                  }
	               }
	          dec $attempts
	          if ($attempts > 0)
	                  goto init_retry
	
	          return 4
	
	  RESET:
	          baud 2400                 ; set the baud rate
	          display "   Baud Rate : 2400"
	          $attempts = 5
	
	  init_retry:
	          if (ri = 1)               ; see if phone is ringing
	              goto init_retry
	
	          dtr 0                     ; make sure modem is On-Hook
	          wait 1
	          dtr 1
	
	          sendln "ATZ"              ; reset modem to default settings
	
	          wait 2
	          waitrsp 1
	
	          if ("0" isin response)
	              goto reset_okay
	
	          if ("OK" isin response)
	              {
	  reset_okay:
	              if (ri = 1)           ; see if phone is ringing
	                  goto reset_okay
	
	              sendln "ATE0M1V0X1"
	
	              wait 1
	              waitrsp 1
	
	              if ("0^M" isin response)
	                  {
	  set_options:
	                  if (ri = 1)      ; see if phone is ringing
	                      goto set_options
	
	                  sendln "ATS0=0S7=45S9=6S10=50S12=50"
	
	                  waitrsp 1
	                  if (response = "0^M")
	                      return 0
	                  }
	               }
	          dec $attempts
	          if ($attempts > 0)
	                  goto init_retry
	
	          return 4
	
	  CALL:
	          $ret = 8               ; set default ret code to "no answer"
	
	          clearrsp               ; clear the response buffer
	
	          echo 0                 ; do not display phone number
	
	          sendln "ATD" + dial_mode + phone_number  ; execute the dial up
	
	          echo 1                 ; turn echo back on
	
	          waitrsp 120            ; wait up to 2 minutes for return code
	                                 ;    from modem
	
	          if (response = "1^M")
	            {
	            baud 300
	            display ">>> CONNECT 300 <<<"
	            $ret = 1
	            }
	          else if (response = "3^M")
	            {
	            display ">>> NO CARRIER <<<"
	            $ret = 8             ; no answer or no connect
	            }
	          else if (response = "5^M")
	            {
	            baud 1200
	            display ">>> CONNECT 1200 <<<"
	            $ret = 5
	            }
	          else if (response = "7^M")
	            {
	            display ">>> BUSY <<<"
	            $ret = 7             ; busy
	            }
	          else if (response = "10^M")
	            {
	            baud 2400
	            display ">>> CONNECT 2400 <<<"
	            $ret = 10
	            }
	          else if (response = "25^M")
	            {
	            baud 1200
	            display ">>> CONNECT 1200/ECL <<<"
	            $ret = 5
	            }
	          else if (response = "30^M")
	            {
	            baud 2400
	            display ">>> CONNECT 2400/ECL <<<"
	            $ret = 10
	            }
	
	          return $ret            ; return connect baud rate to
	                                 ;    application
	
	  ANSWER:
	          $ret = 8               ; set default ret code to "no answer"
	
	          waitrsp 1              ; see if phone is ringing
	
	          if ("2^M" isin response)  ; 2 is numeric form of "RING"
	              {
	  answer_retry:
	              if (ri = 1)        ; if phone actually ringing at this
	                                 ;    moment
	                  goto answer_retry
	
	              if (listen = 1)    ; see if Listen program is running or
	                  sendln "ATD"   ; not answer phone in originate mode
	                                 ;    (Listen)
	              else
	                  sendln "ATA"   ; answer the phone normally
	
	              waitrsp 120        ; wait up to 2 minutes for return code
	                                 ;    from modem
	
	              if (response = "1^M")
	                {
	                baud 300
	                display ">>> CONNECT 300 <<<"
	                $ret = 1
	                }
	              else if (response = "3^M")
	                {
	                display ">>> NO CARRIER <<<"
	                $ret = 8             ; no answer or no connect
	                }
	              else if (response = "5^M")
	                {
	                baud 1200
	                display ">>> CONNECT 1200 <<<"
	                $ret = 5
	                }
	              else if (response = "10^M")
	                {
	                baud 2400
	                display ">>> CONNECT 2400 <<<"
	                $ret = 10
	                }
	              else if (response = "25^M")
	                {
	                baud 1200
	                display ">>> CONNECT 1200/ECL <<<"
	                $ret = 5
	                }
	              else if (response = "30^M")
	                {
	                baud 2400
	                display ">>> CONNECT 2400/ECL <<<"
	                $ret = 10
	                }
	              }
	
	          return $ret            ; return connect baud rate to
	                                 ;    application
	
	  DISCONNECT:
	          wait 2                 ; wait 2 seconds
	
	          send "+++"             ; send escape sequence to put modem
	                                 ;    back to command state
	          wait 2                 ; wait 2 seconds
	
	          clearrsp               ; clear the response buffer
	
	          sendln "ATH0"          ; hang up the phone
	
	          waitrsp 1              ; wait for a response
	
	          if (response != "0^M") ; if hang up failed, drop DTR to force
	                                 ;    hang up
	              {
	              DTR 0              ; drop DTR to reset modem
	              wait 2             ; some modems require a delay here
	              DTR 1              ; raise DTR
	              clearrsp           ; clear response buffer
	              }
	
	          return 0               ; always return OK
	
	Additional query words: 2.10 2.1 2.10e
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN210e
	Version           : WINDOWS:2.1e
	
	=============================================================================
	

{% endraw %}
