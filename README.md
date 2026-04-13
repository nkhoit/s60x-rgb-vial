# Sentraq S60-X RGB — VIAL Firmware

VIAL-enabled QMK firmware for the Sentraq S60-X RGB keyboard PCB.

This board never had VIA or VIAL support. Now it does.

## Quick Start

1. Download `s60x_rgb_vial.hex`
2. Flash with [QMK Toolbox](https://github.com/qmk/qmk_toolbox) (MCU: ATmega32U4, reset button on back of PCB)
3. Download [VIAL](https://get.vial.today) — works on Windows, macOS, and Linux
4. Plug in the keyboard — VIAL auto-detects it, no configuration files needed
5. Remap keys live

## Files

| File | Description |
|------|-------------|
| `s60x_rgb_vial.hex` | Pre-compiled firmware, ready to flash |
| `keymap.c` | QMK keymap source (3 layers) |
| `rules.mk` | QMK build rules |
| `config.h` | VIAL configuration (UID, unlock combo, layer count) |
| `vial.json` | VIAL keyboard definition (compiled into firmware) |

## Features

| Feature | Status |
|---------|--------|
| VIAL live remapping | ✅ |
| 3 layers | ✅ |
| EXTRAKEY (media keys) | ✅ |
| NKRO (full key rollover) | ✅ |
| BOOTMAGIC (Esc = EEPROM reset) | ✅ |
| Tap Dance (configurable in VIAL) | ✅ |
| Combos (configurable in VIAL) | ✅ |
| RGB underglow | ❌ (disabled to save flash) |
| Per-key backlight | ❌ (disabled to save flash) |

Firmware size: 28,008 / 28,672 bytes (97%)

## Default Layout

- **Layer 0:** Standard ANSI with split backspace
- **Layer 1:** Function layer (F1-F12, media, navigation)
- **Layer 2:** Empty (configure via VIAL)

## Building From Source

Requires [vial-qmk](https://github.com/vial-kb/vial-qmk) (not regular QMK):

```bash
git clone https://github.com/vial-kb/vial-qmk
cd vial-qmk

# Copy keyboard files from QMK
cp -R /path/to/qmk_firmware/keyboards/sentraq keyboards/

# Copy the vial keymap files into keyboards/sentraq/s60_x/rgb/keymaps/vial/
# Then compile:
make sentraq/s60_x/rgb:vial
```

## Hardware

- **PCB:** Sentraq S60-X RGB (ATmega32U4, atmel-dfu bootloader)
- **Sold via:** Massdrop/Drop (~2017, discontinued)
- **Vendor/Product ID:** 0x5351:0x6060
- **VIAL unlock combo:** Esc + Backspace

## Notes

- This is for the **RGB** version only. The non-RGB S60-X has a different matrix.
- Sentraq is defunct. This firmware is a community contribution.
- RGB underglow was disabled to fit VIAL + all features in the 28KB flash limit.
  If you want RGB back, disable TAP_DANCE and COMBO in `rules.mk`.
