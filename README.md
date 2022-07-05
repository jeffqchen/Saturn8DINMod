# Sega Saturn 8-pin mini DIN Mod

<img src="./Pics/8dins.jpg" width="600px" />

This is a mod design with a PCB and a 3D printed shroud, for replacing a broken 10-pin mini DIN AV port on a Sega Saturn with an 8-pin mini DIN port. It will output an RGBS video signal and stereo audio, conforming to the XRGB pinout.



<img src="./Pics/XRGB_pinout.jpg" width="300px" />

-------------
## Explanation

The Sega Saturn opted for a strange 10-pin mini DIN connector for its AV output. Decades of abuse and oxidation has rendered a lot of them inoperable. Some horror story has it shorting +5V to GND internally, almost killing the machine itself.

<img src="./Pics/flaky10din.jpg" width="600px" />

*Flaky old 10-pin mini DIN*

"Just replace it with a new one!" You may say. But looking around the internet, it's impossible to find an exact replacement 10-pin mini DIN female socket.

On the other hand, if you want to hook up a Saturn to your setup, you will need a 10-pin AV cable. This cable will only work with the Saturn since no other device uses the same type of connection. Bummer. This cable is also known for it's flaky connection. Accidentally sneeze on it, your picture turns blue and you lose an audio channel. To add salt to injury, there is no way to buy that male 10-pin mini DIN plug either, even if you plan to build your own dream cable. Oof.

Meanwhile, 8-pin mini DIN sockets are eye-watering cheap and abundantly available on Aliexpress 🤡

<img src="./Pics/8din_aliexpress.jpg" width="800px" />

This is why I made this decision - the 10-pin mini DIN connector has to go.

<img src="./Pics/3-10_din.jpg" width="400px" />

Looking at the Saturn's schematic, its RGB lines are properly DC-decoupled with 220uF caps. Its CSync line needs to be attenuated and DC-decoupled for normal 75 ohm devices. This is very similar to an XRGB 8-pin DIN video cable, which is just straight pass-throughs with no extra components.

Consoles that use 8-pin mini DIN RGBS cables that I am aware of:
- NESRGB (8-pin mini DIN version)
- 3DORGB
- Supergun Minigun

If you have a cable for any of these devices above, you are already set!

<img src="./Pics/8din_scart.jpg" width="400px" />

*[Mini-DIN 8p to RGB SCART adapter](https://etim.net.au/shop/shop.php?crn=203&rn=543&action=show_detail) from Tim Worthington*

Retro Gaming Cables from UK sells a cable that's similar to Tim's cable [Here](https://www.retrogamingcables.co.uk/8PIN-MINI-DIN-TO-RGB-EUROSCART-TIM-WORTHINGTON-NES-RGB-ATARI-2600-HAS-SUPERGUN-Sega-Game-Gear-Philips-CDi-Colecovision-Intellivision-Panasonic-3DO).

Retro Access sells an [XRGB to BNC adapter](https://retro-access.com/collections/xrgb-adaptors/products/bnc-to-8-pin-mini-din-for-extron-to-xrgb-mini-pro-coaxial-multicore?variant=45853115731).

Since this port conforms to the XRGB standard, the signal can go straight into the RGB IN port on a Framemeister with an 8-pin mini DIN cable.

But of course, if you don't have any of those above, you can still build my [8DIN2VGA dongle](https://github.com/jeffqchen/8DIN2VGA) and output from a VGA cable!

<img src="./Pics/8din2vga.jpg" width="400px" />


-------------
## Parts

- [Saturn 8-pin mini DIN Mod PCB](https://oshpark.com/shared_projects/etx4c03R)
- 8-pin mini DIN Female Socket

<img src="./Pics/8din.jpg" width="300px" />

For Attenuated CSync:
- SMD Capacitor 100uF / 6.3V / Imperial 1206 Size - [Link](https://github.com/jeffqchen/JeffParts/blob/main/Components/100uF%20SMD%20Cap/info.md)
- SMD Resistor 470 Ohm / Imperial 0603 Size (for 75 Ohm CSync, otherwise zero Ohm)

-------------
## 3D Printing

Print the model as-is without support. Easy and simple.

<img src="./Pics/3dprint.jpg" width="600px" />

-------------
## Port Assembly

Clean up the perimeter of the PCB so nothing is sticking out.

<img src="./Pics/pcb_before.jpg" width="600px" />

Populate the PCB. Choose one from these 3 options.

- For attenuated 75 Ohm CSync:
  - Solder the 100uF capacitor and the 470 Ohm resistor on to the PCB

- For unattenuated CSync:
  - Populate the 100uF capacitor, short the resistor footprint with a blob of solder or 0 Ohm SMD resistor.

- For Luma as Sync:
  - Close the "Luma Sync" jumper. Do not populate any SMD component.


<img src="./Pics/pcb_after.jpg" width="600px" />

Note: When soldering the 100uF SMD cap, make sure the solder does NOT short the adjacent jumper pad.

Then, tin all the SMD pads with a good amount of solder, so you can solder metal pins onto them.

### Solder pins onto the PCB

Here is a method suggested by [Leon Kiriliuk](https://twitter.com/leonkiriliuk/status/1542005845776547842), and I find it makes a ton of sense. Unfortunately I ran out of the Saturn PCB at the time, so I used a piece of prototype board as a demonstration.

First, pick a sacrificial resistor with long legs. I bent the legs into a zigzag shape with a syringe needle, with each section about 5mm long. This will be the length we need for the pins. You could also simply mark the length with a marker pen. It's all up to you.

<img src="./Pics/pins_1.jpg" width="600px" />

Holding the resistor body, solder the end to the pad.

<img src="./Pics/pins_2.jpg" width="600px" />
<img src="./Pics/pins_3.jpg" width="600px" />

Then, cut it with a side cutter.

<img src="./Pics/pins_4.jpg" width="600px" />

Repeat the process.

<img src="./Pics/pins_5.jpg" width="600px" />

Correct any crooked pins with the needle. I find it very easy to bend and correct pins with a syringe needle. Sometimes I use this method to bend chip pins, including CPU pins.

<img src="./Pics/pins_6.jpg" width="600px" />
<img src="./Pics/pins_7.jpg" width="600px" />


-------------
## Install onto Saturn motherboard

With all the pins soldered to the PCB, we can proceed.

<img src="./Pics/pins_soldered.jpg" width="600px" />

Before trying to feed the 8-pin mini DIN socket into the 3D printed piece, bend the shielding pins on the two side slightly outwards.

<img src="./Pics/bend_pins.jpg" width="600px" />


Feed the 8-pin mini DIN socket from the front of the 3D-printed piece. For now, push it in only so that the pins on the back is flush with the hole on the back.

<img src="./Pics/not_all_the_way_in.jpg" width="600px" />

Lay the PCB on the back of the 3D printed piece. Lodge the cutout on the PCB into the sticking out piece on the left side of the shroud at an angle, then close it down so it sits inside the brackets on the right side.

<img src="./Pics/8din_insert_back.jpg" width="600px" />

Then feed the pins on the back of the 8-pin DIN through the holes on the PCB, and press the DIN port all the way in. Its rim should sit flush with the face of the piece once pushed all the way in.

<img src="./Pics/8din_insert_front.jpg" width="600px" />

If you have problems with the pins going through the vias, especially the shielding pins on the sides, use a pair of tweezers to help guiding those pins through from the gap between the PCB and the 3D printed shroud. This is why I suggested to bend the shield pins slightly outwards before hand.

Make sure everything is tightly pressed together, then solder down at least two pins onto the PCB. Keep checking if it's tight and snug. Melt the soldered pin if you have to adjust. Then, solder in the rest of the pins on the 8-pin DIN.

<img src="./Pics/8din_soldered.jpg" width="600px" />

-------------
## 10-pin mini DIN Removal

*This is my method WITHOUT using a desoldering gun. If you have a desoldering gun, feel free to proceed with your own ordinary method!*

Remelt every pin on the 10-pin DIN with some fresh solder. Push and wiggle the pins to exercise the solder inside the vias so that it's thoroughly reflowed.

Suck up as much as possible solder from each of the pins with solder wick. Wiggle the pins by pushing them around with the solder wick while heating it up with the iron to make sure you remove as much as the solder you can.

<img src="./Pics/10pin_solder_sucked.jpg" width="600px" />

Then with a pair of pliers holding the 10 pin DIN from below (but not pulling YET), blast the PCB with hot air from the top.

Wait until the solder start to melt. Then you will be able to wiggle and pull the 10-pin DIN out without too much resistance. IF you feel that you are pulling too hard and the PCB started to warp, STOP. This means your solder is not melted enough. And you will likely cause a lot of damage to the board. Be patient and give it a bit more time to melt properly.

<img src="./Pics/10din_removed.jpg" width="600px" />

Finally, clean up the bottom of the PCB with some alcohol.

-------------
## Installation

Feed the assembled 8-pin DIN through the holes on the Saturn motherboard. Be careful and patient so you don't feel the leads through wrong holes.

<img src="./Pics/8din_inserted.jpg" width="600" />

Make sure the 3D-printed piece sits tightly against the PCB. Note the front and back face of the DIN is NOT perpendicular with the PCB. This is intended. Otherwise the new 8-pin DIN port will not sit flush with the Saturn outer shell, but instead have an ugly gap.

<img src="./Pics/not_perpendicular.jpg" width="600" />

Solder in the two outside pins so the assembly is held down. You can melt them again if the assembly does not sit properly in its place. Keep adjusting until you are satisfied.

<img src="./Pics/8din_solder_shielding_pins.jpg" width="600" />

Solder in one row of the signal pins, then trim them.

<img src="./Pics/8din_solder_front_pins.jpg" width="600" />
<img src="./Pics/8din_trim_front.jpg" width="600" />

Solder in the other row of signal pins, and trim them too.

<img src="./Pics/8din_solder_back.jpg" width="600" />

And installation is finished.

-------------
## Closing Up

You can now put the Saturn back together like normal.

Note when you try to sit the motherboard back into its place, the 8-pin DIN needs a firm press so it snaps into the hole snuggly with an audible click.

<img src="./Pics/into_shell.jpg" width="600" />
<img src="./Pics/8din_outside.jpg" width="600" />

When laying the top metal shield back into its place, make sure the metal tongues sit nicely into the slots on the 3D-printed piece.

<img src="./Pics/shielding_sitting.jpg" width="600" />

With the help of the outer shell, the PCB and the metal shielding, there is no wiggle room for the new port. I expect it to be as sturdy as the original, if not better.

Enjoy your Saturn with an 8-pin mini DIN AV port!

<img src="./Pics/gallery_1.jpg" width="400px" /><img src="./Pics/gallery_2.jpg" width="400px" />

<img src="./Pics/gallery_3.jpg" width="400px" /><img src="./Pics/gallery_4.jpg" width="400px" />

<img src="./Pics/gallery_5.jpg" width="400px" /><img src="./Pics/gallery_6.jpg" width="400px" />

<img src="./Pics/gallery_7.jpg" width="400px" />

-------------
## Special Thanks
Leon Kiriliuk
Twitter: https://twitter.com/leonkiriliuk
