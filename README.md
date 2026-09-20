# Delarion
A custom core XY 3d printer

Delarion is a project aimed to make a decent bang for your buck core xy 3d printer. The frame is made out of 2020 aluminum extrusions giving it a sturdy rigid frame with ball screws,linear rails to provide that buttery smooth movement.

<img width="1767" height="1048" alt="Screenshot 2026-09-06 150802" src="https://github.com/user-attachments/assets/610b3218-75e4-4d01-9691-6848fe283e0e" />


How it began? basically every geek has an urge to keep building random nerd stuff via youtube tutorial, i went via it through but gotta admit the work-around required to make something without a 3d printer that uses is quite messy with the final thing not having that finesse instead a messy encasement made out of scraps, i guess we all been there. When i went out to buy a cheap 3d printer the results werent that good. Yes 3d printers are nowadays quite cheap starting from a 100 bucks usd but honestly thoose are mostly crap and why to even buy an ender 3 nowadays as everything is just better than it. Yes bamboo is an option some budget products are there but still not satisfactory. So a good printer will cost about 500 dollars while cheap ones are just cheap(Atleast over here in my area) So the quest beagn to create a 3d printer and voila that how this project began.

Key takaways:
Delarion utilizes Klipper firmware with tmc2208 drivers,nema17 stepper motors. The main MCU is an esp32 s3, which does provide endless possibilities for trying out diff stuff. The mian idea for klipper rather than some other mcu based firmware is that 1) it utilizes microprocessor so yeah huge speed advantage, 2) everyone has an old laptop or a raspberry pi laying round, 3) Documentaion

PCB:
its a really basic custom pcb, which includes an MPU6050, tmc2208 drivers, Note that you will need to provide the appropriate 24volts clean supply to the board, 5v supply is cleanly regulated by an ams117. And yeah IRLZ44N needs to be attached at the bottom of the board not the top.

<img width="1724" height="1020" alt="Klipper_mcu" src="https://github.com/user-attachments/assets/056f84d5-a3d5-4a0c-85c6-29b3c66b95aa" />
This is the first PCB i made so yeah not beautiful, not well laid out, but yeah it works 100% or thats what i atleast hope for


3d model Demo link::
https://cad.onshape.com/documents/ddc5642abc531e1225c0dc8b/w/1fb68ecf66842d529f7141f3/e/0a949859a3af9baaf41af0a4

CREDITS:
@hacktheclub honetly this project was only possible cause of them, they helped me connect find the right people and finally pushed me to make my dream.

@Stardance as per this commit i am submitting it for funding, fingers crossed that i get funded to make it actual project kudos

@RaygunRupe at first i just started to make it blindly, buy stuff build it and figure on the fly, the only reason i am actually stuck in this deep at designing, to polish the looks is cause of this mf, otherwise i would had already made a mess by skipping all the design aan CAD stuff

@Mistsu Makes(youtube) I waatched his toutorial to understand how to do this project, how the motion system works how the bedslinging mechanism should, if it werent for him, it would had been quite more difficult. And yeah it was this dude only whoose video after watching i decided that yeah lets fing do it, he was my starting point kinda that yeah i can too make this.

@ 3ddistributed.com This gottna be the best website to understand coreXY working, i watched countless toutorials but in the end got how to do this vis this website's infographics only

@Slack hardware community, thoose guys also helped me a lot from figring out how this shit works to networking with people that helped me make this


