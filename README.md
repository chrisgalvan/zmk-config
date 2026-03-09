# Kyria Rev2 ZMK Configuration

My custom configuration for the Kyria Rev2 ergonomic split keyboard. This repository contains the ZMK firmware configuration, keymaps, and device tree overlays.

## Hardware

- **Keyboard**: Kyria Rev2 (ergonomic split keyboard)
- **Microcontroller**: Nice Nano v2 (on left and right halves)
- **Wireless Receiver**: XIAO BLE (Prospector adapter) - acts as a wireless dongle
- **Display**: Nice View displays on both halves with fixed brightness (80%)
- **Connectivity**: Bluetooth Low Energy

The dongle/receiver approach improves battery life of the peripheral halves by handling the wireless communication independently.

## Keymaps

### Default Layer (QWERTY)
Standard QWERTY layout with modifier keys and layer access:
- **Mods**: ESC, Tab, Shift, Ctrl, Alt, GUI
- **Layer Access**: Mo1 and Mo2 for Nav and Num layers
- **Special**: Backtick, Enter, Space, Backspace

### Nav Layer
Navigation and window management:
- **Arrow Keys**: Up, Down, Left, Right
- **Window Management**: CMD+Left/Right, Alt+Left/Right for app/window switching
- **Ctrl+Up/Down**: Jump between paragraphs/blocks

### Num Layer
Numbers and special characters:
- **Numbers**: 0-9 arranged in standard calculator layout
- **Symbols**: !, @, #, $, %, ^, &, *
- **Parentheses**: ( and )

## Build Configuration

The `build.yaml` includes configurations for:
- **Left Split** (nice_nano_v2 + kyria_rev2_left + nice_view)
- **Right Split** (nice_nano_v2 + kyria_rev2_right + nice_view)
- **Dongle** (xiao_ble + kyria_rev2_dongle + prospector_adapter)
- **Settings Reset** configurations for both main and dongle boards

## Configuration Details

### Enabled Features
- **Displays**: ZMK OLED display support enabled
- **Bluetooth**: Experimental BLE features enabled for better connectivity
- **TX Power**: TX power set to +8 dBm for improved range
- **Fixed Brightness**: Prospector fixed brightness at 80%

### Device Modules
- [ZMK Firmware](https://github.com/zmkfirmware/zmk) - Main firmware
- [Prospector ZMK Module](https://github.com/carrefinho/prospector-zmk-module) - Dongle support
- [Nice View Battery](https://github.com/infely/nice-view-battery) - Battery display support

## Building

The firmware builds are orchestrated via GitHub Actions using the configurations in `build.yaml`. Custom builds can be generated using the ZMK CLI.

## Directory Structure

```
config/
├── kyria_rev2.keymap          # Main keymap definition
├── kyria_rev2.conf            # Firmware configuration
├── west.yml                   # West manifest for dependencies
└── boards/shields/kyria/      # Shield definitions and overlays
    ├── kyria_rev2_left.overlay
    ├── kyria_rev2_right.overlay
    └── kyria_rev2_dongle.overlay
```