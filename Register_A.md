# Register A

## Module Overview

Register A is a key component of the 8-bit breadboard computer.
It is an 8-bit register, meaning it can hold an 8-bit binary value and output the data held.
It's like the computer's "short-term memory," holding data that the computer is currently working with, 
making it a crucial part of the computer's operations.

 ## Components used
 
 * **IC 74LS173** : 4-Bit D-Type Registers With 3-State Outputs [^1]
 * **IC 74LS245** : 3-State Octal Bus Transceiver [^2]

## Schematic

![Register_A_Schematic](https://eater.net/schematics/a-register.png)


**Fig.** ***Register A Schematic*** *(designed on KiCAD, Credits: Ben Eater)* [^3]
 
 ## Working of the Register A
 
 ### Summary of working 
 
* One of the components of the computer is the register A, which is an 8-bit register that can store and output data. 
* The register A uses a 74LS173 chip, which is a 4-bit D register that can be enabled or disabled by a control signal. 
* The register A also uses a 74LS245 chip, which is an octal bus transceiver that can transfer data between two buses. 
* The register A has a load pin that allows it to store data from the bus, and an enable pin that allows it to output data to the bus. 
* These flip-flops are connected to a common bus, which allows them to receive data from other parts of the computer. 
This bus system is a fundamental part of the computer's architecture, enabling communication between different components.
* These control lines can instruct the register to load data from the bus, output its data onto the bus, or perform other operations.
* The register A has eight red LEDs that indicate the stored data.

### Role of IC 74LS245

* The 74LS245 is an octal bus transceiver, which means it can transmit data in both directions on an 8-bit bus. 
It's used in the A register (and other registers) to control whether the register is outputting its data onto the bus or not.

* The 74LS245 has a direction pin (DIR) and an output enable pin (OE). 
When the OE pin is low, the transceiver is enabled, and the direction of data flow is determined by the DIR pin. 
If DIR is high, data flows from the A side (pins A1-A8) to the B side (pins B1-B8).  
If DIR is low, data flows from the B side to the A side.

* In the context of the A register, the 74LS245 is used to control when the register's data is put onto the bus. 
When the register's output control signal is activated (low), the 74LS245's OE pin is set low, 
enabling the transceiver and allowing the data stored in the register to be put onto the bus. 
When the output control signal is not activated (high), the OE pin is set high, 
disabling the transceiver and  isolating the register's data from the bus. 
This ability to control when a register outputs its data onto the bus is crucial in a computer system, 
as it allows different components to use the bus at different times without interfering with each other.

### Role of IC 74LS173

* The 74LS173 is a 4-bit D-type register. It's used for storing data temporarily within a digital circuit. 
*In the context of Register A, it's used to hold the data that the register is currently working with.

* The 74LS173 has four data input lines (D0-D3), four output lines (Q0-Q3), two control lines for output enable (OE1 and OE2), 
and a clock input (CP). When the clock input receives a rising edge (transition from low to high), 
the data present on the D0-D3 inputs is latched into the register and held there until the next rising edge of the clock.
The output enable lines are used to control whether the contents of the register are output onto the Q0-Q3 lines. 
When both OE1 and OE2 are low, the outputs are enabled and the data in the register is output. 
When either OE1 or OE2 is high, the outputs are disabled and the Q0-Q3 lines are in a high impedance state, 
effectively disconnecting the register from whatever it's connected to.

* In the context of Register A, two 74LS173 chips would be used to create an 8-bit register. 
The data inputs would be connected to the data bus, allowing the register to receive data from other parts of the computer. 
The output enable lines would be controlled by the computer's control logic, allowing it to control 
when the register outputs its data onto the bus. 
The clock input would be connected to the computer's clock signal, synchronizing the register's operations with the rest of the computer

## Pictures



## References

[^1]: [Data Sheet 74LS173](https://eater.net/datasheets/74ls173.pdf)

[^2]: [Data Sheet 74LS245](https://eater.net/datasheets/74ls245.pdf)

[^3]: [Ben Eater's Website](https://eater.net/8bit)

* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)
