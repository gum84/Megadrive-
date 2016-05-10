**MegaDrive++ can run on several microcontrollers**, supporting different subsets of functionalities. It can probably be ported to many others with little effort, thanks to the flexibility of the Arduino platform.

If you are not too much into the Arduino world, this variety can be confusing, so here's how to choose the best microcontroller for you:

* First of all, **if you have already modded your console** with the D4s/Seb mod and the chip is installed in a socket, you are advised to get an **ATtiny44(A)** or **ATtiny84(A)**: all the wires that are already in place will be fine and you will just need to solder a few more wires to the controller port. If the chip is not installed in a socket, just desolder it but keep the wires, they will all be fine!

* **If you have an Atmel AVR microcontroller handy**, check out below to see if that particular chip is supported and if the features you are interested in are available on it. If so, **use it**!

* **If you have to buy a new chip from scratch** I'd strongly recommend getting an
**Arduino Nano**, since:
  * It is cheap (Non-official clones are 2-3 EUR straight from China, shipping included!).
  * It has plenty of pins, which means it supports all the features.
  * It has an embedded USB port and serial converter, allowing for easy
upgrades (and debugging, in case).

* An **ATtiny861** is also **a good choice**, if you prefer sticking to a single chip,
as it has plenty of I/O pins and supports all features.

## Supported Microcontrollers
All diagrams below for ATtiny chips are based on ATTinyCore:
https://github.com/SpenceKonde/ATTinyCore. Probably other cores will work as well, but you might have to adjust pin numbers and *#defines*, so please stick to ATTinyCore..

**NOTE:** In all diagrams, outer pin number are referred to the physical chips,
while inner pin numbers are Arduino pin numbers.

### ATtiny 25/45/85
ATtinyX5 only supports Reset-From-Pad.
```
                 ,-----_-----.
                 |1 (5)     8| +5V
        Reset In |2   3  2  7| Pad Port Pin 7
       Reset Out |3   4  1  6| Pad Port Pin 9
             GND |4      0  5| Pad Port Pin 6
                 `-----------'
```

### ATtiny24/44/84(A)
**On ATtinyX4 most features are supported**. The only exception is that **RIGHT and LEFT cannot be used**, so we resort to using UP and DOWN to cycle through the available modes.

The connection layout is derived from that of the Seb/D4s mod, so that **if you already have a properly-wired socket in you console, you will just need to add a few wires** and replace the chip to get the new features. The wires to be added are all those coming from the controller pad port.
```
                  ,-----_-----.
              +5V |1        14| GND
   Pad Port Pin 1 |2   0 10 13| Reset In
   Pad Port Pin 2 |3   1  9 12| Pad Port Pin 6
                  |4 (11) 8 11| Pad Port Pin 9
          LED Red |5   2  7 10| JP1/2 (Language)
        LED Green |6   3  6  9| JP3/4 (Video Mode)
   Pad Port Pin 7 |7   4  5  8| Reset Out
                  `-----------'
```

### ATtiny261/461/861
**On ATtinyX61 all features are supported**. We even read all buttons with a single instruction.

_Tech note: The connection layout puts the SELECT signal on the INT1 pin. This will probably be needed if we ever want to read 6-button pads. LED is connected to PWM-capable pins._
```
                    ,-----_-----.
           Reset In |1   9  0 20| Pad Port Pin 1
            LED Red |2   8  1 19| Pad Port Pin 2
          Reset Out |3   7  2 18| Pad Port Pin 7
          LED Green |4   6 14 17| Pad Port Pin 3
                +5V |5        16| GND
                GND |6        15| +5V
 JP3/4 (Video Mode) |7   5 10 14| Pad Port Pin 4
           LED Blue |8   4 11 13| Pad Port Pin 6
   JP1/2 (Language) |9   3 12 12| Pad Port Pin 9
                    |10(15)13 11|
                    `-----------'
```

### Full Arduino Board
**On a full Arduino board all features are supported**.

_Tech note: Unfortunately, there is no single port whose pins are all available, so we resort again to reading UP and DOWN from a different port. Technically we could use PORTD, but since working on a full Arduino board is mainly useful to get debugging messages through the serial port, we don't do that (PD0/1 are used for hardware serial)._

*All Arduino ASCII-Art below courtesy of [BusyDuckMan](http://busyducks.com/ascii-art-arduinos))*

#### Arduino Uno
```
                    +----[PWR]-------------------| USB |--+
                    |                            +-----+  |
                    |         GND/RST2  [ ][ ]            |
                    |       MOSI2/SCK2  [ ][ ]  A5/SCL[ ] |
                    |          5V/MISO2 [ ][ ]  A4/SDA[ ] |
                    |                             AREF[ ] |
                    |                              GND[ ] |
                    | [ ]N/C                    SCK/13[ ] | (Built-in LED)
                    | [ ]IOREF                 MISO/12[ ] |
                    | [ ]RST                   MOSI/11[X]~| LED Blue
                    | [ ]3V3    +---+               10[X]~| LED Green
                +5V | [X]5v    -| A |-               9[X]~| LED Red
                GND | [X]GND   -| R |-               8[ ] | 
                    | [ ]GND   -| D |-                    |
                    | [ ]Vin   -| U |-               7[ ] |
                    |          -| I |-               6[X]~| Pad Port Pin 9
     Pad Port Pin 1 | [X]A0    -| N |-               5[X]~| Pad Port Pin 6
     Pad Port Pin 2 | [X]A1    -| O |-               4[X] | Pad Port Pin 4
          Reset Out | [X]A2     +---+           INT1/3[X]~| Pad Port Pin 3
           Reset In | [X]A3                     INT0/2[X] | Pad Port Pin 7
 JP3/4 (Video Mode) | [X]A4/SDA  RST SCK MISO     TX>1[ ] |
   JP1/2 (Language) | [X]A5/SCL  [ ] [ ] [ ]      RX<0[ ] |
                    |            [ ] [ ] [ ]              |
                    |  UNO_R3    GND MOSI 5V  ____________/
                    \_______________________/
```

#### Arduino Nano
```
                                 +-----+
                    +------------| USB |------------+
                    |            +-----+            |
     (Built-in LED) | [ ]D13/SCK        MISO/D12[ ] |
                    | [ ]3.3V           MOSI/D11[X]~| LED Blue
                    | [ ]V.ref     ___    SS/D10[X]~| LED Green
     Pad Port Pin 1 | [X]A0       / N \       D9[X]~| LED Red
     Pad Port Pin 2 | [X]A1      /  A  \      D8[ ] |
          Reset Out | [X]A2      \  N  /      D7[ ] |
           Reset In | [X]A3       \_0_/       D6[X]~| Pad Port Pin 9
 JP3/4 (Video Mode) | [X]A4/SDA               D5[X]~| Pad Port Pin 6
   JP1/2 (Language) | [X]A5/SCL               D4[X] | Pad Port Pin 4
                    | [ ]A6              INT1/D3[X]~| Pad Port Pin 3
                    | [ ]A7              INT0/D2[X] | Pad Port Pin 7
                +5V | [X]5V                  GND[X] | GND
                    | [ ]RST                 RST[ ] |
                    | [ ]GND   5V MOSI GND   TX1[ ] |
                    | [ ]Vin   [ ] [ ] [ ]   RX0[ ] |
                    |          [ ] [ ] [ ]          |
                    |          MISO SCK RST         |
                    | NANO-V3                       |
                    +-------------------------------+
```

#### Arduino Pro Mini

Arduino Pro Mini does not have an onboard USB <-> Serial converter, so you will have to use an external one (or ICSP) to program it. That's what the pins on the top are meant for.

Be careful with the position of the A4/A5 pins! You can remap them in the code to pins 7/8 if you prefer.

**WARNING: You MUST use the 5V/16MHz version!**

```
		                  D0   D1   RST
		   GND  GND  VCC  RX   TX   /DTR
                +--------------------------------+
                |  [ ]  [ ]  [ ]  [ ]  [ ]  [ ]  |
                |              FTDI              |
                | [ ]1/TX                 RAW[ ] |    
                | [ ]0/RX                 GND[X] | GND   
                | [ ]RST        SCL/A5[X] RST[ ] | A5 = JP1/2 (Language)
                | [ ]GND        SDA/A4[X] VCC[X] | A4 = JP3/4 (Video Mode), VCC = +5V
 Pad Port Pin 7 | [X]2/INT0    ___         A3[X] | Reset In
 Pad Port Pin 3 |~[X]3/INT1   /   \        A2[X] | Reset Out
 Pad Port Pin 4 | [X]4       /PRO  \       A1[X] | Pad Port Pin 2
 Pad Port Pin 6 |~[X]5       \ MINI/       A0[X] | Pad Port Pin 1
 Pad Port Pin 9 |~[X]6        \___/    SCK/13[ ] | (Built-in LED)
                | [ ]7          A7[ ] MISO/12[ ] |
                | [ ]8          A6[ ] MOSI/11[X]~| LED Blue
        LED Red |~[X]9                  SS/10[X]~| LED Green
                |           [RST-BTN]            |    
                +--------------------------------+  
```

### Standalone ATmega168/328

**This is not an officially supported target at the moment**, but it would be trivial to add. You can use it with the normal Arduino pin-mapping though, but the real bonus here is that running the 328 on its internal 8 MHz clock (unlike they do on Arduino boards), we also get access to the full PORTB, allowing us to read all buttons at once.

Support for the 328@8Mhz can be found in the [Optiboot](https://github.com/Optiboot/optiboot) package, for instance.

Note that you **MUST** connect both grounds (pins 8 and 22) and both VCCs (pins 7 and 20).

```
                    ,-----_-----.
                    |1     A5 28| JP1/2 (Language)
                    |2   0 A4 27| JP3/4 (Video Mode)
                    |3   1 A3 26| Reset In
     Pad Port Pin 7 |4   2 A2 25| Reset Out
     Pad Port Pin 3 |5   3 A1 24| Pad Port Pin 2
     Pad Port Pin 4 |6   4 A0 23| Pad Port Pin 1
                +5V |7        22| GND
                GND |8        21|
                    |9        20| +5V
                    |10    13 19| (Built-in LED)
     Pad Port Pin 6 |11  5 12 18|
     Pad Port Pin 9 |12  6 11 17| LED Blue
                    |13  7 10 16| LED Green
                    |14  8  9 15| LED Red
                    `-----------'
```