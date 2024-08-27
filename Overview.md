# Overview

In early 2024 (???) the 3D printer in the machine shop (Fusion3 f410) failed catastrophically.  The controller
board, the LCD display, the SD card, and the filament sensor all died.


The controller board (Duet 2 Ethernet) and the LCD display (Panel Due) are both Open Source hardware,
manufactured by Duet3D.  The firmware running on the controller board  is a slightly modified version
of RepRap firmware. The filament sensor and the old PanelDue board are NLA, and the version of RepRap firmware that was
running is quite ancient.


Unfortunately, the folks at Fusion3 do not provide any support AT ALL for modifying or updating the
firmware.


In order to get the system back into operation, I replaced the controller with a Duet 2 WiFi (exactly the same board, with
a WiFi module plugged in instead of an Ethernet module. I replaced the (NLA) PanelDue with a newer version
PanelDue.  And I updated the firmware to the newer (but still old) RepRap Firmware version 1.18.

