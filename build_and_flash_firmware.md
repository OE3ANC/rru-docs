## Flashing the firmware
### Connect the RRU to your PC

I'm using 2 devices to connect to my RRU for now:
- USB-UART for the debug output (PINs DTX / DRX on the RRU)
- STLink for flashing and debugging via SWD

How i connected them:

| USB-UART | RRU |
| -------- | --- |
| TXD      | DRX |
| RXD      | DTX |
| GND      | GND |

I connected to the debug console with picocom:
```bash
picocom -b 460800 --imap lfcrlf /dev/ttyUSB0
```

You can quit picocom with ctrl-a, ctrl-x

| STLink        | RRU   |
| ------------- | ----- |
| GND           | GND   |
| RST           | nRST  |
| SWDIO         | SWDIO |
| SWCLK         | SWCLK |
| NOT CONNECTED | U_MCU |

I haven't connected U_MCU as i'm powering the MCU with the RRUs internal PSU

My first attempts to connect to SWD with a ST-Link from a nucleo board failed. I ended up ordering a cheap ST-Link "stick" from the internet which worked without problems. I'm not sure what was the problem with the one of the nucleo board, maybe it's just broken.

### Build and flash the firmware

Install the STM32CubeIDE and STM32CubeProgrammer. Open the [rru-rf-fw](https://github.com/M17-Project/rru-rf-fw) project in STM32CubeIDE and build it (Project -> Build all).

Then open the STM32CubeProgrammer, connect to the ST-Link, select "Erase & Programming", select built firmware (rru-rf-fw/Release/rru-rf-fw.bin) and press Start Programming. These are the options i've used:

![[STM32CubeProgrammer.png]]

On the debug console, you should see this output, if you've checked "Run after programming":

```
Remote Radio Unit (RRU) 420-450 MHz  
FW v1.0.0 by Wojciech SP5WWP  
RX IC: CC1200  
TX IC: CC1200  
Starting TRX config... done  
RX PLL locked  
TX PLL locked
```

