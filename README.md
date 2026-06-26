# Flipper Blinker

Flipper Blinker is a Flipper Zero external app that sends text as Morse code through an LED connected to GPIO pin PC3.

It is meant for a simple external LED circuit:

```text
PC3 -> 220 ohm resistor -> LED anode / long leg
LED cathode / short leg -> GND
```

The app does not try to detect whether an LED is connected. Use the built-in blink test in Setup and confirm it yourself.

## Features

- Text input using the normal Flipper keyboard
- Morse output for A-Z, 0-9, and spaces
- Adjustable speed from 5 to 40 WPM
- Optional repeat mode
- Repeat delay from 1 to 300 seconds
- Setup blink test for checking the wiring
- Settings saved on the Flipper SD card

## Hardware

Parts:

- 1 LED
- 1 220 ohm resistor
- Jumper wires

Wiring:

```text
Flipper PC3 ---- 220 ohm resistor ---- LED long leg
LED short leg ------------------------ GND
```

If the LED does not blink during Setup, check polarity first. The long leg goes toward PC3. The short leg goes toward GND.

## Build

Place this folder in the official firmware tree:

```text
flipperzero-firmware/applications_user/FlipperBlinker
```

From the firmware root, build the app:

```powershell
.\fbt.cmd fap_flipper_blinker
```

The built app will be written to:

```text
build/f7-firmware-D/.extapps/flipper_blinker.fap
```

## Install And Launch

With the Flipper connected over USB:

```powershell
.\fbt.cmd launch APPSRC=applications_user\FlipperBlinker
```

This uploads the app to:

```text
/ext/apps/GPIO/flipper_blinker.fap
```

and launches it.

## Usage

Open Flipper Blinker and choose:

- `Setup` to run the five-blink wiring test
- `Send Message` to enter text and transmit it
- `Settings` to adjust speed, repeat, repeat delay, and view the LED pin
- `About` for version and app info

During transmission, press Back to stop immediately.

## Morse Timing

The app uses standard Morse timing:

- Dot: 1 unit
- Dash: 3 units
- Gap between symbols: 1 unit
- Gap between letters: 3 units
- Gap between words: 7 units

At the default 15 WPM, one unit is 80 ms.

## Notes

- Only PC3 is exposed in the current UI.
- The GPIO code is separated so other pins can be added later.
- Do not connect an LED directly to PC3 without a resistor.

## Credits

Made by T3chieJack.
