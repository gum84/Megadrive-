## Welcome to the MegaDrivePlusPlus wiki!

**MegaDrivePlusPlus** is a modchip for the **Sega Mega Drive** (AKA **Sega Genesis**). It has the following features:
- **EUR/USA/JAP mode switching**: this effectively **makes your console universal**, allowing it to **bypass region checks** and to **run all games** without resorting to an adapter.
  - If you come from a PAL region, you will also be able to **run most games at 60 Hz**, which means **full-speed** and **full-screen**! Get rid of those **black bars**! See the difference [here](https://youtu.be/X1CW8Da8i1o)!
  - The mod is **switchless**, so you don't need to modify the aesthetics of your console installing ugly switches, but rather you will be able to change the region:
    - Through the **Reset button: Keep pushed** to cycle through modes.
    - From the Player 1 controller pad: Press **Start + B + Up/Down** to cycle through modes or **Start + Down/Left/Right** to set a certain mode (according to the actual chip you have installed, more on this below).
  - The last used mode is saved automatically after 5 seconds and reused at power up.
  - Supports a single led, common-anode or common-cathode dual or RGB LEDs to indicate the current mode (Colors can be set to any value when PWM pins are available).
- **Reset-From-Pad** (AKA **In-Game-Reset** AKA **IGR**): Press **Start + A + B + C**.
  - Supports consoles with both active-high and active-low reset signals by
autosensing (i.e.: **all console revisions**!).
- Uses **cheap *Atmel AVR* microcontrollers**.
  - Can be **flashed on different chips** (ATtiny's, ATmega's, or **even a full
Arduino** board), but please note that **not all features are supported on all chips**, depending on
the number of available I/O pins, please read on for details.
  - If flashed on an ATtinyX4(A), it is **pin-to-pin compatibile with the _D4s/Seb mod_**.
- Even though default settings are recommended, **everything can be customized** to taste.
- Uses the popular **Arduino environment**, allowing for easy development, testing and modifications.
- Last but not least, it is **Open Source and Free Software**!


If you are interested to mod your console with MegaDrive++, please proceed to the [[Installation]] page!