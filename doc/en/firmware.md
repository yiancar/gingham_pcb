# Firmware

## The easy way
- Go to [QMK Configurator](https://config.qmk.fm/#/gingham/LAYOUT_60_ansi)
- Complete the keymap to your preference
- Select `COMPILE` and once its done `FIRMWARE`
- Open [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases)
- Select the downloaded `.hex` file
- Put keyboard in bootloader mode
- Press `Flash`

## The hard way: Setup QMK Firmware
If you want to compile QMK in your host environment keep reading
- https://github.com/qmk/qmk_firmware
- https://docs.qmk.fm/#/newbs_getting_started

## Build and burn default keymap
In your qmk directory,

#### Just building firmware
```
make gingham:default
```

#### Build and burn to Gingham
After entering bootloader mode,
```
make gingham:default:program
```

#### avr-gcc version
With avr-gcc 8.2.0, you may encounter an error similar to `ERROR: address 0x8002a7 out of range at line 920 of .build/gingham_default.hex`. To work around this on macOS, install an older version of avr-gcc with homebrew,
```
brew uninstall avr-gcc
brew install avr-gcc@7
brew link --force avr-gcc@7
```
And then re-run `make gingham:default:program`.

## Test with wire
When you burn the default keymap, test without soldering switches.   
You can use any wire and short the switch pads on pcb.

## Customize keymaps
- https://docs.qmk.fm/#/newbs_building_firmware

## If you improve firmware
Send a PR!

## NEXT
[Solder switches and complete](./complete.md)
