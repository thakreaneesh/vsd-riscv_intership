# Decoding RISC-V Instructions: A Visual Guide

## Understanding I-Type, S-Type, B-Type, U-Type, and J-Type Instructions

---

## 📘 Introduction

RISC-V (Reduced Instruction Set Computer - V) is an open standard instruction set architecture (ISA) based on established reduced instruction set computing principles. Unlike proprietary ISAs, RISC-V is free and open, enabling unrestricted academic and commercial use without licensing fees. This has made RISC-V an attractive option for research, education, and industry applications, fostering innovation and development across various domains.

---

## 📌 Importance of Understanding Instruction Formats

Understanding instruction formats is crucial for several reasons:

- **Instruction Decoding:** Enables correct decoding of instructions, essential for CPU execution.
- **Pipeline Design:** Affects the design of the CPU pipeline for efficient execution stages.
- **Compiler Design:** Helps optimize code generation.
- **Debugging and Verification:** Aids in identifying issues related to instruction execution.
- **Extensibility and Customization:** Essential for creating and integrating custom instructions.

---

## 📚 Basics

### Instruction Types and Fields

RISC-V instructions are categorized by field organization:

- **R-type:** Register type
- **I-type:** Immediate type
- **S-type:** Store type
- **B-type:** Branch type
- **U-type:** Upper immediate type
- **J-type:** Jump type

### Opcode and Function Fields

- **Opcode:** Determines instruction type.
- **func3 / func7:** Specify operations within the instruction type.

Example: In R-type, `func3` and `func7` differentiate between `ADD` and `SUB`.

### Immediate Values and Registers

- **Immediate Values:** Encoded in specific fields (e.g., 12-bit for I-type).
- **Registers:** `rd`, `rs1`, `rs2` define destination and source registers.

---

## 🔍 Example - U-Type Instruction

**Instruction:** `lui x5, 0x12345`  
**Encoding:** 0x12345 in immediate field, `x5` in `rd` field  
**Execution:** Loads upper 20 bits of immediate into upper 20 bits of `x5`

---

## ➕ Arithmetic Instructions

- **ADD:** `ADD rd, rs1, rs2` → `rd = rs1 + rs2`
- **ADDI:** `ADDI rd, rs1, imm` → `rd = rs1 + imm`

---

## 🔣 Logical Instructions

- **AND, OR, XOR:** Bitwise operations  
  Example: `AND rd, rs1, rs2` → `rd = rs1 & rs2`

---

## 🔁 Branch Instructions

- **BEQ:** `BEQ rs1, rs2, offset` → Branch if `rs1 == rs2`
- **BNE:** `BNE rs1, rs2, offset` → Branch if `rs1 != rs2`

---

## 📥 Load and Store Instructions

- **LW:** `LW rd, offset(rs1)` → Load word from memory
- **SW:** `SW rs1, offset(rs2)` → Store word to memory

---

## 🧠 Special Instructions

- **AUIPC:** `AUIPC rd, imm` → `rd = PC + (imm << 12)`

---

## 🚀 Branch and Jump Instructions

- **Jump (J):** Unconditional branch to address
- **Branch (B):** Conditional branch based on comparison

---

## ⚙️ RV32I Extensions

Optional RISC-V ISA extensions:

- **M:** Integer multiplication and division
- **A:** Atomic instructions
- **F, D, Q:** Floating-point (32, 64, 128-bit)
- **C:** Compressed instructions

---

## 🧩 R-Type Instructions

Used for register-based arithmetic/logical operations.

**Fields:**
- `opcode`: e.g., `0110011` (integer reg-reg ops)
- `rd`: Destination register
- `funct3`: Operation specifier
- `rs1`, `rs2`: Source registers
- `funct7`: Extended specifier

---

## 🧮 I-Type Instructions

Covers immediate arithmetic, loads, and control operations.

**Immediate Extraction:**

Immediate = bits `[31:20]`

```c
uint32_t imm_i = (instruction & 0xFFF00000) >> 20;
