# **CSE 141L Computer Architecture Design Project**

This is our computer architecutre project designed over 10 weeks, a specialized custom RISC processor made to succesfully run 3 given programs. Before writing the code for our project, extensive planning of our ISA and specifications were made in preparation. Inside the repo, the hardware and software for our processor can be found, alongside the individual programs designed to run with it. Our machine is an accumulator with an ISA based off of MIPS, but with various limitations placed on it such as an:
- 8-bit Program Counter
- 16 registers
- 9-Bit fixed-length instructions
- 8-Bit data paths
- Overall simplified and reduced instruction set

### Running/Synthesizing the Processor ###
The processor can be synthesized on Quartus by taking all of the files in the HardwareV2 folder as a project and synthesized as is. We used EDA playground to compile/simulate our processor as opposed to ModelSim/Questa for simplicity. Similarly to synthesizing, all of the files in HardwareV2 and the assembly bin files in the assembly-programs folder for all 3 programs are needed to simulate and connect our processor with the test benches. The test benches provided are found in our test-programs folder and can be used to test how our processor executes the given programs. On EDA playground, the processor can be compiled and then simulated with the test benches for each program.

### Instruction Operations ###
Accumulator Register = R0
|  Name  | Bit Breakdown |    Notes    |
| ------ | ------------- | ----------- |
| LDI | 1_XXXXX_XXXX | Loads Immediate value that is 8 bits long into accumulator register R0 |
| ADD | 0_0000_XXXX | R0 = R0 + R(XXXX) |
| SUB | 0_0001_XXXX | R0 = R0 - R(XXXX) |
| AND | 0_0010_XXXX | Bitwise AND, R0 = R0 AND R(XXXX) |
| OR | 0_0011_XXXX | Bitwise OR, R0 = R0 OR R(XXXX) |
| NOT | 0_0100_XXXX | Bitwise NOT , R(XXXX) = ~R(XXXX) |
| LSR | 0_0101_XXXX | Logical Right Shift by XXXX bits, R0 >> XXXX |
| MOVA | 0_0110_XXXX | R(XXXX) = Accumulator |
| MOVR | 0_0111_XXXX | Accumulator = R(XXXX) |
| LOAD | 0_1000_XXXX | Load from Mem(R(XXXX)) to Accumulator |
| STR | 0_1001_XXXX | Store Accumulator to mem(R(XXXX)) |
| BLT | 0_1010_XXXX | Branches PC to value stored in R(15) if accumulator < R(XXXX) |
| BGT | 0_1011_XXXX | Branches PC to value stored in R(15) if accumulator > R(XXXX) |
| BEQ | 0_1100_XXXX | Branches PC to value stored in R(15) if accumulator == R(XXXX) |
| BNE | 0_1101_XXXX | Branches PC to value stored in R(15) if accumulator != R(XXXX) |
| B | 0_1110_XXXX | Branches PC to value stored in R(XXXX) |
| XOR | 0_1111_XXXX | Bitwise XOR, R0 = R0 XOR R(XXXX) |

### RTL Schematic ###
![Image of RTL Schematic](https://github.com/ed-see/cse-141l/blob/main/Images/RTL141.png)

### Programs 1-3 ###
Program 1: Closest Pair -- Finds the smallest and largest Hamming distances among all pairs of
values in an array of 16 bytes. Assumes all values are 8-bit integers. The array of integers starts at location 0. Writes the minimum distance in location 16 and the maximum distance in location 17

Program 2: 2-Term Product -- Finds the product of two two’s complement numbers, ie, A * B. The operands are found in memory locations 0 (A), and 1 (B). The result is written
into locations 3 (high bits) and 2 (low bits)

Program 3: 3-Term Product -- Finds the product of three two’s complement numbers, ie, A * B * C. The operands are found in memory locations 0 (A), and 1 (B), and 2 (C). The result is written into locations 5 (highest bits), 4 (middle bits), and 3 (low bits). 

### Collaborators ###
- Edgar Seecof: EdtheEggHead
- Yves Mojica: Yves-M22
