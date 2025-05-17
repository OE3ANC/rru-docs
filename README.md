# rru-docs

I'll put my write-ups about the setup of SP5WWPs [Remote Radio Unit](https://github.com/M17-Project/rru-rf-hw) in this repo.

This is how i built and flashed the [RRU firmware](https://github.com/M17-Project/rru-rf-fw.git), setup my Raspberry PI 4 (I didn't used the [CM4 board](https://github.com/M17-Project/rru-cm4-hw.git) for now) and built and run [cari-host](https://github.com/M17-Project/cari-host.git) on the Raspberry PI.

I used Arch Linux on my host PC and Raspberry PI OS (x64) on the Raspberry 4.

Guides:
---

#### [Build and flash the RRU firmware](build_and_flash_firmware.md)
- Connect the STLink and a USB-UART converter for debugging
- Build and Flash the RRU Firmware

---

#### [Prepare and connect the Raspberry PI](prepare_raspberry_pi.md)
- Connect the RRU to the Raspberry PIs GPIOs
- Setup the RPIs internal serial port and the user to use it

---

#### [Build and use cari host](build_and_use_cari_host.md)
- Install dependencies
- Build and install cari-host and connect to the RRU

---

Make sure to also check [M17 Project](https://m17project.org/) / [M17 Foundation](https://m17foundation.org/) for more awesome open source software and hardware!
