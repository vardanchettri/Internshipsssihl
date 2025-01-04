# RISC-V INSTRUCTION TYPES

There are various types of instruction formats, which can be categorized into two main types: ***base instruction formats*** **&** ***immediate encoding variants***

but before that what is a instruction format.
***
**Instruction format:** The instruction formats are a sequence of bits (0 and 1) which when grouped, are known as fieldsand each field of the machine provides 
specific information to the CPU related to the operation and location of the data.They refer to the specific structure or layout of binary instructions used by a processor to perform operations and define how the bits in an instruction are divided 
and allocated to represent various components, such as the operation code (opcode), registers, memory addresses, and other relevant data.
***
***
### (1) BASE INSTRUCTION FORMATS:

In the RV32I (RISC-V 32-bit Integer) base Instruction Set Architecture (ISA), 
all instructions are 32 bits long and are classified into four formats: **R-type, I-type,  
S-type, and U-type**, each serving different operations like arithmetic, logic, memory access, and 
loading upper immediate values. Instructions must be aligned on a four-byte boundary, meaning 
their memory addresses should be multiples of 4. If an instruction is placed at an address 
like 0x1001 or 0x1003, which is not divisible by 4, it is considered misaligned, triggering an 
Instruction-Address-Misaligned Exception. This exception signals an error, and the processor 
either raises an exception to handle it or takes an unconditional jump to correct the address. 

![a](https://github.com/user-attachments/assets/56fa2e47-95b4-4d79-bd3c-c831fe0c2a6a)

###### In the RISC-V architecture, the instruction format consists of several fields, each serving a specific purpose. The source registers are denoted as rs1 and rs2 (these registers hold the input values required for an operation). The destination register is rd, which holds the result of the operation performed by the instruction. The funct3 is a 3-bit field within the instruction that helps determine the specific variant of an operation, while funct7 is a 7-bit field providing additional information about the operation. The opcode specifies the type of operation to be performed by the processor. The imm[x:y] notation refers to an immediate value, which is a constant value embedded directly within the instruction; the value is derived from the bits in the instruction from position y to position x. To simplify decoding, the RISC-V instruction set architecture (ISA) keeps the positions of the source registers (rs1 and rs2) and the destination register (rd) consistent across all instruction formats. This uniformity in layout allows the processor to quickly decode and execute instructions, enhancing efficiency.
***
### (2) Immediate Encoding Variants :

There are a further two variants of the instruction 
formats based on the handling of immediates namely B-Type and J-Type
  
  [ B-type and J-type immediate encodings are often discussed more frequently because 
of their use in branch and jump operations, respectively. However, immediates 
exist in various other instruction formats (I-type, S-type, U-type) 
as well, and each has its own way of encoding the immediate value.]




![b](https://github.com/user-attachments/assets/b29efb41-09e0-4834-9d68-1392293f4544)
![c](https://github.com/user-attachments/assets/934f0c58-f008-47c7-9fb8-780c3c7ef429)


***
***
**(i) R- TYPE**

The R-Type is an instruction format in the RISC-V architecture used for performing arithmetic and logical operations between registers. It is structured as follows:

* opcode (6-0): This field identifies the operation to be performed, such as addition, subtraction, AND, OR, etc.

* rd (11-7): This field specifies the destination register where the result of the operation will be stored after execution.

* funct3 (14-12): This 3-bit field helps specify the exact operation within the given opcode category (e.g., distinguishing between ADD and SUB operations).

* rs1 (19-15): The first source register that holds one of the operands for the operation.

* rs2 (24-20): The second source register, which contains the other operand for the operation.

* funct7 (31-25): This 7-bit field provides additional operation details, allowing for variations of instructions that share the same opcode and funct3 values.

***This format allows RISC-V to execute a wide range of arithmetic and logical operations efficiently, using different combinations of the fields to define the exact operation.***
***
**(ii) I-TYPE**

The I-Type instruction format in RISC-V is used for operations that involve a combination of immediate values and registers. The format is organized as follows:

*opcode (6-0): This field determines the specific operation to execute, such as loading data or adding an immediate value.

* rd (11-7): This indicates the destination register where the result of the operation will be stored after execution.

* funct3 (14-12): A 3-bit field that specifies the type of operation within the broader opcode category (for example, differentiating between ADDI and LW operations).

* rs1 (19-15): The first source register that holds one of the operands used in the operation.

* imm[11:0] (31:20): A 12-bit immediate value, which is a constant directly embedded within the instruction. This constant serves as one of the operands in the instruction.

  ***This instruction format enables RISC-V to execute
  operations that involve immediate values, such as adding
  a constant to a register or performing memory load operations,
  efficiently integrating constants within the instruction itself***.
***
**(iii) S-TYPE**

  he S-Type instruction format in RISC-V is used for operations involving store instructions, where data is written to memory. The structure is as follows:

* opcode (6-0): Specifies the operation to be performed, such as store word or store half-word.

* funct3 (14-12): A 3-bit field that defines the specific store operation (e.g., distinguishing between SW and SH).

* rs1 (19-15): The source register containing the base address for memory access.

* rs2 (24-20): The source register containing the data to be stored in memory.

* imm[11:5] (31:25) and imm[4:0] (11:7): The immediate value is split into two parts. The immediate represents the offset to the memory address and is used in combination with the base address from rs1.


  ***The S-Type format is specifically designed for memory store operations, where an immediate offset is added to the address in rs1, and the data in rs2 is written to the resulting address in memory.***
***
**(iv) U-TYPE**

The U-Type instruction format in RISC-V is used for operations that involve large immediate values. The structure is as follows:

* opcode (6-0): Specifies the operation to be performed, such as Load Upper Immediate (LUI) or Add Upper Immediate to PC (AUIPC).

* rd (11-7): The destination register where the result of the operation will be stored.

* imm[31:12] (31:12): A 20-bit immediate value used for loading large constants. This value is shifted left by 12 bits and placed in the upper portion of the register.


  ***The U-Type format is primarily used for operations that require large constant values, allowing the instruction to load a large immediate value into the upper 20 bits of a register (e.g., LUI).***
***
**(v) B-TYPE**
The B-Type instruction format in RISC-V is used for branch operations that determine the control flow of a program. The structure is as follows:

* opcode (6-0): Specifies the branch operation, such as branch if equal (BEQ) or branch if not equal (BNE).

* funct3 (14-12): A 3-bit field that specifies the condition of the branch (e.g., comparing equality, inequality, etc.).

*  rs1 (19-15): The first source register, which is compared to the second source register for the branch condition.

* rs2 (24-20): The second source register, which is compared to rs1 for the branch decision.

* imm[12] (31:31), imm[10:5] (30:25), imm[4:1] (11:8), and imm[11] (7:7): The immediate value is used to calculate the offset for the branch. The instruction uses these fields to construct the target address for the branch.


  ***The B-Type format is used for conditional branching, where the program’s control flow depends on a condition involving two registers, and the target address is calculated using an immediate offset.***

***
**(vi) J-TYPE**

The J-Type instruction format in RISC-V is used for unconditional jump operations. The structure is as follows:

* opcode (6-0): Specifies the jump operation, such as Jump and Link (JAL).

* rd (11-7): The destination register, where the return address (the address of the next instruction) is stored.

* imm[20] (31:31), imm[10:1] (30:21), imm[11] (20:20), and imm[19:12] (19:12): The immediate value used to calculate the target address for the jump. The instruction fields are combined to form the full 20-bit immediate value, which is then used to determine the jump target relative to the current instruction.


  ***The J-Type format is primarily used for unconditional jumps, such as the JAL instruction, which allows for long-range jumps by using a large immediate value to calculate the jump address.***
***
***
















