# ALU (Arithmetic and Logic Unit)

## Table of Contents 
- [Overview](#Overview)
- [Components used](#Components-Used)
- [Schematics](#Schematics)
- [Working](#Working-of-the-ALU)
    1. [How addition works](#How-the-addition-actually-works)
    2. [How subtraction works](How-the-subtraction-actually-works)
- [Images](#Images)
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

### *How the addition actually works* 

For this operation, the XOR gates (IC7486) and the 4-bit adder (IC74283) are used. The step-by-step operation of how two 8-bit numbers are added is as below.
- The value from RAM is loaded into Register A and Register B.
- The 7486 IC receives two input signals, typically representing one bit from the Register B being added and the value of SU = 0 for addition. The value 0 is also given as Carry in.
- The outputs of the XOR gates are fed to one-half of both the 74283s and the other half is fed with the data from Register A. 
- The IC74283 has 4 individual adder circuits which calculate the sum of the two input bits and the carry-in bit, providing a sum output 
  bit and a carry-out bit. The carry-out bit of the lower adder (B0-B3 + A0-A3) is fed as Cin to the other adder.
- The sum outputs from each full adder form the resulting bits of the addition operation.
- If a negative number is to be added, the 2's complement of the number is taken and added with the positive number. (The 2's compliment has to be manually entered )

By utilizing this combination of logic gates and carry signals, the ALU performs binary addition efficiently and accurately. 

### *How the subtraction actually works*

For this operation, the XOR gates (IC7486) and the 4-bit adder (IC74283) are used. The step-by-step operation of how two 8-bit numbers are subtracted is as below.
- The value from RAM is loaded into Register A and Register B.
- The 7486 IC receives two input signals, typically representing one bit from the Register B being added and the value SU = 1 for subtraction. This operation results in the 1's complement of the original value of Register B. The value 1 is also given in as Carry in which when added to the 1's complement makes it 2's complement.
- The outputs of the XOR gates are fed to one-half of both the 74283s and the other half is fed with the data from Register A.
- The IC74283 has 4 individual adder circuits which calculate the sum of the two input bits and the carry-in bit, providing a sum output 
  bit and a carry-out bit. The carry-out bit of the lower adder (B0-B3 + A0-A3) is fed as Cin to the other adder.
- Since one of the numbers is a 2's complement the result will be the subtracted number with a change in flag if borrow was used
- If a negative number has to be subtracted the the 2's complement of the number has to be manually entered.

  By utilizing this combination of logic gates and carry signals, the ALU performs binary addition efficiently and accurately.


## Images

![ALU](https://github.com/Abhilash-bhat/EightBitComputer/assets/80198193/369de57d-d5b0-4e57-bd4d-c072fecab275)



## References 


* [Ben Eater's Channel](https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU)


