# DOS/86

An 8086 PC emulator for [PicoDeck](https://picodeck.net) on the ClockworkPi
PicoCalc, based on [Fake86](https://github.com/mikechambers84/fake86) by Mike
Chambers. It boots DOS from floppy disk images, with the PC speaker and
AdLib (OPL2) sound.

## Using it

1. Put floppy images (`.img`) in `/data/dos86/disks/` on the SD card. The app
   creates the folder on its first run and lists what it finds there.
2. Start DOS/86 and choose a disk: Up and Down to move, Enter to boot it, Esc
   to cancel.
3. The PicoCalc's keyboard is the PC's. To leave, open the system menu and
   choose **Exit App**.

## Install

From the **App Store** on the device (firmware 0.7.0 or later), or copy the
files listed in `files.txt` to `/apps/dos86/` on the SD card.

## Building

It is a native PicoDeck app (an ELF32 PIE). With the ARM toolchain
(`arm-none-eabi-gcc` and newlib) installed, `make` builds `main.elf` and `make zip`
builds the release zip from `files.txt`, as CI does. A tag `v<version>`
matching `app.json`'s version publishes it as a release, which the PicoDeck
store lists.

`sdk/native/` is a copy of the PicoDeck SDK headers it builds against (from
the [PicoDeck repository](https://github.com/PicoDeck/picodeck)'s
`sdk/native/`). Update them from there when the app needs a newer API.

The app was part of the PicoDeck repository until version 0.1.0; its history
came with it.

## Licence

DOS/86 is free software under the GNU General Public License, version 2 or
(at your option) any later version: see `COPYING`. Fake86 is Copyright (C)
2010-2013 Mike Chambers. The ROMs in `roms/` are the ones Fake86 is
distributed with.
