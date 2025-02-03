# Samsung-RISCV
The program is centered around the RISC-V architecture and leverages open-source tools to provide hands-on learning in VLSI chip design and RISC-V concepts. The internship is guided by the esteemed instructor, Mr. Kunal Ghosh.

## Profile Overview

Name: G S Monish Yadav

College: Vidyavardhaka College of Engineering

Email ID: monishyadav@zohomail.in

GitHub Profile: monu112004

LinkedIn Profile: www.linkedin.com/in/g-s-monish-yadav-23262b266

<details>
<summary><b>Task 1:</b> Task 1: Review lab videos on C programming and RISC-V architecture. Perform the task of compiling C code using both the GCC compiler and the RISC-V compiler, demonstrating an understanding of the compilation process for each.simulator</summary>   
<br>

## C and RISC-V Based Labs

This repository demonstrates the processes involved in compiling C programs and generating assembly code using both a standard GCC compiler and a RISC-V GCC compiler. It includes comprehensive steps and explanations to guide users through each stage of the compilation and debugging workflow.

## C Language-Based Lab

### Steps to Compile a .c File on Your Machine:

1. Open the bash terminal and navigate to the directory where you want to create your file.
2. Use the following command to create and edit a new .c file:
   ```sh
   gedit sum_1ton.c
![3](https://github.com/user-attachments/assets/0e762cb5-cbdf-495e-aaec-0dea9aae3aa1)

### Steps to Compile a .c File on Your Machine:
 ```sh
 gcc sum_1ton.c
 ./a.out
 # Compilation and execution complete.
 ```
![2](https://github.com/user-attachments/assets/5712cf49-d372-467e-9ace-425a3741b7b4)
## RISC-V Based Lab

### Steps to Compile Using RISC-V GCC Compiler:
1. Ensure the RISC-V GCC compiler is installed and accessible on your system.
2. Verify the .c file contents using the cat command:
``` sh
cat sum_1ton.c
```
3. Compile the C program for RISC-V architecture using:
``` sh
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
```
4. Disassemble the object file to view its assembly code using:
``` sh
riscv64-unknown-elf-objdump -d sum_1ton.o
```
5. Use /main in the terminal to locate the main function in the assembly output.
![4](https://github.com/user-attachments/assets/abbb078b-bee3-452d-9e04-0f0d61ba42bf)
### Explanation of Key Commands and Options: 
1. -mabi=lp64: Specifies the Application Binary Interface (ABI) for 64-bit integers, pointers, and long data types, suitable for 64-bit RISC-V architecture.

2. -march=rv64i: Indicates the 64-bit RISC-V base integer instruction set architecture.

3. -O1: Enables basic optimization for better performance without significantly increasing compilation time.

4. riscv64-unknown-elf-objdump: A tool for disassembling RISC-V binaries to examine the code structure and debug it effectively.
</details>

<details>   
<summary><b>Task 2:</b> Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler simulator</summary>   
<br>
   
#  RISC-V ISA Simulation with SPIKE
This repository provides instructions for setting up and using SPIKE, a RISC-V ISA simulator, along with the Proxy Kernel (pk) for program execution. Follow the steps below to install the necessary tools, run simulations, and debug RISC-V programs effectively.

##  What is SPIKE?
SPIKE is an open-source RISC-V ISA simulator written in C++. It emulates a RISC-V core and cache system, enabling developers to test RISC-V programs without hardware. SPIKE supports running standalone programs as well as operating systems like Linux

## Testing the SPIKE Simulator
To validate the setup, compile and execute a sample program (sum_1ton.c) using both the GCC and RISC-V compilers.
### Using GCC Compiler:
``` sh
gcc product.c  
./a.out
```
![VirtualBox_vsdworkshop_13_01_2025_20_43_22](https://github.com/user-attachments/assets/e20f695b-6839-42d1-9f3f-7835fb7b8d7f)

### Using RISC-V Compiler:
``` sh
spike pk product.o
```
## Analyzing the Assembly Code
### Objdump Analysis:
Generate the assembly code with the following command:
``` sh
riscv64-unknown-elf-objdump -d sum_1ton.o | less
```
![VirtualBox_vsdworkshop_13_01_2025_20_43_47](https://github.com/user-attachments/assets/04a7db80-2d33-42ed-bafd-77a29c09d413)

### Debugging with SPIKE:
1. Open the debugger using the command:
``` sh
spike -d pk product.o
```
2. Perform debugging operations in the terminal.
   
## Optimization Levels
Snapshots of RISC-V objdump at different optimization levels (-O1 and -Ofast) provide insights into how compiler optimizations affect the generated assembly code. Use these options during compilation to analyze the differences:

-O1 Optimization

-Ofast Optimization

![VirtualBox_vsdworkshop_13_01_2025_20_42_05](https://github.com/user-attachments/assets/68908728-8b0a-405b-8b9c-19f3cc09741b) 

</details>
<details>
<summary><b>Task 3:</b> The task is to determine the instruction type for each of the provided instructions and provide their corresponding 32-bit instruction codes in the appropriate format.format</summary>

# Understanding RISC-V and Its Instruction Formats

## What is RISC-V?
RISC-V is an open-source Instruction Set Architecture (ISA) that enables developers to design processors tailored to specific applications. Based on Reduced Instruction Set Computer (RISC) principles, RISC-V represents the fifth generation of processors built on this concept. Its open and free nature means developers can utilize RISC-V without purchasing licenses, making it a compelling alternative to proprietary processor technologies.

## Instruction Formats in RISC-V
The instruction format of a processor defines how machine language instructions are structured for execution. These instructions are composed of binary data (0s and 1s), each segment providing details about data location and operations to be performed. In RISC-V, there are six primary instruction formats:

1. **R-format**
2. **I-format**
3. **S-format**
4. **B-format**
5. **U-format**
6. **J-format**
<img width="772" alt="instructions_types" src="https://github.com/user-attachments/assets/d6c2154d-57bb-44cc-a4a2-b5cd4480c46f" />

Let’s examine each format in detail.

---

### 1. R-type Instruction
R-type (Register-type) instructions operate on registers rather than memory locations. These are used for arithmetic and logical operations. Each instruction is 32 bits and divided into six fields:

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rd         | 5 bits| Destination register                  |
| func3      | 3 bits| Specifies the type of operation       |
| rs1        | 5 bits| First source register                 |
| rs2        | 5 bits| Second source register                |
| func7      | 7 bits| Additional operation specification    |

#### Example: ADD r9, r2, r5
- **Operation:** Adds values in registers r2 and r5, storing the result in r9.
- **Field Breakdown:**

  - Opcode: `0110011`
  - rd (Destination): `r9` -> `01001`
  - rs1 (Source 1): `r2` -> `00010`
  - rs2 (Source 2): `r5` -> `00101`
  - func3: `000`
  - func7: `0000000`
- **32-bit Instruction:** `0000000_00101_00010_000_01001_0110011`


#### Example: XOR r10, r1, r4
- **Operation:** XOR operation between r1 and r4, result in r10.
- **Field Breakdown:**

  - Opcode: `0110011`
  - rd (Destination): `r10` -> `01010`
  - rs1 (Source 1): `r1` -> `00001`
  - rs2 (Source 2): `r4` -> `00100`
  - func3: `100`
  - func7: `0000000`
- **32-bit Instruction:** `0000000_00100_00001_100_01010_0110011`


#### Example: SLT r11, r2, r4
- **Operation:** Sets r11 to 1 if r2 < r4; otherwise, sets r11 to 0.
- **Field Breakdown:**

  - Opcode: `0110011`
  - rd (Destination): `r11` -> `01011`
  - rs1 (Source 1): `r2` -> `00010`
  - rs2 (Source 2): `r4` -> `00100`
  - func3: `010`
  - func7: `0000000`
- **32-bit Instruction:** `0000000_00100_00010_010_01011_0110011`

![r type](https://github.com/user-attachments/assets/d1be72f1-b550-44cb-8e39-7be69fa91379)

---

### 2. I-type Instruction
I-type (Immediate-type) instructions use a register and an immediate (constant) value. These are typically used for load and immediate operations.

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rd         | 5 bits| Destination register                  |
| func3      | 3 bits| Specifies the type of operation       |
| rs1        | 5 bits| Source register                       |
| imm[11:0]  | 12 bits| Immediate value                      |

#### Example: ADDI r12, r4, 5
- **Operation:** Adds immediate value 5 to the value in r4 and stores it in r12.
- **Field Breakdown:**
  - Opcode: `0010011`
  - rd (Destination): `r12` -> `01100`
  - rs1 (Source): `r4` -> `00100`
  - imm[11:0] (Immediate): `000000000101`
  - func3: `000`
- **32-bit Instruction:** `000000000101_00100_000_01100_0010011`

![i type](https://github.com/user-attachments/assets/4aab8842-63ca-4953-afe9-c174affab3d2)

---

### 3. S-type Instruction
S-type (Store-type) instructions store register values into memory locations.

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rs1        | 5 bits| Base address register                 |
| rs2        | 5 bits| Source register                       |
| imm[11:5]  | 7 bits| Upper immediate value                  |
| imm[4:0]   | 5 bits| Lower immediate value                  |
| func3      | 3 bits| Specifies the type of operation       |

#### Example: SW r3, 2(r1)
- **Operation:** Stores the value in r3 into the memory at the address `r1 + 2`.
- **Field Breakdown:**
  - Opcode: `0100011`
  - rs1 (Base Address): `r1` -> `00001`
  - rs2 (Source): `r3` -> `00011`
  - imm[11:5] (Upper Immediate): `0000000`
  - imm[4:0] (Lower Immediate): `00010`
  - func3: `010`
- **32-bit Instruction:** `0000000_00011_00001_010_00010_0100011`

![s type](https://github.com/user-attachments/assets/174deda1-19be-455b-90f1-05416c4132ef)

---

### 4. B-type Instruction
B-type (Branch-type) instructions handle branching based on conditions.

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rs1        | 5 bits| Source register 1                      |
| rs2        | 5 bits| Source register 2                      |
| imm[12|10:5|4:1|11] | 13 bits| Branch offset                      |
| func3      | 3 bits| Specifies the condition for branching |

#### Example: BNE r0, r1, 20
- **Operation:** Branches to the address `PC + 20` if r0 is not equal to r1.
- **Field Breakdown:**
  - Opcode: `1100011`
  - rs1: `r0` -> `00000`
  - rs2: `r1` -> `00001`
  - imm[12|10:5|4:1|11]: `0000010100`
  - func3: `001`
- **32-bit Instruction:** `0000000_00001_00000_001_10100_1100011`

#### Example: BEQ r0, r0, 15
- **Operation:** Branches to the address `PC + 15` if r0 equals r0 (always true).
- **Field Breakdown:**
  - Opcode: `1100011`
  - rs1: `r0` -> `00000`
  - rs2: `r0` -> `00000`
  - imm[12|10:5|4:1|11]: `000001111`
  - func3: `000`
- **32-bit Instruction:** `0000000_00000_00000_000_01111_1100011`

![b type](https://github.com/user-attachments/assets/4be3dedf-fabc-4665-995b-0bdc9f8104c4)

---

### 5. U-type Instruction
U-type (Upper Immediate) instructions load immediate data into the destination register.

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rd         | 5 bits| Destination register                  |
| imm[31:12] | 20 bits| Upper immediate value                  |

![u type](https://github.com/user-attachments/assets/84fdadcc-a99c-4d9c-a0d5-b3bb865f1983)

---

### 6. J-type Instruction
J-type (Jump-type) instructions implement jump operations, often used for loops.

#### Structure:

| Field Name | Size  | Description                            |
|------------|-------|----------------------------------------|
| Opcode     | 7 bits| Determines the instruction type        |
| rd         | 5 bits| Destination register                  |
| imm[20|10:1|11|19:12] | 20 bits| Jump offset                        |

![j type](https://github.com/user-attachments/assets/5dbe1d45-4357-4816-bd3f-9b7f74c9d31a)

---

# RISC-V 15 Unique Instructions and Their 32-Bit Machine Codes

This repository contains a list of 15 unique RISC-V instructions extracted from the assembly code along with their corresponding 32-bit instruction codes. These instructions cover different instruction formats, such as **U-type**, **I-type**, **J-type**, **B-type**, and **R-type**.

![ss](https://github.com/user-attachments/assets/d6bb46fa-4fb4-4bd7-9e02-eaa5399a9ece)


## List of Instructions

1. **`lui a0, 0x21` (Load Upper Immediate)**
   - **Opcode**: `0110111` (LUI)
   - **Format**: U-type
   - **Machine Code**: `0x00021537`
   - **Instruction Binary**: `00000000001000010001000000010011`

2. **`li a3, 50` (Load Immediate)**
   - **Opcode**: `0010011` (ADDI)
   - **Format**: I-type
   - **Machine Code**: `0x03200693`
   - **Instruction Binary**: `00000011001000000000011010010011`

3. **`li a2, 5` (Load Immediate)**
   - **Opcode**: `0010011` (ADDI)
   - **Format**: I-type
   - **Machine Code**: `0x00500613`
   - **Instruction Binary**: `00000000010100000000001110010011`

4. **`li a1, 10` (Load Immediate)**
   - **Opcode**: `0010011` (ADDI)
   - **Format**: I-type
   - **Machine Code**: `0x00a00593`
   - **Instruction Binary**: `00000000101000000000001110010011`

5. **`addi a0, a0, 352` (Add Immediate)**
   - **Opcode**: `0010011` (ADDI)
   - **Format**: I-type
   - **Machine Code**: `0x16050513`
   - **Instruction Binary**: `00000001011100010000000000010011`

6. **`j 103f4` (Jump)**
   - **Opcode**: `1101111` (JAL)
   - **Format**: J-type
   - **Machine Code**: `0x3300006f`
   - **Instruction Binary**: `00000000011000001100000001101111`

7. **`auipc a5, 0xffff0` (Add Upper Immediate to PC)**
   - **Opcode**: `0010111` (AUIPC)
   - **Format**: U-type
   - **Machine Code**: `0xffff0797`
   - **Instruction Binary**: `11111111111100000111000001111001`

8. **`addi a5, a5, -200` (Add Immediate)**
   - **Opcode**: `0010011` (ADDI)
   - **Format**: I-type
   - **Machine Code**: `0xf3878793`
   - **Instruction Binary**: `11111111111100000011111000010011`

9. **`beqz a5, 100e0` (Branch if Equal to Zero)**
   - **Opcode**: `1100011` (BEQ)
   - **Format**: B-type
   - **Machine Code**: `0x00078863`
   - **Instruction Binary**: `00000000000001011111000001100011`

10. **`ret` (Return)**
    - **Opcode**: `1101111` (JALR)
    - **Format**: I-type
    - **Machine Code**: `0x00008067`
    - **Instruction Binary**: `00000000000000000000000000001111`

11. **`jal ra, 102d4` (Jump and Link)**
    - **Opcode**: `1101111` (JAL)
    - **Format**: J-type
    - **Machine Code**: `0x1d4000ef`
    - **Instruction Binary**: `00000000001011010000000001101111`

12. **`auipc a0, 0x0` (Add Upper Immediate to PC)**
    - **Opcode**: `0010111` (AUIPC)
    - **Format**: U-type
    - **Machine Code**: `0x00000517`
    - **Instruction Binary**: `00000000000000000000000000111001`

13. **`addi a0, a0, 272` (Add Immediate)**
    - **Opcode**: `0010011` (ADDI)
    - **Format**: I-type
    - **Machine Code**: `0x11050513`
    - **Instruction Binary**: `00000001000001000000000000010011`

14. **`j 1019c` (Jump)**
    - **Opcode**: `1101111` (JAL)
    - **Format**: J-type
    - **Machine Code**: `0x0c00006f`
    - **Instruction Binary**: `00000000000011010000000001101111`

15. **`jal ra, 1019c` (Jump and Link)**
    - **Opcode**: `1101111` (JAL)
    - **Format**: J-type
    - **Machine Code**: `0x090000ef`
    - **Instruction Binary**: `00000000000011010000000001101111`
</details>

<details>
<summary><b>Task 4:</b> Task 4: Conduct a functional simulation experiment using the RISC-V Core Verilog netlist and testbench, and analyze the resulting waveforms.simulator</summary> 
<br>
   
# RISC-V Verilog Simulation

This repository contains Verilog code to simulate a simple RISC-V design. Follow the instructions below to simulate the design and generate waveforms.

---

## Prerequisites

Ensure the following tools are installed on your system:

1. **Icarus Verilog** - For compiling and simulating the Verilog code.
2. **GTKWave** - For viewing the waveform of the simulation.

---

## File Structure

The repository includes the following files:

- `iiitb_rv32i.v` - The main Verilog design file.
- `iiitb_rv32i_tb.v` - The testbench file for the design.
- `README.md` - This file.

---

## Simulation Steps

Follow these steps to run the simulation and view the waveform:

### 1. Clone the Repository

Clone the repository to your local system:
``` sh
git clone https://github.com/monu112004/samsung-riscv.git
cd samsung-riscv
```
### 2. Compile the Verilog Code   
``` sh
iverilog -o iiitb_rv32i_sim iiitb_rv32i.v iiitb_rv32i_tb.v
```
This will create an executable file named iiitb_rv32i_sim.
### 3. Run the Simulation
``` sh
./iiitb_rv32i_sim
```
### 4. View the Waveform
``` sh
gtkwave iiitb_rv32i.vcd
```
![image](https://github.com/user-attachments/assets/6e3d4a0a-baf4-44a7-b638-383239e5ee1d)

### Signal Analysis
The waveform includes the following key signals:

clk: The clock signal driving the design.

NPC [31:0]: The next program counter value.

WB_OUT [31:0]: The write-back output signal.

RN: A register or control signal (usage depends on your design).

#### Observations from the Waveform

The clk signal toggles periodically to synchronize the design.

The NPC value increments, indicating instruction execution.

The WB_OUT signal changes at specific intervals, corresponding to write-back operations.

The RN signal may represent a register value or an internal control flag.
