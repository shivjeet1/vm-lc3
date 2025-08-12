# Simple Virtual Machine (VM) Based on LC-3

A basic Virtual Machine emulating the LC-3 (Little Computer 3) architecture, a 16-bit instruction set architecture (ISA) commonly used for educational purposes to teach computer architecture and assembly programming.

This project implements a simple LC-3 VM, closely following the tutorial by Justin Meiners: [Writing a Simple Virtual Machine](https://www.jmeiners.com/lc3-vm/). The implementation includes all key features of the LC-3 and supports the complete instruction set.

---

## Features

- Executes LC-3 assembly programs in `.obj` format.
- Simulates:
  - Registers (8 general-purpose registers, PC, and condition flags).
  - Memory (addressable 16-bit words).
  - Input/Output (keyboard input and character output).
- Supports all 16 LC-3 instructions.
- Modular code design with separate files for memory, instruction execution, and I/O.
- **Testable with Example Binaries**:
  - Play the classic game **2048** using `2048.obj`.
  - Explore a basic rogue-like game using `rogue.obj`.

---

## LC-3 Architecture Overview

The LC-3 architecture is designed to be simple yet powerful for educational purposes. Below are the detailed components:

### **1. Word Size**
- **16-bit word size**: Every register, memory location, and instruction in the LC-3 is 16 bits wide.
  
### **2. Memory**
- **Address Space**: 65,536 (2^16) memory locations, with each storing a 16-bit word.
- **Memory-Mapped I/O**: Reserved memory locations for input/output devices, such as the keyboard and display.

### **3. Registers**
- **8 General-Purpose Registers**: `R0–R7` for temporary data.
- **Program Counter (PC)**: Points to the next instruction.
- **Condition Flags (N, Z, P)**: Indicate the result of the last operation (Negative, Zero, Positive).

### **4. Instruction Set Architecture (ISA)**
Supports 16 operations, including:
- **Arithmetic/Logic**: `ADD`, `AND`, `NOT`.
- **Data Movement**: `LD`, `ST`, `LEA`, etc.
- **Control**: `BR`, `JMP`, `JSR`, etc.
- **System/Trap**: I/O operations like `GETC`, `OUT`, `PUTS`.

Example 
```asm

   ADD: Resgister Mode
   +----+---+---+-+--+---+
   |0001|DR |SR1|0|00|SR2|
   +----+---+---+-+--+---+

   ADD: Immediate  Mode
   +----+---+---+-+------+
   |0001|DR |SR1|1| imm5 |
   +----+---+---+-+------+

   ADD R2 R0 R1    ; add the contents of R0 to R1 and store in R2.
   0001 001 000 0 00 001
```

### **5. Trap Routines**
Trap routines are subroutines for I/O defined in the program, such as:
- `GETC` (Read a character), `OUT` (Output a character), `HALT` (Stop execution).

For a complete ISA description, see the **Resources** below.

---

## Usage
This code is for **UNIX**-based systems (Linux, macOS) only.

1. Clone the repository:
   ```bash
   git clone https://github.com/shivjeet1/vm-lc3.git 
   ```

2.  1. Compile the project using `gcc`:
        ```bash
        gcc vm-lc-3.c -o vm-lc3
        ```
    2. Compile the project using `gcc`:
        ```bash
        gcc vm-lc-3.c
        ```

3.  1. Run the VM with an LC-3 program file:
       ```bash
       ./vm-lc3 program.obj
       ```
    2. Run the VM with an LC-3 program file:
       ```bash
       ./a.out program.obj
       ```

4. **Test the VM with Example Binaries**:
   - **2048 Game**:
     ```bash
     ./vm-lc3 2048.obj
     ```
   - **Rogue-like Game**:
     ```bash
     ./vm-lc3 rogue.obj
     ```
    ```[!NOTE]
> At the end, it all comes down on how you compile the program.
> If you compile as given at point 2.i then use the point 4 as it is else use ./a.out like 2.ii and 3.ii.
     
---

## File Descriptions

- **Core Files**:
  - `vm-lc-3.c`: Implements the main logic for decoding and executing LC-3 instructions.
  - `2048.obj` : Binary of 2048 game made in assembler for LC3 architecture.
  - `rogue.obj` : Binary of rogue(Pacman like game) made for LC3 architecture using Assembler.

---

## Credits

This project is based on and heavily inspired by the tutorial "[Writing a Simple Virtual Machine](https://www.jmeiners.com/lc3-vm/)" by Justin Meiners. The tutorial provides a step-by-step guide for implementing an LC-3 VM and is an excellent resource for learning about virtual machines and computer architecture.

- Readme is based on [chebanne-az][https://github.com/chebanne-az/lc3-vm/blob/main/README.md]
---

## Resources 
- [Writing a Simple Virtual Machine](https://www.jmeiners.com/lc3-vm/)
- [LC-3 ISA](https://www.jmeiners.com/lc3-vm/supplies/lc3-isa.pdf)



