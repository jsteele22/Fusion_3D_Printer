# Overview

In early 2024 (???) the 3D printer in the machine shop (Fusion3 f410) failed catastrophically.  The controller
board, the LCD display, the SD card, and the filament sensor all died.


The controller board (Duet 2 Ethernet) and the LCD display (Panel Due) are both Open Source hardware,
manufactured by Duet3D.  The firmware running on the controller board  is a slightly modified version
of RepRap firmware. The filament sensor and the old PanelDue board are NLA, and the version of RepRap firmware that was running is quite ancient, hence hard to get help on.


Unfortunately, the folks at Fusion3 do not provide any support AT ALL for modifying or updating the
firmware.


In order to get the system back into operation, I replaced the controller with a Duet 2 WiFi (exactly the same board, with
a WiFi module plugged in instead of an Ethernet module. I replaced the (NLA) PanelDue with a newer version
PanelDue.  And I updated the firmware to the newer (but still old) RepRap Firmware version 1.18.

Thus, the printer is not supported by Fusion3 any more.  All support is obtained from the open source community.

# Cause of the failure.

After some poking around, I discovered the cause of the failure.  A metal screw that supports the center of the glass build plate had worn through the Kapton insulation of the build plate heating pad. This provide a +24V, high current power supply to a pin of the Duet2.  The corresponding PCB trace and even the conductors inside the CPU were extremely crispy. 
 
As a fix, I added some more Kapton, lowered the support screw, and added some insulating material between the screw and the heating pad.  The printer works, but unfortunately the glass build plate is not perfectly flat.  This results in problems with first layer adhesion.

# Print Head

The original Z-probing system relied on electrical probing of aluminum foil pads in the 4 corners of the build plate.  Modern fuirmware does not support this method any more (hence the roadblock at v 1.18.)  In order to better probe the build plate, I ordered a piezoelectric sensor (Orion 2) from Precision Piezo.

The piezo sensor is a small PCB with 2 piezo elements. The hotend is supported by the PCB which is supported by the main print head mount, so any pressure of the build plate on the hotend nozzle creates an electrical signal, which is amplified and sent to the controller.

In order to use this sensor, and to overcome some shortcomings in the Fusion3 design, I designed a new hotend mount using OnShape.  (A free online CAD system)  The new system has two securely supported part cooling fans with very short ducts pointing just below the nozzle tip.  The same hotend components (E3D Volcano nozzle, heater block, thermistor,heatbreak, heatsink, heatsink fan and fan clamp) were used. I used the step model from Precision Piezo for the clamp that holds the heatsink. 

The overall design at the moment is a horizontal shelf resembling a sideways "T" that the piezo PCB (plus hotend) mounts to (from below), the 2 fan units mount to (from the sides), and the Bowden tube adapter mounts to (from above.)  Each fan unit is two pieces that clamp the fan and hold the duct in place.
