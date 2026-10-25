this pcb was created in Kicad version 10.
as you can see in the schematics the XL103 hasnt been mounted on the pcb this is beaacuse of the reason of thermal issues. Adding a high voltage step down convertor produces a lot of heat, which risk damagaing the other components.
clean 24volts and 5volts from the step down convertor need to be provided to the designated pins.Use of active cooling is required for the same unless a big explosion is fancied.
Heatsnks and proper active cooling should also be applied to the tmc2208/2209 drivers or otherwise damage risk remains high.

A thorough DRC has been ran through there are some errors regarding high power mosfets near signal pins which can meddle with it but i do have added capacitors into the play and kept the mosfet at the back of the board so yeah hopefully all good
