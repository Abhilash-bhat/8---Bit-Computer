
# OUTPUT REGISTER

## Table of Contents
1. [Module Overview](#module-overview)
2. [Components Used](#components-used)
3. [Schematics](#schematics)
4. [Insights](#insights)
     -  [555 Timer IC](#555-timer-ic)
     -  [IC 74LS76](#ic-74ls76)
     -  [IC 74LS139](#ic-74ls139)
     -  [IC 74LS273](#ic-74ls273)
     -  [IC 74LS08](#ic-74ls08)
     -  [IC AT28C16](#ic-at28c16)
5. [Working](#working)
6. [Images](#images)
7. [References](#references)

## Module Overview

Similar to any register, the Output Register stores the binary value present on the bus and displays it on a 7segment LED display.Conversion from binary value to 7segment configuration is done by the rest of the circuits present in the Output Register module. This module shows human readable form of the binary number,i.e. decimal number. The 4th display is used for displaying '-' sign for negative numbers.

## Components Used

- **IC 555 Timer**[^1]
- **IC 74LS273** : 8-bit D Register[^2]
- **IC AT28C16** : 16k EEPROM[^3]
- **IC 74LS76**  : Dual JK FlipFlop[^4]
- **IC 74LS139** : Dual 2-to-4 line decoder/demultiplexer[^5]
- **IC  74LS08** : Quad AND Gate [^6]
- **Common Cathode 7 segment display** (7segment_CC x4)
- **SPDT Switch**
- **Resistors** : 1k ohm, 100k ohm, 10k ohm
- **Capacitors** : 0.01uF

## Schematics

![OUTPUT REGISTER_Schematics](https://eater.net/schematics/output.png)

**Fig.** ***OUTPUT REGISTER Schematic*** *(designed on KiCAD, Credits: Ben Eater)*[^7]

## Insights

### 555 Timer IC

The 555 timer is configured in astable mode and has a differnt rate than that of the master clock. Its main purpose is to sequence through each of the 4 7segment displays. And hence the displays display decimal numbers in a sequence. This action is controlled by the rate at which the astable multivibrator oscillates.

### IC 74LS76

IC 7476 is a dual JK FlipFlop. Cascading the two FlipFlops,  we obtain a 2-bit binary counter. The counting speed is determined by the square wave frequency of the astable multivibrator of Output Register module. This counter is used to address the 4 7segment displays. The counter is 2-bit and hence sequences through 4 unique sequence.

### IC 74LS139

IC 74139 is a dual 2-to-4 line decoder. For the distict sequence produced by IC 7476 (JK FF-counter), this IC Outputs one of the 4 lines a Low (IC 74139 is an active LOW IC). A common cathode display requires an active LOW signal, which is provided by this IC.

### IC 74LS273

IC 74273 is an 8-bit D register, which stores 8-bit binary value. Whenever ,there is a necessity to display decimal numbers, the binary value is pushed to the bus. In the subsequent clock cycle, the value from the bus ,gets stored into this D register. All the other circuits of this module converts this binary value to the decimal display.

### IC 74LS08

IC 7408 is a quad AND gate. It is used as a gate ,for the entry of bus value into the D register.

### IC AT28C16

IC 2816 is a 16k EEPROM (Electrically Erasable Programmable Read Only Memory). It contains 2k address locations in which 8-bit data can be stored. Since it is a ROM, data is permanantly stored. i.e. unlike RAM, ROM doesn't loose the data when the power goes off. Its electrically erasable, and programmable, hence data in any address can be erased and reprogrammed with a new data.

## Working

- Whenever an user wants decimal representation of the binary values, the OI control signal (Output In) is made HIGH. Then, in the next clock pulse, the 8-bit binary value from the bus gets stored into D Register.
- The 8-bit value is directly connected to 8 address lines of EEPROM. Based on the data stored in the 2k address locations, the EEPROM reads the data of the address pointed on its address lines.
- The next 2 address lines are connected to the JK FF-counter. The counter along with the data, decode the binary value into signals that configure the 7segment display to show decimal value corresponding to the binary value.
- The EEPROM is programmed through an Arduino. The code is available at **Output_Register_Code.ino**. [^8]
- The JK FF is given an on-module high frequency square wave as clock. This high frequency signal is obtained by an astable multivibrator circuit, built with a 555 Timer IC.
- A demultiplexer, decodes the counter signlas into 4 distinct signals, such that for each count, only one of the 4 displays are enabled.
- Since the frequency is very high, human eye cannot differentiate the pulsing of values.
- For positive only computations, we obtain values between 0 and 255.
- For general computations, we get values between -128 and 127.(2's complement method)
- The last address line of EEPROM makes this difference, for only positive or general computatuion. A simple SPDT switch determines the computation capabilities.

## Images

![Output_Register Image](https://github.com/Abhilash-bhat/EightBitComputer/assets/78137287/48a58ed5-21ec-42b4-8e81-35587681049c)


**Fig.** ***Output Register***

## References

[^1]: [Data Sheet 555 Timer IC](https://eater.net/datasheets/lm555.pdf)

[^2]: [Data Sheet 74LS273](https://eater.net/datasheets/74ls273.pdf)

[^3]: [Data Sheet AT28C16](https://eater.net/datasheets/28c16.pdf)

[^4]: [Data Sheet 74LS76](https://eater.net/datasheets/74ls107.pdf)

[^5]: [Data Sheet 74LS139](https://eater.net/datasheets/74ls139.pdf)
 
[^6]: [Data Sheet 74LS08](https://eater.net/datasheets/74ls08.pdf)

[^7]: [Ben Eater's Website](https://eater.net/8bit)

[^8]: [Output_Register_Code ](https://github.com/Abhilash-bhat/EightBitComputer/blob/main/Output_Register_Code.ino)

Note:IC 74LS76 is same as IC 74LS107.(Watch out for the Pins!)
* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)
