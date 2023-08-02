# Random Access Memory (RAM)

## Table of Contents 
- [Overview](#Overview)
- [Components used](#Components-Used)
- [Schematics](#Schematics)
- [Working](#Working-of-the-RAM)
   1. [Programming the RAM](#Programming-the-RAM)
- [Images](#Images)
- [References](#References)


## Overview

The RAM module is a fundamental component of our 8-bit computer project, serving as a crucial part of the computer's memory architecture. RAM, short for Random Access Memory, functions as a temporary data storage medium that allows fast access to information needed by the Central Processing Unit (CPU) during program execution.

The main purpose of the RAM module is to efficiently handle data and instructions while running programs. It provides rapid read and write access, making it an essential element of the memory hierarchy in modern computing systems.

## Components Used 

- 74LS00 Quad NAND gate
- 74LS04 Hex inverter
- 74LS157 Quad 2-to-1 selectors/multiplexer
- 74LS173 4-bit D register
- 74189 64-bit RAM
- 74LS245 8-bit bus transceiver

## Schematics
<img width="1409" alt="ram" src="https://github.com/Abhilash-bhat/EightBitComputer/assets/80198193/6adecb4d-fd7d-4665-890c-eed181bc1492">


## Working of the RAM

The working of RAM (Random Access Memory) in the 8-bit computer involves storing and retrieving data during program execution. RAM serves as a temporary storage medium that allows the CPU (Central Processing Unit) to access data quickly and efficiently. Here's a step-by-step explanation of how RAM works in an 8-bit computer:

1. **Data Storage**: The RAM module is made up of multiple memory cells, each capable of holding 8 bits of data. These memory cells are organized in a matrix-like structure, with each cell having a unique address. When the computer is turned on, the RAM is initialized with random data or set to a predefined state.

2. **Addressing**: The CPU communicates with the RAM module by sending memory addresses on the address bus. Each address corresponds to a specific memory cell. For example, an 8-bit computer can have a maximum of 2^8 (256) unique memory addresses since it uses 8 bits to address each cell.

3. **Read Operation**: When the CPU needs to read data from RAM, it puts the desired memory address on the address bus and issues a read command. The address decoder in the RAM module activates the appropriate memory cell corresponding to the given address.

4. **Data Transfer**: The data stored in the activated memory cell is then sent back to the CPU through the data bus. The CPU reads the data from the data bus and processes it as needed for program execution.

5. **Write Operation**: When the CPU needs to write data into RAM, it places the memory address on the address bus, along with the data to be written on the data bus. The address decoder activates the appropriate memory cell, and the data from the data bus is stored in that cell, overwriting the previous content.

6. **Random Access**: The term "random access" means that the CPU can access any memory cell in RAM directly, without having to read through the entire memory sequentially. This property allows for efficient and flexible data access, essential for executing various instructions in a program.

7. **Temporary Storage**: RAM is considered volatile memory, which means that its contents are only retained while the computer is powered on. When the computer is shut down, the data stored in RAM is lost. This is in contrast to non-volatile storage, such as hard drives or solid-state drives, which retain data even when the power is off.

In summary, the RAM in an 8-bit computer is a crucial component that enables the CPU to temporarily store and retrieve data during program execution. Its fast random access and volatile nature make it ideal for handling dynamic data and executing programs efficiently.

The roles of each IC individually are given below:

- #### Role of 74LS00 Quad NAND gate

The 74LS00 IC contains four NAND gates, which are fundamental logic gates used to perform Boolean operations. They can be used to implement various logic functions in the computer, such as AND, OR, and NOT.

- #### Role of 74LS04 Hex inverter

The 74LS04 IC contains six inverters, which perform the NOT operation. They invert the input signals, converting 0s to 1s and 1s to 0s, which is useful for various logic and signal processing tasks.

- #### Role of 74LS157 Quad 2-to-1 selectors/multiplexer

The 74LS157 IC has four 2-to-1 multiplexers that allow selecting one of two input signals based on a control signal. It enables data multiplexing and selection, crucial for efficient data routing in the computer.

- #### Role of 74LS173 4-bit D register

The 74LS173 IC is a 4-bit D-type register capable of storing data. It latches and holds the data at its inputs when a clock signal is received, allowing the CPU to read or write data as needed.

- #### Role of 74189 64-bit RAM

The 74189 IC expands memory capacity in the 8-bit computer by adding 64-bit RAM with parallel data storage. Allows for faster data transfer, modularity, and handling of larger programs. Interfaces with CPU through address and data buses.

- #### Role of 74LS245 8-bit bus transceiver

The 74LS245 IC is an 8-bit bidirectional bus transceiver used to enable data transfer between the computer's internal bus and external devices. It facilitates data exchange with peripherals and memory units outside the CPU.

Each of these ICs plays a specific role in the overall functioning of the computer, contributing to data processing, memory management, and communication within the system.
