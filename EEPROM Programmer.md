# EEPROM Programmer

## Table of Contents
1.  [Module Overview](#module-overview)
2.  [Components used](#components-used)
3.  [Schematic](#schematic)
4.  [Working](#working)

    I.   [Summary of Working](#summary-of-working)

    II.  [Role of IC 74HC595](#role-of-ic-74hc595)
    
    III. [Role of IC AT28C16](#role-of-ic-at28c16)

    IV.  [Role of IC Arduino Nano](#role-of-arduino-nano)
6.  [Pictures](#pictures)
7.  [References](#references)

## Module Overview

In the 8-bit computer, the EEPROM programmer plays a crucial role in programming the EEPROM (Electrically Erasable Programmable Read-Only Memory) chip. The EEPROM is used to store the computer's microcode, which is a set of instructions that control the computer's operations.

The EEPROM programmer allows us to write the microcode instructions onto the EEPROM chip, effectively customizing the computer's behavior and enabling it to perform specific tasks. By programming the EEPROM, Ben can make changes to the computer's instruction set and implement different functionalities within the constraints of the hardware design.

 ## Components used
 
 * **IC 74HC595** : 8-Bit Shift Registers With 3-State Outputs [^1]
 * **IC AT28C16** : 16K (2K x 8) Parallel EEPROMs [^2]
 * **Arduino Nano** : Microcontroller to program the EEPROM [^3]


## Schematic

![EEPROM Programmer_Schematic](https://github.com/beneater/eeprom-programmer/blob/master/schematic.png)


**Fig.** ***EEPROM Programmer Schematic*** *(designed on KiCAD, Credits: Ben Eater)* [^4]
 
 ## Working
 
 ### Summary of working 
 
The EEPROM programmer in 8-bit computer is designed to write data onto the EEPROM chip. The process involves the following steps:

* **Prepare the EEPROM:** The first step is to insert the EEPROM chip into the breadboard on the programmer. The breadboard holds the chip in place without damaging the pins.

* **Load Data:** The microcode or data that needs to be written onto the EEPROM is loaded into the programmer. This data typically contains the instructions that define the computer's behavior.

* **Start Programming:** The programming process is initiated by pressing the relevant button or activating the programming sequence.

* **Microcontroller Controls Write Process:** The microcontroller in the programmer takes over and starts the actual write process. It sends the data to the EEPROM chip one byte at a time in the correct sequence.

* **Write to EEPROM:** The microcontroller writes the data to the EEPROM's memory cells by applying specific voltage levels to the chip's pins. These voltage levels represent the binary data being programmed into the EEPROM.

* **Verify Data:** After writing each byte, the programmer may read back the data from the EEPROM to verify that it was written correctly. This verification ensures that the data is stored accurately and reliably.

* **End of Programming:** Once all the data is written and verified, the programmer signals that the programming process is complete, and the EEPROM is now programmed with the desired microcode or data.


### Role of IC 74HC595

* The 74595 IC is a type of shift register that can convert serial data into parallel data or vice versa. The Arduino does not have enough pins to directly control all of the address, data, and control lines of the EEPROM chip, so it uses two 74595 ICs to shift out the address and output enable signals serially and then latch them into parallel outputs. This way, the Arduino can send commands and data to the EEPROM chip using only a few wires.

* The 74595 IC has eight parallel outputs (Q0 to Q7) that can be connected to the address, data, and control lines of the EEPROM chip. The 74595 IC also has a serial input (DS) and a serial output (Q7S) that can be connected to the Arduino. The 74595 IC also has three control pins: a shift register clock (SH_CP), a storage register clock (ST_CP), and an output enable (OE).

* The Arduino can send data to the 74595 IC by setting the DS pin to either high or low, and then pulsing the SH_CP pin. This will shift the bit into the shift register, and move the previous bits one position to the right. The Arduino can repeat this process until it sends eight bits to the 74595 IC. The Arduino can also receive data from the 74595 IC by reading the Q7S pin, and then pulsing the SH_CP pin. This will shift the bit out of the shift register, and move the next bits one position to the left. The Arduino can repeat this process until it receives eight bits from the 74595 IC.

* The Arduino can also transfer the data from the shift register to the storage register by pulsing the ST_CP pin. This will latch the data into the parallel outputs, and make them available for the EEPROM chip. The Arduino can also enable or disable the parallel outputs by setting the OE pin to either low or high, respectively.

### Role of IC AT28C16
* The role of the AT28C16 in the EEPROM programmer in the 8-bit computer by Ben Eater is to store the microcode that defines the instruction set of the CPU. The microcode is a set of binary patterns that control the signals sent to the different components of the CPU, such as the registers, the ALU, and the control unit. By programming the AT28C16 with different microcode, the programmer can change the behavior and functionality of the CPU. For example, the programmer can add new instructions, modify existing ones, or implement conditional logic .

* The AT28C16 is a type of EEPROM (electrically erasable programmable read-only memory) chip that can store 16K (2K x 8) bits of data. The AT28C16 is accessed like a static RAM for read and write operations. During a byte write, the address and data are latched internally. Following the initiation of a write cycle, the device will go to a busy state and automatically write the latched data using an internal control timer. The device provides two methods for detecting the end of a write cycle: the RDY/BUSY output and DATA POLLING of I/O7 .

### Role of Arduino Nano

* The role of the Arduino Nano in the EEPROM programmer in the 8-bit computer by Ben Eater is to control the programming process of the EEPROM chip using a serial protocol. The Arduino Nano is a small, complete, and breadboard-friendly board based on the ATmega328P microcontroller. It has more or less the same functionality of the Arduino Uno board, but in a smaller form factor.

* The Arduino Nano is connected to the EEPROM chip and two 74595 ICs using a few wires. The 74595 ICs are shift registers that can convert serial data into parallel data or vice versa4. The Arduino Nano uses the 74595 ICs to send the address and output enable signals to the EEPROM chip serially, and then latch them into parallel outputs. This way, the Arduino Nano can send commands and data to the EEPROM chip using only a few wires.

* The EEPROM chip stores the microcode that defines the instruction set of the CPU, which is a set of binary patterns that control the signals sent to the different components of the CPU, such as the registers, the ALU, and the control unit4 . By programming the EEPROM chip with different microcode, the programmer can change the behavior and functionality of the CPU. For example, the programmer can add new instructions, modify existing ones, or implement conditional logic.

## Pictures


## References

[^1]: [Data Sheet 74HC595](https://www.sparkfun.com/datasheets/IC/SN74HC595.pdf)

[^2]: [Data Sheet AT28C16](https://eater.net/datasheets/28c16.pdf)

[^3]: [Arduino Nano Documentation](https://docs.arduino.cc/hardware/nano)

[^4]: [Ben Eater's Website](https://eater.net/8bit)

* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)
