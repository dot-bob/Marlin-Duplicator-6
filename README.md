# Marlin 3D Printer Firmware for the Wanhao Duplicator 6 / Monoprice Ultimate 3D Printer

<img align="top" width=175 src="buildroot/share/pixmaps/logo/marlin-250.png" />

Marlin specific documentation can be found at [The Marlin Documentation Project](https://www.marlinfw.org/).
Please test this firmware and inform us if it misbehaves in any way, volunteers are standing by!

Marlin for the Tevo Black Widow is base off Release Candidate -- Marlin 1.1.0-RC8 - 6 Dec 2016
For the Marlin specific release notes refere to the Marlin RC brach located here: https://github.com/MarlinFirmware/Marlin/tree/RC.

Duplicator 6 Specific Changes:

Version 1.1.0-RC8 02-27-17 Version 4.5 (RM)
- Added support for the PCA9632 that drives the RGB leds behind the encoder dial.  Use gcode command M150 to set a color.
- Added option to enable or disable the auto cooldown feature when canceling a print from the SD card.
- Added replaced "Babystep Z" in the main menu during a print with "Live adjust Z" if using an auto leveling probe.  Live adjust Z
 modifies the Z offset in realtime and saves the eeprom on exit.

Version 1.1.0-RC8 02-11-17 Version 4.4 (RM)
-Removed unused example configurations.
- Add status_printf function for status line of display.
- Added hotend name to heating status indicator.

Version 1.1.0-RC8 02-05-17 (bug fix) Version 4.3 (BC)
- Increased both THERMAL_PROTECTION_PERIOD and WATCH_TEMP_PERIOD to 90 seconds to prevent false Thermal Run-away errors (time may need to be tweaked) from the hot-end

Version 1.1.0-RC8 02-04-17 (proposed fixed) Version 4.2 (BC)
- Enabled Analog connector(J9) to support a filament Run-out sensor (mechanical switch)
- Modified sensor code in Marlin_Main.cpp to allow filament run-out support while print USB AND SD_Card
- Increased both THERMAL_PROTECTION_BED_PERIOD and WATCH_BED_TEMP_PERIOD to 90 seconds to prevent false Thermal Run-away errors (time may need to be tweaked)

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


[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)
