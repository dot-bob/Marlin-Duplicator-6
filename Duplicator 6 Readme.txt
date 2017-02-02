Duplicator 6 Firmware - Marlin 1.1.0-RC8 by dot_bob (Robert Mendon)
Release Notes

Background:

Being an embedded linux kernel developer myself and being tired of the limited features of the stock firmware
I decided to make my own port of the Marlin firmware.  My initial goal was to make the firmware as vanilla as possible allowing
future ports to mainline to be quick and simple.  For the desciription of changes see notes below.

Usage:

If you are stock Duplicator 6 compile as is.  Use the Aduino Software IDE and add the U8glib graphics library to compile and load the firmware.

Changes:

Version 1.1.0-RC8 02-01-17 (Official Public Release) Version 4
- Enabled the LCD info menu.
- Changed the move axis menu to select the axis first and distance second.
- Relocated the move axis menu item to the top of the prepare menu.  
- Added filament change option to the prepare menu.
- Reduced the duration of the filament change beep from 300ms to 20ms.
- Added a quick menu with commonly used functions.
- Added code to prevent a z-bump if the axis hasn't been homed.  This is to prevent driving the build plate past Z Max.
- Added option to drop build plate from the prepare menu.

Version 1.1.0-RC8 01-23-17 (Third Test Release) Version 3
- Added LED lighting setting to EEPROM.
- Added LED dimming setting to the Control Menu.
- Added confirm to stop print when printing with sd card.
- Fixed a bug in the stop print function by adding code to shutdown the hotend and heatbed.
- Added the ability to adjust stepper driver current from the Control -> Motion lcd menu.
- Added auto leveling grid boundry positions from marlin development repository.
- Changed menu selection from hollow box to inverted text.
- Changed the menu beep from 100ms to 5ms.
- Updated Conditionals_post.h so the #define XXXXXX_PROBE_BED_POSITION statements are no longer needed.


Version 1.1.0-RC8 01-16-17 (Second Test Release) Version 2
- Fixed many display issues and improved responsiveness.
- Added Support for the LED light
- Added adjusting stepper driver currents with command M907 and saving in EEPROM and supported in commands M500, M502, M503;
- Removed Babystep for X and Y axis.

Version 1.1.0-RC8 01-16-17 (Initial Test Release) Version 1
- Increased the display menu timeout from 15 seconds to two minutes by changing the line "#define LCD_TIMEOUT_TO_STATUS 15000"
to "#define LCD_TIMEOUT_TO_STATUS 120000" in the file ultralcd.h.
- Added "Babystep Z" to the Main Menu when performing a print.  This allows the user to quickly access the the realtime z height ajustment.


Recommeded GCode scripts:

; Duplicator 6 / Monoprice Maker Ultimate Start Script V3
M107 ; start with the fan off
G28 ; home
;G29 ; probe bed
G1 Z15 F3600 ; move the platform 15mm down from home
G0 X0 Y0 ; Rapid move X0 Y0
G92 E0 ; zero the extruded length
; perform wipe and prime
G1 X8.0 Z0.0 F3600   
G1 X10.0 Z0.2 F3600
G1 X70 Z0.4 E9.0 F1000 ; prime
G1 X100.0 E22 F1000 ; prime
G1 X130 Z0.2 F9000 ; pull away wipe
G1 X140 F9000     ; finish wipe
G1 Z2 F1000 ; lift head before first move
G1 X100 Y100 F5000 ; Move nozzle to center of bed
G92 E0 ; zero extruder again
; Place printing message on LCD screen
M117 Printing...

; Duplicator 6 / Monoprice Maker Ultimate Stop Script V2
G92 E0 ; zero the extruded length 
G1 E-1.5 F500 ; retract the filament to release some of the pressure
M104 S0 ; turn off heater
M140 S0 ; turn off bed
M106 S0 ; turn off part fan
G91 ; relative positioning
G1 Z3 ; lower build plate a few mm
G90 ; absolute positioning
G28 X0 Y0 ; move head out of the way
G1 Z170 F9000 ; lower build plate
M84 ; disable stepper motors