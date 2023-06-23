# ALU (Arithmetic and Logic Unit)

## Table of Contents 
- [Overview](#Overview)
- [Components used](#Components-Used)
- [Schematics](#Schematics)
- [Working](#Working-of-the-ALU)
- [Difficulties Faced](#Difficulties-Faced)
- [References](#References)

## Overview

The **ALU**  in the 8-bit computer is a crucial component responsible for performing arithmetic and logical operations. It is designed to operate on **8-bit** binary data.

The ALU consists of various logic gates and circuits that enable it to execute operations such as:
- Addition
- Subtraction

## Components Used 

The components that were used to make the arithmetic and logic unit are specified below:
- 74LS86 Quad XOR gate 
- 74LS245 Octal bus transceiver 
- 74LS283 4-bit adder

## Schematics



<img width="1427" alt="alu" src="https://github.com/Abhilash-bhat/EightBitComputer/assets/80198193/13209e4d-6148-416f-b53f-6015e69ee35f">
                                                                   
**Fig.** ***ALU*** *(designed on KiCAD, Credits: Ben Eater)*

## Working of the ALU

The ALU receives inputs from the computer's registers A and B and carries out the specified operation based on control signals. It performs calculations and produces outputs that can be stored back in the registers or used for further processing or can be stored in the RAM location. The ALU design is based on a combination of combinatorial logic and sequential logic, ensuring accurate and efficient computation. The step-by-step working of the ALU is as follows. 

1. The ALU receives inputs from the computer's registers, which hold the operands for the desired operation.

2. The control signals specify the operation to be performed by the ALU. These control signals determine which logic gates and circuits are activated.

3. For arithmetic operations like addition and subtraction, the ALU uses a combination of XOR gates, AND gates, and OR gates to perform the binary arithmetic. The carry-in and carry-out signals are utilized to handle overflow in addition and borrowing in subtraction.

4. The output of the ALU can be stored back in the registers or used for further processing within the computer system.
   
The ALU operates synchronously with the clock signal, ensuring proper timing and synchronization with the rest of the computer's components. The ALU's modular design and combination of logic gates allow for flexibility and expandability, enabling enthusiasts to customize further and extend the ALU's functionality based on specific requirements or project goals such as multiplication with the involvement of flags and some changes in the assembly level code. 

1. The ALU receives two 8-bit binary numbers as inputs, typically from the computer's registers. These numbers represent the operands for the addition operation.

2. The ALU performs the addition using a combination of XOR gates, AND gates, and OR gates. These logic gates are interconnected to implement the binary addition algorithm.

3. The bits of the two input numbers are processed simultaneously, starting from the least significant bit (LSB) to the most significant bit (MSB).

4. At each bit position, the XOR gate calculates the sum of the corresponding bits of the input numbers. This sum represents the current bit of the result.

5. The AND gate generates a carry-out signal if both input bits are set (equal to 1), indicating a carry-over to the next bit position.

6. The OR gate produces a carry-in signal, which is received from the previous bit's carry-out signal.

7. The carry-in signal and the carry-out signal are used to handle carry propagation across multiple bit positions during addition. They ensure that the addition is correctly performed, taking into account any carry-over from lower bits.

8. The result of each bit addition, along with the carry-out signal from the most significant bit, forms the final 8-bit sum.

9. The carry-out signal can be used to detect overflow in case the addition results in a value larger than what can be represented with 8 bits.

10. The ALU generates the sum as its output, which can be stored back in registers or used for further processing within the computer system.

By utilizing this combination of logic gates and carry signals, the ALU performs binary addition efficiently and accurately. The modular design of the ALU allows for the addition operation to be integrated with other arithmetic and logical operations, providing a versatile computing capability to Ben Eater's 8-bit computer.





