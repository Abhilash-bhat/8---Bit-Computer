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

The ALU operates synchronously with the clock signal, ensuring proper timing and synchronization with the rest of the computer's components. The ALU's modular design and combination of logic gates allow for flexibility and expandability, enabling enthusiasts to customize further and extend the ALU's functionality based on specific requirements or project goals such as multiplication with the involvement of flags and some changes in the assembly level code. 

### *How the addition actually works* ###

For this operation, the XOR gates (IC7486) and the 4-bit adder (IC74283) are used. The step-by-step operation of how two 8-bit numbers are added is as below.
- The value from RAM is loaded into Register A and Register B.
- The 7486 IC receives two input signals, typically representing one bit from the Register B being added and the value 0 for addition.
- The outputs of the XOR gates are fed to one-half of both the 74283s and the other half is fed with the data from Register A. 
- The IC74283 has 4 individual adder circuits which calculate the sum of the two input bits and the carry-in bit, providing a sum output 
  bit and a carry-out bit

By utilizing this combination of logic gates and carry signals, the ALU performs binary addition efficiently and accurately. The modular design of the ALU allows for the addition operation to be integrated with other arithmetic and logical operations, providing a versatile computing capability to Ben Eater's 8-bit computer.





