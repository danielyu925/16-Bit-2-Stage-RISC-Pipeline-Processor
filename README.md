# 16-Bit 4-Stage RISC Pipeline Processor

The processor utilizes a 16-bit RISC instruction set. It consists of several components including the Program Counter (PC), Instruction Memory (IMEM), Decoder, Register File (RF), Shifter, Arithmetic Logic Unit (ALU), Data Memory (DMEM), and SRAM module.

The RF, Shifter, ALU, and SRAM are manually drawn layouts. The PC and Decoder layouts are designed using Cadence Innovus APR.

In this design, both the SRAM and DMEM are part of the same memory hierarchy. The SRAM is designed using a 10T (10-transistor) configuration and supports Boolean operations such as AND and NOR on the SRAM side. This enables the reduction of data transfer time within the memory system.
