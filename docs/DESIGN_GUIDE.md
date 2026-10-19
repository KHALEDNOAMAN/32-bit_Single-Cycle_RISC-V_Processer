# 32-bit RISC-V Processor - Design Guide

## Architecture Overview
```
PC --> Instruction Memory --> Decode --> Register File --> ALU --> Data Memory --> Writeback
                               |            |                        |
                          Control Unit   Immediate Gen          MUX Select
```

## Supported Instructions
| Type | Instructions |
|------|-------------|
| R-Type | ADD, SUB, AND, OR, XOR, SLL, SRL, SLT |
| I-Type | ADDI, ANDI, ORI, LW, JALR |
| S-Type | SW |
| B-Type | BEQ, BNE, BLT, BGE |
| J-Type | JAL |
| U-Type | LUI, AUIPC |

## Module Hierarchy
| Module | Function |
|--------|----------|
| top.v | Top-level integration |
| pc.v | Program Counter |
| instr_mem.v | Instruction Memory |
| reg_file.v | 32x32 Register File |
| alu.v | Arithmetic Logic Unit |
| control.v | Control Unit + ALU Decoder |
| data_mem.v | Data Memory |

## Simulation
```bash
iverilog -o sim src/*.v sim/testbench.v
vvp sim
gtkwave dump.vcd
```