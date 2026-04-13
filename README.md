# Sentraq S60-X RGB — VIA Firmware

VIA-enabled QMK firmware for the Sentraq S60-X RGB keyboard PCB.

This board never had VIA support. Now it does.

## Quick Start

1. Download `s60x_rgb_via.hex`
2. Flash with [QMK Toolbox](https://github.com/qmk/qmk_toolbox) (MCU: ATmega32U4, reset button on back of PCB)
3. Open [VIA](https://usevia.app) → Settings → enable "Show Design Tab"
4. Design tab → Load Draft Definition → select `s60x_rgb_via_definition.json`
5. Go to Configure → remap keys live

## Files

| File | Description |
|------|-------------|
| `s60x_rgb_via.hex` | Pre-compiled firmware, ready to flash |
| `s60x_rgb_via_definition.json` | VIA keyboard definition (load in Design tab) |
| `keymap.c` | QMK keymap source (4 layers, LAYOUT macro) |
| `rules.mk` | QMK build rules (`VIA_ENABLE = yes`) |

## Default Layout

- **Layer 0:** Standard ANSI with split backspace
- **Layer 1:** Function layer (F1-F12, media, navigation)
- **Layers 2-3:** Empty (configure via VIA)

## Building From Source

```bash
# Copy keymap.c and rules.mk to:
# qmk_firmware/keyboards/sentraq/s60_x/rgb/keymaps/via/

qmk compile -kb sentraq/s60_x/rgb -km via
```

Compiled size: 26,812 / 28,672 bytes (93%)

## Hardware

- **PCB:** Sentraq S60-X RGB (ATmega32U4, atmel-dfu bootloader)
- **Sold via:** Massdrop/Drop (~2017, discontinued)
- **Vendor/Product ID:** 0xFEED:0x6060

## Notes

- This is for the **RGB** version only. The non-RGB S60-X has a different matrix.
- The VIA definition uses the `LAYOUT` macro (65 keys) which supports split backspace and split right shift configurations.
- Sentraq is defunct. This firmware is a community contribution.
