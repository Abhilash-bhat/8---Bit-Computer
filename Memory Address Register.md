
# MEMORY ADDRESS REGISTER (MAR)

## Table of Contents
1. [Module Overview](#module-overview)
2. [Components](#components)
3. [Schematics](#schematics)
4. [Insights](#insights)
   
   1. [Working](#working)
   
   3. [IC 74LS173](#ic-74ls173)
      
   5. [IC 74LS157](#ic-74ls157)
6. [References](#references)

## Module Overview

MAR is a simple 4-bit register, that holds/points to a RAM[^1] location. 
It is the basic block, through which data can be given to the computer for computations. It guides through the complete sequence of operations, without which the computer cannot compute at all.
 
## Components

- **IC 74LS173**[^2] : 4-Bit D-type registers with 3-state Outputs.
- **IC 74LS157**[^3] : Quad 2-line to 1-line data multiplexers/selectors.
- **4-position DIP Switch**
- **SPDT Switch**
- **Resistors** : 4x 220 ohm (Note: Only to limit current across LEDs.)
- **Light Emitting Diodes** : 4x Yellow, 1x Red, 1x Green

## Schematics

![MAR_Schematics](https://eater.net/schematics/mar.png)

**Fig.** ***MAR Schematic*** *(designed on KiCAD, Credits: Ben Eater)*[^4]

## Insights

### Working

There **2** modes in which MAR works:
- **User / Manual Mode**
- **Clock / Auto Mode**

The modes are selected using a simple SPDT (Single Pole Double Throw) switch. Red LED indicates User mode, while Green LED indicates Clock mode.
The 4 Yellow LED shows us the value in MAR. The value in MAR represents one of the 16 addresses of RAM[^1]. 

#### User Mode

When selected in this mode, the user can set 4-bit value to the MAR. Values are set using the 4-position DIP switch. If DIP position is in OFF position, it represents Logic-0 (low), amd when at ON position, it represents Logic-1 (high). The values range from 0 (binary 0000) to 15 (binary 1111), in all 16 values.

### IC 74LS173[^2]

### IC 74LS157[^3]


## References
