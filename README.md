# Delarion
A custom core XY 3d printer

Delarion is a project aimed to make a decent bang for your buck core xy 3d printer. The frame is made out of 2020 aluminum extrusions giving it a sturdy rigid frame with ball screws,linear rails to provide that buttery smooth movement.

How it began? basically every geek has an urge to keep building random nerd stuff via youtube tutorial, i went via it through but gotta admit the work-around required to make something without a 3d printer that uses is quite messy with the final thing not having that finesse instead a messy encasement made out of scraps, i guess we all been there. When i went out to buy a cheap 3d printer the results werent that good. Yes 3d printers are nowadays quite cheap starting from a 100 bucks usd but honestly thoose are mostly crap and why to even buy an ender 3 nowadays as everything is just better than it. Yes bamboo is an option some budget products are there but still not satisfactory. So a good printer will cost about 500 dollars while cheap ones are just cheap(Atleast over here in my area) So the quest beagn to create a 3d printer and voila that how this project began.

Key takaways:
Delarion utilizes Klipper firmware with tmc2208 drivers,nema17 stepper motors. The main MCU is an esp32 s3, which does provide endless possibilities for trying out diff stuff.

PCB:
its a really basic custom pcb, which includes an MPU6050, tmc2208 drivers, Note that you will need to provide the appropriate 24volts clean supply to the board, 5v supply is cleanly regulated by an ams117.
