# Smart ALU

## Overview

This project is focused on designing and implementing a circuit that combines both combinational and sequential logic to create an **Arithmetic Logic Unit (ALU)** and a **tester**. The tester utilizes a random sequence to validate the functionality of the ALU.

## Key Components

### 1. Arithmetic Logic Unit (ALU)

The ALU is responsible for performing operations based on a provided operation code (opcode). It takes two 2-bit inputs and produces a 4-bit output according to the opcode. The operations are defined as:

| Opcode | Operation   | Output Description         |
| ------ | ----------- | -------------------------- |
| 000    | Add         | `Output = Input1 + Input2` |
| 001    | Subtract    | `Output = Input1 - Input2` |
| 010    | Multiply    | `Output = Input1 * Input2` |
| 011    | Divide      | Quotient and Remainder     |
| 100    | Bitwise AND | `Output = Input1 & Input2` |
| 101    | Bitwise XOR | `Output = Input1 ^ Input2` |
| 110    | Pass Input2 | `Output = Input2`          |
| 111    | Modulo      | `Output = Input1 % Input2` |

#### Additional Features

- **Zero Flag**: A flag that is set to 1 if the ALU output is 0.
- **Division/Modulo Special Case**: If `Input2` is 0, the output is set to `1111` to handle division by zero.

### 2. Binary Sequence Generator

A module is designed to generate the binary sequence:

```
1110100 1100101 1010110 1000111 0111000 0101001 0011010 0001011
```

This sequence is used to test the ALU operations.

### 3. Multiplexer

A 2-to-1 multiplexer is implemented to select the output source for the ALU. The selection signal determines whether the output comes from the Binary Sequence Generator or manual user input.
