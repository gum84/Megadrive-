**MegaDrivePlusPlus can run on several microcontrollers**, supporting different subsets of functionalities. It can probably be ported to many others with little effort, thanks to the flexibility of the Arduino platform.

If you are not too much into the Arduino world, this variety can be confusing, so here's how to choose the best microcontroller for you:

* First of all, **if you have already modded your console** with the D4s/Seb mod and the chip is installed in a socket, you are advised to get an **ATtiny44(A)** or **ATtiny84(A)**: all the wires that are already in place will be fine and you will just need to solder a few more wires to the controller port. If the chip is not installed in a socket, just desolder it but keep the wires, they will all be fine!

* **If you have an Atmel AVR microcontroller handy**, check out below to see if that particular chip is supported and if the features you are interested in are available on it. If so, **use it**!

* **If you have to buy a new chip from scratch** I'd strongly recommend getting an
**Arduino Nano-compatible board**, since:
  * It is cheap (2-3 EUR straight from China).
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
**On ATtinyX4 most features are supported**. The only exception is that **RIGHT and LEFT cannot be used in combos**.

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

The connection layout puts the SELECT signal on the INT1 pin. This will probably be needed if we ever want to read 6-button pads. LED is connected to PWM-capable pins.
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

### Arduino (or bare ATmega168/328)
**On a full Arduino board (or just MCU) all features are supported**. Unfortunately, there is no single port whose pins are all available, so we resort again to reading UP and DOWN from a different port. Technically we could use PORTD, but since working on a full Arduino board is mainly useful to get debugging messages through the serial port, we don't do that (PD0/1 are used for hardware serial). But if you put a single ATmega328 on a board and use its internal clock you also get a full PORTB, so we might support that in the future. On a side note, PORTD also has INT1 on pin2, so we could easily use the X61 read function for 6-button pads...
```
                    ,-----_-----.
                    |1     A5 28| JP1/2 (Language)
                    |2   0 A4 27| JP3/4 (Video Mode)
                    |3   1 A3 26| Reset In
     Pad Port Pin 7 |4   2 A2 25| Reset Out
     Pad Port Pin 3 |5   3 A1 24| Pad Port Pin 2
     Pad Port Pin 4 |6   4 A0 23| Pad Port Pin 1
                +5V |7        22| GND
                GND |8        21| +5V
                    |9        20| +5V
                    |10    13 19| (Built-in LED)
     Pad Port Pin 6 |11  5 12 18|
     Pad Port Pin 9 |12  6 11 17| LED Blue
                    |13  7 10 16| LED Green
                    |14  8  9 15| LED Red
                    `-----------'
```