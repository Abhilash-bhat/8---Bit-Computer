# ALU (Arithmetic and Logic Unit)

The **ALU**  in the 8-bit computer is a crucial component responsible for performing arithmetic and logical operations. It is designed to operate on **8-bit** binary data.

The ALU consists of various logic gates and circuits that enable it to execute operations such as:
- Addition
- Subtraction

## Components Used 

The components that were used to make the arithmetic and logic unit are specified below:
- 74LS86 Quad XOR gate 
- 74LS245 Octal bus transceiver 
- 74LS283 4-bit adder


## Working of the ALU

The ALU receives inputs from the computer's registers and carries out the specified operation based on control signals. It performs calculations and produces outputs that can be stored back in the registers or used for further processing.

By carefully configuring the control signals, the ALU can perform a wide range of operations, making it a versatile component of the computer system. Ben Eater's ALU design is based on a combination of combinatorial logic and sequential logic, ensuring accurate and efficient computation.

The ALU plays a vital role in enabling the computer to perform arithmetic calculations, logical comparisons, and data manipulation, contributing to the overall functionality of the 8-bit computer.

1. The ALU receives inputs from the computer's registers, which hold the operands for the desired operation.

2. The control signals specify the operation to be performed by the ALU. These control signals determine which logic gates and circuits are activated.

3. For arithmetic operations like addition and subtraction, the ALU uses a combination of XOR gates, AND gates, and OR gates to perform the binary arithmetic. The carry-in and carry-out signals are utilized to handle overflow in addition and borrowing in subtraction.

4. Logical operations such as logical AND, logical OR, and bitwise operations are implemented using appropriate combinations of logic gates.

5. For shifting operations, the ALU employs multiplexers to select the desired shift direction (left or right) and the number of shifts.

6. The ALU performs the specified operation on the inputs and generates the result.

7. Depending on the operation and the control signals, the ALU may also produce additional outputs such as carry-out signals, overflow flags, or zero flags to indicate specific conditions or results.

8. The output of the ALU can be stored back in the registers or used for further processing within the computer system.

9. The ALU operates synchronously with the clock signal, ensuring proper timing and synchronization with the rest of the computer's components.

10. By configuring the control signals appropriately, the ALU can perform a wide range of arithmetic and logical operations, providing versatility and computational capabilities to the 8-bit computer.

11. The ALU's modular design and combination of logic gates allow for flexibility and expandability, enabling enthusiasts to further customize and extend the ALU's functionality based on specific requirements or project goals.



