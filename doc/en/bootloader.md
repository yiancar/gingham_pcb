# Bootloader

This project uses the USBaspLoader as USB bootloader.
- https://www.obdev.at/products/vusb/usbasploader.html
- HSGW's customized bootloader (as used in the Plaid)   
  - https://github.com/hsgw/USBaspLoader/tree/plaid
  - When you burn bootloader to raw ATMEGA328p, don't forget write fuse bits.

## If you buy a kit, the bootloader is already burned in the ATMEGA328p.

## Windows
Needs device drivers.   
You can use zadig and install ```libusbK```.
- https://zadig.akeo.ie/
- https://sparks.gogo.co.nz/usbasp_drivers.html

## Enter bootloader mode
1. Plug into USB cable
2. Push and hold ```RESET``` SW
3. Push and hold ```BOOT``` SW
4. Release ```RESET``` SW
5. Release ```BOOT``` SW

If you enter bootloader mode successfully, you will see ```usbasp``` in device manager.

## In case the bootloader is not recognized
- Check components and soldering near ATMEGA328p.
  - Direction of ATMEGA328p
  - BOOT SW and RESET SW
  - USB connector
  - R1,R2,R3,D15,D16

- Try a different USB cable, PC, USB hub
  - If you are connecting via USB hub, try directly.

## Test with avrdude
After the pcb is in bootloader mode and recognized as ```USBasp```, run this command in terminal.   
If you don't setup QMK Firmware, please read [firmware.md](./firmware.md) in this build guide.

```
avrdude -c usbasp -p m328p
```

If everything goes smoothly the output will be:

```
$ avrdude -c usbasp -p m328p
avrdude.exe: AVR device initialized and ready to accept instructions
Reading | ################################################## | 100% 0.00s
avrdude.exe: Device signature = 0x1e950f (probably m328p)
avrdude.exe done.  Thank you.
```

## NEXT
[Build and burn QMK Firmware](./firmware.md)