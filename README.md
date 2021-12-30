# Little-Monster-Marlin
Marlin port for the TEVO Little Monster

I was having too many issues with the Smoothieware firmware delivered with my Litte Monster.  Wouldn't home correctly, failed prints constantly, etc.  The support for this printer from the manufacturer is almost non-existant, so I decided to port the printer to Marlin code instead.  I was unable to locate a recent port for the little monster with the latest Marlin, so I went about it on my own and decided I'd share my results.

The printer is now working beautifully.  I've completed many prints and every one has worked on the first try.  I do have a nagging issue with G28 homing which I can't seem to correct.  I think it is a heating issue with the MKS board, but can't be sure.  I've made some changes (see below) to turn on the motherboard fan which seems to have helped a lot but the issue still crops up every now and then.  Ususally a printer shutdown for a while fixes the issue.

NOTE: In the time since I've first purchased the printer, I"ve had to perform several updates to it.  In the original packaging, the Power supply was DOA, and they did not send gears to attach to the stepper motors.  While I happened to have a compatible power supply handy, I had to procure new gears which did not match the original manufacturers.  If you use this, you'll have to update the steps/mm to match your hardware (XYZ_PULLEY_TEETH parameter located in Configuration.h).  I've also replaced the original print bed with a glass plate (and I'm about to upgrade the pully sled wheels to something that won't squeek constantly..)

Also you should be aware the this will change your required Start/Stop GCODE!  I've included my recommended Start/Stop GCODE to use as a starting point.

There were a few portions of the standard Marlin code which I updated that there may have been a better way to do it, but my method did work in the end.  This includes changes to:
  pins_MKS_SBASE.h (pin definitions did not match my MKS SBASE v1.3 board for some reason.  Don't know if this is something to do with a poor nock-off used or what.
  temperature.cpp (was having motherboard heating issues w/ the heat bed FETs, however there is a MB fan attached to the hotend fan, so changed to make those come on if the heated bed is on.)
  
To update the firmware in the Little Monster:
1. Open the project in Atom (in admin mode).
2. Update the XYZ_PULLEY_TEETH parameter in Configuration.h
3. Compile
4. Copy firmware.bin located in .pio\build\LPC1768\ to a micro-sd card
5. Insert card into MKS SBASE mother board and cycle power
  
I have also included my version of the MKSTFT28 LCD firmware I've used to upgrade from (kinda had to as the old one was set for Smoothieware codes).  To Update the LCD: simply copy the files in the MKSTFT28 folder to an SD card, insert into LCD screen, and cycle power.

I also have a separate project (flashprint converter) which I use to help parse and create my gcode files utilizing flashprint software.
  
  
