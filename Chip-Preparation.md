1. Download the Arduino IDE and install it.
2. If you are targeting an ATtiny chip, download ATTinyCore, install it and make sure it shows up under Boards in your Arduino IDE.
3. **Close** the Arduino IDE.
3. **Download** the _MegaDrivePlusPlus_ sketch and save it in a directory with the same name in your Arduino sketch folder.
3. **Open** the Arduino IDE.
4. **Connect** your chip as an ICSP target.
5. **Set** the following options in the _Tools_ menu:
   * Board: ATtiny x4 Series
   * B.O.D.: B.O.D. Enabled (4.3v)
   * Clock: 8 MHz (Internal)
   * Chip: ATtiny84
   * Port: Choose whatever port you connected your programmer to.
6. **Select** **Burn Bootloader** from the _Tools_ menu. Wait for the _Done burning bootloader_ message to appear.
7. **Select** Open... from the File menu and open the _MegaDrivePlusPlus_ sketch 
8. **Select** _Upload Using Programmer_ from the _Sketch_ menu.

If no errors show up, your chip is ready!