# Cobra-19XS-VFO-DDS-VFO

ESP32-based digital VFO, meter, and menu firmware for a Cobra 19XS-style radio.

## What’s included

- Flashable PlatformIO project
- ESP32 Arduino firmware in `src/main.cpp`
- Dual OLED support:
  - 128x64 main frequency screen
  - 128x32 Cobra-style meter screen
- Separate preview/status screen for quick-glance frequency and mode info
- Encoder menu, memory slots, meter modes, and voltage calibration

## Project layout

- `platformio.ini` — build configuration
- `src/main.cpp` — firmware source
- `main code` — legacy source snapshot from the original upload

## Flashing

1. Open the folder in VS Code with PlatformIO installed.
2. Select the `esp32dev` environment.
3. Build and upload.

Command line:

```bash
pio run
pio run -t upload
```

## Screen preview

### Main screen

```text
27.000.000 MHz
AM   RX
^ step underline moves with the selected tuning step
```

### Meter screen

```text
S/RF
S1  S3  S5  S7  S9  +10  +20  +30
pixel-dotted Cobra 148 GTL-style meter face
```

### Preview screen

```text
STATUS     RX
FREQ 27.000 MHz
MODE AM STEP 1k
```

## Controls

- Short press encoder: cycle tuning step
- Long press encoder: open menu
- Encoder rotation: tune or navigate menus
- Long press from main screen: toggle meter invert
- Meter mode, brightness, invert, and voltage calibration are in the Meter menu

## Wiring notes

- Si5351 CLK0 -> radio mixer/VFO injection point
- GPIO35 -> audio/S-meter tap
- GPIO34 / GPIO26 -> PTT detect/key
- GPIO36 -> voltage divider input
- Shared ground is required

## Notes

- This firmware is written for an ESP32 Dev Module target.
- The voltage input must be scaled with a proper divider before connecting to GPIO36.
- Radio modifications should only be done by experienced users.
