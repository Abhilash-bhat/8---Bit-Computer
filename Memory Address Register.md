
# MEMORY ADDRESS REGISTER (MAR)

## Table of Contents
1. [Module Overview](#module-overview)
2. [Components](#components)
3. [Schematics](#schematics)
4. [Insights](#insights)
   
   1. [Working](#working)
   
   3. [IC 74LS173](#ic-74ls173)
      
   5. [IC 74LS157](#ic-74ls157)
5. [Images](#images)
6. [References](#references)

## Module Overview

MAR is a simple 4-bit register, that holds/points to a RAM[^1] location. 
It is the basic block, through which data can be given to the computer for computations. It guides through the complete sequence of operations, without which the computer cannot compute at all.
 
## Components

- **IC 74LS173** : 4-Bit D-type registers with 3-state Outputs.
- **IC 74LS157** : Quad 2-line to 1-line data multiplexers/selectors.
- **4-position DIP Switch**
- **SPDT Switch**
- **Resistors** : 4x 220 ohm (Note: Only to limit current across LEDs.)
- **Light Emitting Diodes** : 4x Yellow, 1x Red, 1x Green

## Schematics

![MAR_Schematics](https://eater.net/schematics/mar.png)

**Fig.** ***MAR Schematic*** *(designed on KiCAD, Credits: Ben Eater)* [^2]

## Insights

### Working

There **2** modes in which MAR works:
- **User / Manual Mode**
- **Clock / Auto Mode**

The modes are selected using a simple SPDT (Single Pole Double Throw) switch. Red LED indicates User mode, while Green LED indicates Clock mode.
The 4 Yellow LED shows us the value in MAR. The value in MAR represents one of the 16 addresses of RAM.

#### User Mode

When selected in this mode, the user can set 4-bit value to the MAR. Values are set using the 4-position DIP switch. If DIP position is in OFF position, it represents Logic-0 (low), and when at ON position, it represents Logic-1 (high). The values range from 0 (binary 0000) to 15 (binary 1111). The computer is initialised in this mode. The instructions, along with data are stored to RAM locations through MAR.

#### Clock Mode

After initialising the computer, the computer now goes into automatic mode, where the clock runs at some suitable frequency set by the user. For each clock pulse, instructions get executed to yield the final result of the computations. For fetching the instruction or data, the MAR is fed RAM location from **8-bit BUS** of the computer(4-bit MSB would have b0000). The Program Counter[^3] dumps value of the RAM location to the BUS which is fed into MAR. For each new instruction or data, the MAR points to 4-bit address of RAM locations.

(Note: In this mode, the DIP switches have no control over MAR value.) 

### IC 74LS173  

IC 74LS173 [^4] is a 16-pin dual in-line package(DIP IC) IC. It is a 4-bit D-type register, with 3-state outputs.
* Pin 1 and 2 are output enable pins. When both are low, the output is enabled and normal logic of D-registers appear. If any of them go high, the output is disabled and a high impedence state is present at output.
* Pin 3,4,5 and 6 are output pins, where, Pin-3 is the LSB and Pin-6 is the MSB.
* Pin 7 is the clock pin. IC 74LS173 recognises rising-edge of the clock pulse.
* Pin 8 is the ground pin.
* Pin 9 and 10 are data enable pins. When both are low, data can be stored into the register. Even when one of them is high, data cannot be fed into the reg. and the register retains the previous value stored.
* Pin 11,12,13 and 14 are input pins, where Pin-11 is the LSB and Pin-14 is the MSB.
* Pin 15 is clear pin. A high on this pin clears the output.
* Pin 16 is the Vcc pin.

The data from BUS goes to pins 11,12,13 and 14, which is then stored into MAR in **Clock Mode**. Other Pins appropriately connected ,so as to avoid floating nodes.
In the Schematic, it is clear that, Pin 9 and 10 are given to MAR IN control signal. Clock and Clear signals are given to Pin 7 and 15 respectively.
Pins 1 and 2 are grounded, as we do not need high impedence state of outputs. Pin 7 is given to ground and Pin 16 is fed with Vcc.
Pins 3,4,5 and 6 are given as inputs to IC 74157.

### IC 74LS157  

IC 74LS157 [^5] is a 16-pin dual in-line package(DIP IC) IC. It is a Quad 2-line to 1-line data multiplexer.
* Pin 1 is the select pin. When low, it selects inputs I0 and when high, it selects inputs I1.
* Pin 2,5,11 and 14 are input lines that get selected when select signal is a low.
* Pin 3,6,10 and 13 are input lines that get selected when select signal is a high.
* Pin 4,7,9 and 12 are output signals, which depends on input and the select signal. Pin 4 is the output for the pair 2,3 , Pin 7 is the output for the pair 5,6 , Pin 9 is the output for the pair 10,11 , Pin 12 is the output for the pair 13,14.
* Pin 8 is the ground pin.
* Pin 15 is a strobe pin. When at logic-0, the multiplexers are selected, else the IC is disabled to only give logic-0 at outputs.
* Pin 16 is the Vcc pin.

The select pin is given appropriate signal to either work in **User Mode** or **Clock Mode**. When high, it works in **User Mode** and when low, it works in **Clock Mode**.
Pin 2,5,14 and 11 are inputs from DIP switches with Pin 2 as MSB amd Pin 11 as LSB ,following the order as stated.
Pin 3,6,13 and 10 are inputs from IC 74173 with Pin 3 as MSB amd Pin 10 as LSB ,following the order as stated.
Pin 15 is grounded, as we want MUX to be enabled all the time. Pin 8 is given to ground and Pin 16 is fed with Vcc.
Pin 4,7,9 and 12 are given to RAM address inputs. A set of LEDs connected to these pins enable us to read the data in MAR.

## Images

![MAR](https://github.com/Abhilash-bhat/EightBitComputer/assets/78137287/ac9a3df8-44d2-494f-ad8f-b8ccaf32dc62)



## References

[^1]: [RAM Module](https://github.com/Abhilash-bhat/EightBitComputer/blob/main/Random%20Access%20Memory.md)

[^2]: [Ben Eater's Website](https://eater.net/8bit)

[^3]: [Program Counter Module](https://github.com/Abhilash-bhat/EightBitComputer/blob/main/Program%20Counter.md)

[^4]: [Data Sheet 74LS173](https://eater.net/datasheets/74ls173.pdf)

[^5]: [Data Sheet 74LS157](https://eater.net/datasheets/74ls157.pdf)

* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)
