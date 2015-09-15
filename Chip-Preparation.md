1. Download the Arduino IDE and install it.
2. If you are targeting an ATtiny chip, download ATTinyCore, install it and make sure it shows up under Boards in your Arduino IDE.
3. Open the Arduino IDE.
4. Connect your chip as an ICSP target.
5. Set the following options in the _Tools_ menu:
   * Board: ATtiny x4 Series
   * B.O.D.: B.O.D. Enabled (4.3v)
   * Clock: 8 MHz (Internal)
   * Chip: ATtiny84
   * Port: Choose whatever port you connected your programmer to.
6. Select **Burn Bootloader** from the Tools menu. Wait for the _Done burning bootloader_ message to appear.
7. 
5. Upload code

[TBD]