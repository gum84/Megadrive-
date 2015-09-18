Installation involves a few steps:

1. First of all, you need to get ahold of a supported chip flashed with the firmware. You can do this yourself following [[the instructions|Chip Preparation]] or ask someone else with some knowledge of the Arduino platform to do it for you. Keep the [[diagram for your chosen chip|Choosing a microcontroller]] at hand.

2. Open up your Mega Drive/Genesis and identify the logic board model: look at what is printed on it and get the diagram for your model below:

  * [[IC BD M5 PAL|Installation on IC BD M5 PAL]]
  * [[IC BD M5 PAL VA4|Installation on IC BD M5 PAL VA4]]
  * [[Mega Drive 2|Installation on Mega Drive 2]]

  If your model is not listed, please open an issue providing high resolution photos of both sides of your logic board, and we will try to help.

  Keep the logic board diagram at hand.

3. All logic boards need a couple of tracks on the PCB to be cut. Use a razor blade and/or a sharp cutter and keep cutting until you get to the white layer. Be aware not to touch nearby tracks! Use a multimeter to check that you have really interrupted the electrical connection.

4. Using the chip and the logic board diagrams, solder wires between them. You are recommended to use a socket for the chip, allowing for easy updates.

  There are two sets of wires to be soldered:

  * The first one uses the same points as the D4s/Seb mod (which is why we use their diagrams). The wires must be soldered between the colored points on the logic board diagram and the pins indicated in the chip diagram, according to the following key:

    | Color   | Signal             |
    | ------- | ------------------ |
    | Red     | +5V                |
    | White   | Ground             |
    | Orange  | Reset In           |
    | Aqua    | Reset Out          |
    | Yellow  | JP1/2 (Language)   |
    | Green   | JP3/4 (Video Mode) |
    | Purple  | Led Color 1        |
    | Blue    | Led Color 2        |

  * The second set of wires goes between the chip and the Player 1 controller port. This time use your chip diagram and [[this reference|Controller Pad Port Pinout]].

5. Finally, test and reassemble your console! Note that will probably have to **use an RGB cable to get the new modes to display correctly** on your TV. I recommend getting one from [retro gaming cables](https://www.retrogamingcables.co.uk/games-consoles/sega): they might not be the cheapest, but they are very high quality and will give you the best possible video!