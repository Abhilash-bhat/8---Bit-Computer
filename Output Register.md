
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

Similar to any register, the Output Register stores the binary value present on the bus and displays it on a 7segment LED display.Conversion from binary value to 7segment configuration is done by the rest of the circuits present in the Output Register module.

## Components Used

- **IC 555 Timer**
- **IC 74LS273** : 8-bit D Register
- **IC AT28C16** : 16k EEPROM
- **IC 74LS76** : Dual JK FlipFlop
- **IC 74LS139** : Dual 2-to-4 line decoder/demultiplexer
- **IC  74LS08** : Quad AND Gate
- **Common Cathode 7 segment display** (CC_7segment x4)
- **SPDT Switch**
- **Resistors** : 1k ohm, 100k ohm, 10k ohm
- **Capacitors** : 0.01uF

## Schematics

![OUTPUT REGISTER_Schematics](https://eater.net/schematics/output.png)

**Fig.** ***OUTPUT REGISTER Schematic*** *(designed on KiCAD, Credits: Ben Eater)*[^4]

## Insights

### 555 Timer IC

### IC 74LS76

### IC 74LS139

### IC 74LS273

### IC 74LS08

### IC AT28C16

## Working

## Images

![Output_Register Image]()

**Fig.** ***Output Register***

## References

