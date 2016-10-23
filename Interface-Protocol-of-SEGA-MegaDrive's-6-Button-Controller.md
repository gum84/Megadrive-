# Interface Protocol of SEGA MegaDrive's 6-Button-Controller

         Source: https://applause.elfmimi.jp/md6bpad-e.html
         Author: Ein Terakawa, applause@@elfmimi.jp
    Last Update: 24/10/2016

## Pin Assign (D-SUB9P)

| SignalName |   Explanation (Direction)
|  ----------|---------------------------------
|   1. D0    | Data         (Controller -> Mainframe)
|   2. D1    | Data         (Controller -> Mainframe)
|   3. D2    | Data         (Controller -> Mainframe)
|   4. D3    | Data         (Controller -> Mainframe)
|   5. +5V   | PowerSupply  (Supplied to Controller by Mainframe)
|   6. D4    | Data         (Controller -> Mainframe)
|   7. Sel   | SelectSignal (Mainframe -> Controller)
|   8. GND   | Ground
|   9. D5    | Data         (Controller -> Mainframe)

All signals are TTL compatible.


## In Case of 3-Button-Controller

     Sel  D0 D1 D2 D3 D4 D5
     Low  UP DW LO LO A  ST
     High UP DW LF RG B  C
    
       # LO --- Always Low
       # UP --- Up of Cross Key
       # DW --- Down of Cross Key
       # LF --- Left of Cross Key
       # RG --- Right of Cross Key
       # A ---- Trigger Button A
       # B ---- Trigger Button B
       # C ---- Trigger Button C
       # ST --- Start Button
       ## Low -> Pressed , High -> Not Pressed

## Data Aquisition Sequence of 6-Button-Controller

    Sel   D0 D1 D2 D3 D4 D5
    Low   UP DW LO LO A  ST
    High  UP DW LF RG B  C
    Low   UP DW LO LO A  ST
    High  UP DW LF RG B  C   # If there is two up-edge in 1.1 milli seconds,
    Low   LO LO LO LO A  ST  # D0 - D3 go Low as Sel goes Low.
    High  Z  Y  X  MD HI HI  # Make Sel High and read D0 - D3.
    Low   HI HI HI HI A  ST  # Check that D0 - D3 go High as Sel goes Low.
    High  UP DW LF RG B  C   # Once this sequence take place
    Low   UP DW LO LO A  ST  # sequence can't be started for 1.8 milli seconds
    .                        # after the first up-edge of Sel.
    .                        # Only Datas read in 1.6 milli seconds from the
    .                        # first up-edge of Sel are reliable.

       # LO --- Always Low
       # HI --- Always High
       # UP --- Up of Cross Key
       # DW --- Down of Cross Key
       # LF --- Left of Cross Key
       # RG --- Right of Cross Key
       # A ---- Trigger Button A
       # B ---- Trigger Button B
       # C ---- Trigger Button C
       # X ---- Trigger Button X
       # Y ---- Trigger Button Y
       # Z ---- Trigger Button Z
       # ST --- Start Button
       # MD --- Mode Button
       ## Low -> Pressed , High -> Not Pressed

Time parameters were measured by using my PC's timer.
It seems that the time is measured by discharging of
a capacitor in a 6-Button-Controller. It may mean
parameters differ one by one controller.
Please choose values you think proper for parameters.

Ein Terakawa

applause@@elfmimi.jp