# Ergo42

**The Answer to the Ultimate Question of Life, the Universe, and at least Keyboards.**

7x4 ortho linear split keyboard.

![Ergo42](https://raw.githubusercontent.com/Biacco42/Ergo42/readme/readme_image/ergo42_image.jpg)

_Caution! Ergo42 after version 2.0.0 is not compatible with version 1 series design. If you build Ergo42 version 1 series, please refer to the 1.x branch._

# Parts

- **2** PCB
- **2** 5V/16MHz Pro Micro compatible boards
- **56** 1N4148 (THD) or 1N4148w (SMD) diodes
- **2** [MJ-4PP-9 TRRS jacks](http://akizukidenshi.com/catalog/g/gC-06070/)
- **2** Case plate set (design available on this repo)
- **10** 5 mm (Cherry MX) / 3 mm (Kailh low profile) height M2 standoffs **(3 mm height standoffs are under verifing)**
- **8** 15 mm height M2 standoffs
- **36** 4 ~ 6 mm M2 screws (Height corresponds to your plate thickness)
- **2** 2 pin tact switch
- **56** [Switches of your choice](https://mechanicalkeyboards.com/shop/index.php?l=product_list&c=107)
- **1** TRRS / TRS cable

The screws may have a slight clearance issue with the keycaps. Use a screw with a lower profile head.

## Mount the diodes

Place the PCB as TRRS jacks on the inside, closest to one another.

- The **left PCB** will have the **TRRS jack on the right**
- The **right PCB** will have the **TRRS jack on the left**

Which side you solder the diodes on depends on your switch plate's thickness and key switch type, which is Cherry MX compatible or Kailh low profile. Acrylic plate thickness < 3 mm with Cherry MX compatibles should have diodes on the same side as the key switches. Acrylic plate thickness 2 mm with Kailh low profile switches should have diodes on the opposite side of the key switches.

**Double check your work**. Black lines (THD) / White lines (SMD) should be facing the square pad.

![diodes_01](https://raw.githubusercontent.com/Biacco42/Ergo42/readme/readme_image/ergo42_rev2_diode_from_top.jpg)

## [Optional] Mount the resistors and bridge jumper

If you want to use I2C, not UART, to comunicate with other side PCB, you should add 2.2 k ohm resistors on the left side PCB's R1 and R2 printed silk. Also bridge to short W1 pad by solder jumper on each side PCB. Usually you don't have to do this step.

## Mount the TRRS Jack and tact switch

Mount the TRRS jack and tact switch on the same side as your switches. It should be on the upper face.

## Mount the Pro Micro

Ergo42's PCB is symmetrical but Pro Micro mount is different between the left and right PCB.

- On the **left PCB** the Pro Micro's component side should be **back to PCB**.
- On the **right PCB** the Pro Micro's component side should be **face to PCB**.

![left side PCB](https://raw.githubusercontent.com/Biacco42/Ergo42/readme/readme_image/ergo42_rev2_promicro_left.jpg)

![right side PCB](https://raw.githubusercontent.com/Biacco42/Ergo42/readme/readme_image/ergo42_rev2_promicro_right.jpg)

## Mount switches

Mount switches on the acrylic plate, set PCB to fit and solder switches.  
**When you use Cherry MX compatibles with Acrylic plate thickness < 3 mm and 5 mm height stand-offs, please cut off the tip of the electricity terminal of the switch. The electricity terminal of the switch interferences with bottom plate.**

## Assemble the case

Tighten the screws with standoffs.
Some [vinyl pads](https://www.amazon.co.jp/gp/product/B00V5MQWGS/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1) may help the keyboard's stability.
Install your keycaps.

## Flash QMK Firmware

QMK firmware for Ergo42 is now available on [QMK firmware](https://github.com/qmk/qmk_firmware).
This document doesn't cover how to build QMK. Prease refer to [QMK documents](https://docs.qmk.fm/).

Connect the keyboard by USB cable to a PC and run

```
$ make ergo42/rev1:default:avrdude
```

on the left and right side keyboard individually.

It will build and try to flash your firmware. Follow the instructions that require to reset the Pro Micro.

This process may require privileges. If you have some `Permission denied` error, please try

```
$ sudo make ergo42/rev1:default:avrdude
```

## All done!
