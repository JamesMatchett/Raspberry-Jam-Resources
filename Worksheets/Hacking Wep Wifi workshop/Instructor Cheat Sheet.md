# Instructor's cheat sheet, Hacking WEP Wi-Fi with Pi 3's

 Workshop created by @JamesMatchett

## Before the workshop starts:

* Check all pi’s have been flashed with the correct adapter firmware and have aircrack installed on them by running through the first few steps of the worksheet, make sure to reboot the pi afterwards.
* Setup a Wi-Fi router with WEP security and make a note of the password.
* Connect one or more devices to the network using the password (this can your phone, laptop, anything, it just has to be connected and in close proximity to the pi’s and routers)
* IMPORTANT NOTE: Ensure that if your Wi-Fi network is 5GHz, force it to use 2.4GHz by either using a 2.4GHz only device or by repeatedly connecting and disconnecting.
The Pi's can only intercept 2.4GHz traffic and the workshop won't work if the connected device is using 5GHz.

## During the workshop:

* Give a *quick* breakdown of the workshop's content, how Wi-Fi works and why WEP is vulnerable.
* Get the attendees started by following the worksheet from the *very* beginning,     
***commands to be typed in are in red*** and must be entered in the order they appear in the worksheet E.g.
- `sudo airmon-ng check kill`
- `nexutil -m2`
- `sudo airmon-ng start wlan0`  


* Once all attendees get into monitor mode and are watching the live dump of what networks are in range of the Wi-Fi chip, ask them to call out the MAC Address, Channel and SSID of the target router. Write this information on the whiteboard for the next commands. This means they are far less likely to target a router that isn't yours!

* As soon as the attendees get to the "aireplay" command, you can begin to speed up the rate the attack captures traffic by standing beside the Pi's with the phone or laptop you connected previously and trying to load a webpage repeatedly, although nothing will load this will still generate traffic and reduce the time taken to capture enough packets.

<div class="page-break"></div>

* The final command "sudo aircrack-ng WEPcrack-01.cap" can either fail or succeed depending on how many packets have been captured. If it fails simply re-enter the command and run again or wait for the program to auto restart when enough new packets have been captured.

## Once the key has been cracked:

* Get parents/kids attending the workshop and try to connect their devices (either their mobile phones or if they don't have one their Pi after a reboot to reset to default configuration) using the Wi-Fi password they've captured, show them that if this was a "real Wi-Fi network" they'd be able to x attacks.

## Shortcuts:

* Ctrl + C stops any captures/processes underway so you don't have to force close a terminal window.
* Using the up-arrow to re-enter/edit commands saves so much time.

## Things that typically go wrong:

* Last command doesn't work/number of keys doesn't increase for file entered a the last operand:

  * This means that the capture has either stopped or is under a different filename, check the attendee's terminal windows to see if another capture has to be started or if one is underway under a different filename than "WEPcrack-01.cap" *by default it usually changes to 02 or 03 instead of 01.*

* Packet capture going really slowly:

  * make sure your connected device is still connected and try to generate some traffic by standing beside the Pi's and trying to browse the internet, nothing will load however the requests sent will generate traffic for the attendee's Pi to capture, I find that putting the Pi between your device and the router works best. *Using this method you can actually control the speed the workshop runs at so if it's running behind you can really get it moving!*

* "Network is open/WPA2" error on final command:

  * This means the attendee has probably started the capture on the wrong network, restart the capture and make sure the right MAC address is entered.

* Aircrack module won't start/monitor mode can't be started:

  * This means either the commands have been mistyped/in the wrong order or something has gone wrong configuration wise, reboot the pi and take care entering the initial instructions in the right order.

* Pi won't boot or Aircrack & monitor mode will not work:

  * This probably means there's a problem with the image on the SD card, I cover this in more detail in the flashing guide but just make sure the image isn't "shrunk" and the SD card is seated properly.



#### Best of luck on this introduction to InfoSec!
