Follow these instructions to prepare your own modchip. If you are targeting a bare ATtiny chip you will need an ICSP programmer, or you can use an Arduino board following the instructions at https://www.arduino.cc/en/Tutorial/ArduinoISP.

1. **Download the Arduino IDE** (latest stable version from https://www.arduino.cc/en/Main/Software) and install it.
2. If you are targeting an ATtiny chip, **download ATTinyCore** from https://github.com/SpenceKonde/ATTinyCore, install it and make sure it shows up under Boards in your Arduino IDE.
3. **Close** the Arduino IDE.
3. **Download the _MegaDrivePlusPlus_ sketch** and save it in a directory with the same name in your Arduino sketch folder.
3. **Open** the Arduino IDE.
4. **Connect** your chip through the ICSP programmer and select the programmer type under _Programmer_ in the _Tools_ menu.
5. **Set** the following options in the _Tools_ menu:
   * Board: _ATtiny x4 Series_
   * B.O.D.: _B.O.D. Enabled (4.3v)_
   * Clock: _8 MHz (Internal)_ **BE VERY CAREFUL WITH THIS!**
   * Chip: _ATtiny84_
   * Port: Choose whatever port you connected your programmer to.
6. **Select** **Burn Bootloader** from the _Tools_ menu. Wait for the _Done burning bootloader_ message to appear.
7. **Select** _Open..._ from the File menu and open the _MegaDrivePlusPlus_ sketch 
8. **Select** _Upload Using Programmer_ from the _Sketch_ menu.

If no errors show up, your chip is ready!