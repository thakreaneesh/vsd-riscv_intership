# Task 2: SPIKE Simulation & RISC-V Compiler Optimization Comparison

## Overview

This repository documents the steps and observations for Task 2 of the SPIKE RISC-V Simulation assignment. The goal was to compare the performance and machine code generation of a simple C program under different compiler optimization flags (`-O1` and `-Ofast`) using the RISC-V GCC toolchain and the SPIKE simulator.

---

## Task Summary

1. **Video Review**:
   - Reviewed the provided SPIKE simulation video to understand how to compile, simulate, and analyze RISC-V programs.

2. **C Program Used**:
   - The program used for this task is named `sum1ton.c`.
   - It calculates the sum of numbers from 1 to 110 and prints the result.
   - Code:
     ```c
     #include <stdio.h>

     int main() {
         int i, sum = 0, n = 110;
         for (i = 1; i <= n; ++i) {
             sum += i;
         }
         printf("\n ***********Sum of Numbers from 1 to %d is %d ***********\n", n, sum);
         return 0;
     }
     ```

3. **Compilation**:
   - Compiled the C code using RISC-V GCC with two optimization flags:
     ```bash
     riscv64-unknown-elf-gcc -O1 sum1ton.c -o sum1ton_O1
     riscv64-unknown-elf-gcc -Ofast sum1ton.c -o sum1ton_Ofast
     ```

4. **Object Dump Generation**:
   - Generated RISC-V object dumps to observe the machine instructions:
     ```bash
     riscv64-unknown-elf-objdump -d sum1ton_O1 > sum1ton_O1.dump
     riscv64-unknown-elf-objdump -d sum1ton_Ofast > sum1ton_Ofast.dump
     ```

5. **SPIKE Simulation**:
   - Executed the compiled object files in the SPIKE simulator to understand runtime behavior.
   - Debugger output showed assembly instructions like `lui`, `addi`, `mv`, and loop control instructions.
   - These instructions helped in understanding the control flow and optimization differences at the ISA level.

---

## Repository Contents

- `sum1ton.c` — The source C file.
- `sum1ton_O1.dump` — Object dump generated using `-O1` optimization.
- `sum1ton_Ofast.dump` — Object dump generated using `-Ofast` optimization.
- `Snapshots/` — Folder containing screenshots of:
  - Source code
  - Terminal output of compilation
  - Object dump and debugger output from SPIKE
- `README.md` — This file.

---

## Key Observations

- **Instruction Patterns**:
  - Both optimization levels showed typical RISC-V instructions like `lui`, `addi`, and control flow statements.
  - With `-Ofast`, redundant operations were removed, and some values were precomputed at compile time.

- **Performance Differences**:
  - `-Ofast` generated fewer instructions, resulting in potentially faster execution and more efficient loop unrolling or constant folding.

- **SPIKE Usefulness**:
  - Helped in visualizing how C code gets translated to RISC-V machine instructions.
  - Provided insight into the internal workings of compiled programs at the ISA level.

---

## Conclusion

This task provided practical experience in compiling and analyzing RISC-V code, comparing optimization levels, and using the SPIKE simulator to study runtime behavior. It deepened understanding of compiler optimizations and low-level instruction generation.

