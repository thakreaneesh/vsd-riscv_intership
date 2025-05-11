# Task 2: SPIKE Simulation & RISC-V Compiler Optimization Comparison

## Overview

This repository contains the results and observations from Task 2 of the SPIKE RISC-V Simulation assignment. The objective was to compare the performance and object code output of a simple C program compiled using two different optimization flags: `-O1` and `-Ofast`.

## Task Breakdown

1. **Simulation Video Review**:
   - Watched and understood the SPIKE Simulation video (link provided in the task instructions).
   - Learned how to use SPIKE with RISC-V GCC and different optimization flags.

2. **C Program Implementation**:
   - Wrote a simple C program (`sample.c`) that performs basic arithmetic and loop operations.
   - The goal was to observe how optimization flags affect the generated machine code.

3. **Compilation**:
   - Compiled the C code using the following optimization flags:
     - `-O1`
     - `-Ofast`
   - Commands used:
     ```bash
     riscv64-unknown-elf-gcc -O1 sample.c -o sample_O1
     riscv64-unknown-elf-gcc -Ofast sample.c -o sample_Ofast
     ```

4. **Object Dump Generation**:
   - Generated RISC-V object dumps using:
     ```bash
     riscv64-unknown-elf-objdump -d sample_O1 > sample_O1.dump
     riscv64-unknown-elf-objdump -d sample_Ofast > sample_Ofast.dump
     ```

5. **Snapshot Upload**:
   - Screenshots of the compiled code and object dumps have been uploaded to this repository.
   - These snapshots show the differences in the machine code produced by each optimization level.

## Repository Contents

- `sample.c`: The simple C program used for compilation.
- `sample_O1.dump`: RISC-V object dump for the code compiled with `-O1`.
- `sample_Ofast.dump`: RISC-V object dump for the code compiled with `-Ofast`.
- `Snapshots/`: Folder containing screenshots of:
  - Terminal commands and output
  - Code and dump files opened in editor or viewer
- `README.md`: This documentation file.

## Key Observations

- The `-Ofast` flag produced more aggressive optimizations, reducing loop iterations and instruction count.
- Instruction reordering and removal of redundant operations were observed in the `-Ofast` object dump.
- The comparison helps understand how compiler optimizations affect code efficiency on the RISC-V architecture.

---

*This task helped gain hands-on experience with RISC-V toolchains, optimization flags, and object code analysis using SPIKE simulation.*
