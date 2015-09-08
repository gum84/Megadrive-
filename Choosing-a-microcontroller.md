## Choosing a microcontroller

**MegaDrivePlusPlus can run on several microcontrollers**, supporting different subsets of functionalities. It can probably be ported to many others with little effort, thanks to the flexibility of the Arduino platform.

If you are not too much into the Arduino world, this variety can be confusing, so here's how to choose the best microcontroller for you:

* First of all, if you already have an Atmel AVR microcontroller handy, check out below to see if that particular chip is supported and if the features you are interested in are available on it.

* If you have to buy a new chip from scratch I'd strongly recommend getting an
**Arduino Nano-compatible board**, since:
- It is cheap (2-3 EUR straight from China).
- It has plenty of pins, which means it supports all the features.
- It has an embedded USB port and serial converter, allowing for easy
upgrades (and debugging, in case).

* An **ATtiny861** is also a valid choice, if you prefer sticking to a single chip,
as it has plenty of I/O pins and it supports all features..

## Supported microcontrollers
All diagrams below for ATtiny chips are based on ATTinyCore:
https://github.com/SpenceKonde/ATTinyCore. Probably other cores will work as well, but you might have to adjust pin numbers and *#defines*, so please stick to ATTinyCore..

NOTE: In all diagrams, outer pin number are referred to the physical chips,
while inner pin numbers are Arduino pin numbers.

[To Be Continued..]