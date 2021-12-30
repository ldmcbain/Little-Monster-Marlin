# Little-Monster-Marlin
Marlin port for the TEVO Little Monster

I was having too many issues with the Smoothieware firmware delivered with my Litte Monster.  Wouldn't home correctly, failed prints constantly, etc.  The support for this printer from the manufacturer is almost non-existant, so I decided to port the printer to Marlin code instead.  I was unable to locate a recent port for the little monster with the latest Marlin, so I went about it on my own and decided I'd share my results.

The printer is now working beautifully.  I've completed many prints and every one has worked on the first try.

NOTE: In the time since I've first purchased the printer, I"ve had to perform several updates to it.  In the original packaging, the Power supply was DOA, and they did not send gears to attach to the stepper motors.  While I happened to have a compatible power supply handy, I had to procure new gears which did not match the original manufacturers.  If you use this, you'll have to update the steps/mm to match your hardware (XYZ_PULLEY_TEETH parameter located in Configuration.h).  I've also replaced the original print bed with a glass plate (and I'm about to upgrade the pully sled wheels to something that won't squeek constantly..)

There were a few portions of the standard Marlin code which I updated that there may have been a better way to do it, but my method did work in the end.  This includes changes to:
  pins_MKS_SBASE.h (pin definitions did not match my MKS SBASE v1.3 board for some reason.  Don't know if this is something to do with a poor nock-off used or what.
  temperature.cpp (was having motherboard heating issues w/ the heat bed FETs, however there is a MB fan attached to the hotend fan, so changed to make those come on if the heated bed is on.)
  
I have also included my version of the MKSTFT28 LCD firmware I've used to upgrade from (kinda had to as the old one was set for Smoothieware codes).  

I also have a separate project (hopefully to be uploaded in the near future) which I use to help parse and create my gcode files utilizing flashprint software.
  
  
