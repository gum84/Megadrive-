## Welcome to the MegaDrivePlusPlus wiki!

**MegaDrivePlusPlus** is a modchip for the **Sega Mega Drive** (AKA **Sega Genesis**) that enables IGR (*In-Game-Reset*), and 50/60 Hz and Language switching in a... switchless fashion.

## Features
- **Reset-From-Pad** (AKA **In-Game-Reset** AKA **IGR**): Press **Start + A + B + C**.
  - Supports consoles with both active-high and active-low reset signals by
autosensing.
- **EUR/USA/JAP mode switching**:
  - Through Reset button: Keep pushed to cycle through modes.
  - From pad: Press **Start + B + Left/Right** to cycle through modes or **Start + Down/Left/Right** to set a certain mode.
  - The last used mode is saved after 5 seconds and reused at power up.
  - Supports a single led, common-anode or common-cathode dual or RGB LEDs to indicate the current mode (Colors can be set to any value when PWM pins are available).
- Uses **cheap *Atmel AVR* microcontrollers**.
  - Can be **flashed on different chips** (ATtiny's, ATmega's, or **even a full
Arduino** board), but please note that **not all features are supported on all chips**, depending on
the number of available I/O pins, please read on for details.
  - If flashed on an ATtiny84, it is **pin-to-pin compatibile with the _D4s/Seb mod_**.
- Last but not least, Even though default settings are recommended, **everything can be customized** to taste.


Use the links on the right to browse among the available pages!