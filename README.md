# 16-Bit 2-Stage RISC Pipeline Processor

## Design Architecture
<img src="/Figure/Processor_Arch.png">

## Modules
- Program Counter(PC)
- Decoder
- Shifter
- Arithmetic and Logic Unit (ALU)
- Register File(RF)
-  Instruction Memory(IMEM)
-  Data Memory(DMEM)
- SRAM

### Program Counter(PC)
All instructions start by using the contents of the program counter (PC) as the address to fetch the next instruction. The PC stores the current instruction address and calculates the address of the next sequential instruction.
|  Instruction |Next PC Value|
|--------------|-------------|
|**Bcond disp**        |PC <- PC + disp (sign ext.) or PC <- PC + 1|
|**Jcond Rdest**       |PC <- Rdest or PC <- PC + 1|
|**JAL** Rlink, Rdest  |Rlink <- PC + 1 and PC <- Rdest|
|Other Instruction     |PC <- PC + 1|

[The PC Verilog Code](Code/PC.v)


### Decoder
• Get instructions from IR + flags→control signals for execute stage

• Control bits for fetch

• Control signals for data memory

[The Decoder Verilog Code](Code/decode.v)

### Shifter
The shifter is a 16-bit Logical Left Shifter. The amount of shifting is positive between 0 and 15.

### Arithmetic and Logic Unit (ALU)
Arithmetic and Logic Unit (ALU) support consists of (i) ADD, (ii) AND, (iii) OR, and (iv) XOR.

The adder is designed as a carry-select adder, which duplicates and selects the adding block to reduce 38% of the propagation time compared to the carry ripple adder.
<img src="/Figure/carry_select.png">

### Register File(RF)
RF comprises a 16-word, 16-bit array of static RAM cells with read/write circuitry and a sense amplifier. It is implemented using the Master-Slaves latches method, which uses one master latch to supply data to 1 of the 16 slave latches for a particular write operation.
<img src="/Figure/RegisterFile.png">

### Instruction Memory(IMEM)
The IMEM stores the processor's instruction set. It is a 1024-word, 16-bit RAM.

### Data Memory(DMEM)
The DMEM stores the data from the processor. It is a 512-word, 16-bit RAM.

### SRAM
The design is a 10T SRAM with the same hierarchy as the DMEM. It is designed to be a computational unit that provides READ, WRITE, AND, and NOR instructions. The AND and NOR computation can be done inside SRAM instead of keeping moving data in and out of the memory.

## Layout
<img src="/Figure/layout_placement.png">

## Report
[16-Bit 2-Stage RISC Pipeline Processor Report](Final_Report.pdf)
