Follow these instructions to prepare your own modchip. If you prefer getting a chip that is ready to install, contact me. If I get enough requests I might start selling pre-flashed chip + leds for a nominal fee.

1. **Download the Arduino IDE** (latest **stable** version from https://www.arduino.cc/en/Main/Software) and install it.
3. **Download the MegaDrive++ sketch** and save it in a directory with the same name in your Arduino sketch folder. If you have no such folder, run the Arduino IDE once and it will be created.
4. **Select _Open_** from the _File_ menu and navigate to where you saved MegaDrive++.

From this point on, instructions vary depending on what board/chip you are targeting:

## Full Arduino Board

This procedure is very easy to carry out. Actually, it takes more time to read through it than to run it! One of the reasons why I maintain an Arduino target is to enable anyone to program their own chips, even people who have never programmed a chip before: most Arduinos can be connected to the computer with a simple USB cable, so everything is pretty straightforward.

5. Make sure that the type of board in the _Tools_ menu corresponds to the actual board you are using.
6. **Connect your board** through USB.
7. **Select _Upload_** from the _Sketch_ menu.

If no errors show up, your board is ready!

## Stand-alone ATtiny chip

If you are targeting a bare ATtiny chip you will need an ICSP programmer, or you can use an Arduino board following the instructions at https://www.arduino.cc/en/Tutorial/ArduinoISP.

2. **Install ATTinyCore**: just go to https://github.com/SpenceKonde/ATTinyCore/blob/master/Installation.md and follow the instructions under *Board Manager Installation*. Make sure it shows up under *Boards* in your Arduino IDE.
4. **Connect your chip** through the ICSP programmer and **select** the right programmer type under _Programmer_ in the _Tools_ menu.
5. **Select** the right type of chip under _Board_ in the _Tools_ menu and **set** the following options:
   * Board: _ATtiny XX Series_ (Depending on the actual chip you are using)
   * B.O.D.: _B.O.D. Enabled (4.3v)_
   * Clock: _8 MHz (Internal)_ **BE VERY CAREFUL WITH THIS!**
   * Chip: Choose the actual chip you are using
   * Port: Choose whatever port you connected your programmer to.
6. **Select _Burn Bootloader_** from the _Tools_ menu. Wait for the _Done burning bootloader_ message to appear.
8. **Select _Upload Using Programmer_** from the _Sketch_ menu.

If no errors show up, your chip is ready!