# Delarion

### A custom CoreXY 3D printer: the best bang for your buck

![Delarion render](https://github.com/user-attachments/assets/610b3218-75e4-4d01-9691-6848fe283e0e)

Delarion is a CoreXY 3D printer designed to deliver near-premium performance without a premium price. It is built on a rigid **2020 aluminum extrusion** frame, with **ball screws** and **linear rails** for smooth, accurate motion, and runs **Klipper** on a custom **ESP32-S3** control board.

> **Status:** Design / pre-build. Submitted to Hack Club Stardance for funding.

[![View PCB on KiCanvas](https://hack.club/pcb-badge)](https://kicanvas.org/?repo=https://github.com/Kishna-Jain/Delarion/tree/main/PCB) [![View BOM](https://img.shields.io/badge/View-BOM-green)](BOM.csv) [![3D Model](https://img.shields.io/badge/CAD-Onshape-orange)](https://cad.onshape.com/documents/ddc5642abc531e1225c0dc8b/w/1fb68ecf66842d529f7141f3/e/0a949859a3af9baaf41af0a4)

---

## Table of Contents

1. [Why Delarion?](#why-delarion)
2. [Highlights](#highlights)
3. [Specifications](#specifications)
4. [Motion System](#motion-system)
5. [Electronics and Firmware](#electronics-and-firmware)
6. [Custom PCB](#custom-pcb)
7. [3D Model](#3d-model)
8. [Bill of Materials](#bill-of-materials)
9. [Repository Structure](#repository-structure)
10. [Build Notes](#build-notes)
11. [Roadmap](#roadmap)
12. [Credits](#credits)

---

## Why Delarion?

Every maker eventually gets the urge to build random nerdy things from YouTube tutorials. I went down that road too, but without a 3D printer the workarounds get messy, and the final result lacks finesse: a pile of scraps in a makeshift enclosure. We've all been there.

So I went shopping for a cheap printer, and the results weren't great. Printers now start around $100 USD, but most of those are disappointing, and there is little reason to buy an Ender 3 today when almost everything is better. Bambu Lab is an option, and some budget machines exist, but still nothing fully satisfying. In my area, a *good* printer costs about **$500**, while the cheap ones are just cheap.

So the quest began: **build my own.** Delarion is the result.

## Highlights

- **CoreXY kinematics** for fast, light-toolhead motion
- **2020 aluminum extrusion frame**, sturdy, rigid and easy to source
- **Ball screws and linear rails** for smooth, precise, quiet movement
- **Klipper firmware** running on a host computer for high speed and advanced features
- **ESP32-S3 main MCU**, with Wi-Fi/BLE and plenty of room for experiments
- **TMC2208 stepper drivers** for quiet operation
- **MPU6050 accelerometer on the board** for input shaping / resonance tuning
- **Fully custom PCB**, designed from scratch

## Specifications

| Item | Detail |
|---|---|
| Kinematics | CoreXY |
| Frame | 2020 aluminum extrusion |
| Linear motion | Linear rails |
| Z motion | Ball screws |
| Motors | NEMA 17 steppers |
| Stepper drivers | TMC2208 |
| Main MCU | ESP32-S3 |
| Firmware | Klipper |
| Host | Raspberry Pi or any spare laptop/PC |
| Input power | 24 V clean DC supply |
| Logic power | 5 V external, 3.3 V regulated on-board (AMS1117-3.3) |
| Input shaping sensor | MPU6050 |
| Build volume | _TBD_ |
| Max speed / acceleration | _TBD_ |
| Hotend / extruder | Standard hotend and extruder (see `BOM.csv`) |
| Estimated cost | ~₹37,500 (~$390), see `BOM.csv` |

<!-- TODO: fill in the TBD rows as the design is finalised -->

## Motion System

CoreXY moves the toolhead in X and Y using two fixed motors and a crossed belt path. Because the motors are stationary, the moving mass is small, which allows higher accelerations and cleaner prints than a traditional bed slinger.

- **X/Y:** two NEMA 17 motors driving a CoreXY belt layout on linear rails
- **Z:** ball screws for precise, repeatable vertical motion
- **Bed motion:** designed around the mechanism explained in MistsuMakes' tutorials (see [Credits](#credits))

New to CoreXY? [3ddistributed.com](https://3ddistributed.com) has the best infographics for understanding how the belt path works.

## Electronics and Firmware

### Why Klipper?

1. **Speed:** Klipper offloads heavy computation to a host microprocessor, giving a huge speed advantage over firmware that runs everything on the MCU.
2. **Accessibility:** Everyone has an old laptop or a Raspberry Pi lying around, so no expensive controller is needed.
3. **Documentation:** Klipper's docs are excellent and thorough.

### Why ESP32-S3?

It is cheap, powerful, and has built-in wireless, which opens up endless possibilities for experimenting with new features.

### Software stack

- Klipper (firmware on MCU, host software on Pi/PC)
- Moonraker (API) and a web UI such as Mainsail or Fluidd _(recommended)_

<!-- TODO: add printer.cfg and Klipper MCU build/flash instructions -->

## Custom PCB

A deliberately simple custom board built around the ESP32-S3.

![Delarion Klipper MCU PCB](https://github.com/user-attachments/assets/056f84d5-a3d5-4a0c-85c6-29b3c66b95aa)

**On board:**

- ESP32-S3 MCU
- TMC2208 stepper drivers
- MPU6050 accelerometer
- AMS1117-3.3 regulator for the 3.3 V logic rail
- IRLZ44N MOSFET(s) for heater/fan switching

> **Key notes**
>
> - **Power:** the board needs a **clean 24 V supply**. Poor-quality power will cause problems.
> - **External 24 V and 5 V:** the XL103 step-down converter is **not mounted on the PCB** because it produces too much heat. Provide clean 24 V and 5 V from an external converter to the designated pins, with **active cooling** on the converter.
> - **3.3 V rail:** regulated on-board by an AMS1117-3.3.
> - **Driver cooling:** fit heatsinks and active cooling to the TMC2208/2209 drivers, otherwise the risk of damage is high.
> - **Designed in KiCad 10.**
> - **IRLZ44N placement:** mount the IRLZ44N on the **bottom** of the board, **not the top**.
> - **Honest disclaimer:** this is my first PCB. It isn't beautiful or well laid out, but it works, or at least that's what I'm hoping for. Revisions are expected.

[![View PCB on KiCanvas](https://hack.club/pcb-badge)](https://kicanvas.org/?repo=https://github.com/Kishna-Jain/Delarion/tree/main/PCB)

<!-- TODO: add schematic PDF, Gerbers, and pinout table -->

## 3D Model

Explore the full CAD model on Onshape:

**[Open in Onshape](https://cad.onshape.com/documents/ddc5642abc531e1225c0dc8b/w/1fb68ecf66842d529f7141f3/e/0a949859a3af9baaf41af0a4)**

## Bill of Materials

The full BOM with supplier links is in [`BOM.csv`](BOM.csv). Estimated total: **~₹37,500 (~$390 USD)**, which keeps Delarion well under the ~$500 price of a comparable ready-made printer.

> Prices are approximate and use an assumed rate of 1 USD ≈ 95.9 INR (mid-September 2026). Suppliers are mostly Indian: Robu, Robokits, OnlyScrews, Amazon.in and local shops.

Main parts: 2020 aluminum extrusion frame, MGN12H linear rails, ball screws for Z, 4× NEMA 17 steppers, GT2 belts and pulleys, the custom ESP32-S3 PCB with TMC2208/2209 drivers, 24 V SMPS, heated bed, hotend and extruder.

## Repository Structure

```
Delarion/
├── README.md
├── BOM.csv
├── assets/        # images used in this README
├── CAD/           # full assembly (.step) and printable parts
├── PCB/           # KiCad project files
└── firmware/      # Klipper printer.cfg and flashing notes
```

## Build Notes

- Square the frame carefully; a rigid, square frame matters more than anything else for print quality.
- Keep belt tension equal on both CoreXY belts.
- Double-check PCB orientation of polarised parts and the IRLZ44N mounting side before powering on.
- Test the board with motors disconnected first, then add components one at a time.
- Run input shaping calibration using the on-board MPU6050 once the machine is assembled.

## Roadmap

- [x] CAD design
- [x] First PCB design
- [ ] Full CAD assembly STEP, Klipper config and firmware notes added to repo
- [ ] Order parts (pending Stardance funding)
- [ ] Frame and motion assembly
- [ ] PCB bring-up and Klipper configuration
- [ ] First print
- [ ] Input shaping and tuning
- [ ] PCB revision 2
- [ ] Full documentation and BOM

## Credits

This project wouldn't exist without a lot of people:

- **[Hack Club](https://hackclub.com):** this project was only possible because of them. They helped me find the right people and pushed me to go build my dream.
- **Stardance:** I'm submitting this project for funding, fingers crossed!
- **@RaygunRupe:** I was going to buy parts and figure it out on the fly. The only reason I went this deep into design and polish is because of this guy. Otherwise I'd have skipped the CAD work and made a mess.
- **MistsuMakes (YouTube):** his tutorials taught me how the motion system and the bed mechanism work. His video is what made me decide, "yeah, let's do it, I can make this too."
- **[3ddistributed.com](https://3ddistributed.com):** probably the best site for understanding how CoreXY works. After countless tutorials, its infographics finally made it click.
- **The Slack hardware community:** they helped me figure out how all of this works and connected me with people who helped me build it.
