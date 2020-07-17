DSAGEN Components
===============================


Spatial Scheduling Libraries
-------------------------------------------
**config library**
  The configuration library contains mechanisms to specify a design
  space of DSA architectures.  

**scheduling library**
  The scheduling library provides a way to specify dataflow graphs, as well
  as tools to map these graphs onto the DSA architecture configuration. 

Simulation
-------------------------------------------
**ssim**
  ssim is a cycle-level simulator of a decoupled-spatial accelerator.  

**gem5**
  gem5 is a modular platform for computer-system architecture research, encompassing system-level architecture as well as processor microarchitecture.
  ssim is embedded within gem5, currently supporting integration with the inorder core (minor).

Associated Workloads
-------------------------------------------

External Suites
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**MachSuite:**
  `Machsuite <http://breagen.github.io/MachSuite/>`__ is a benchmark suite intended for accelerator-centric research.  A subset of workloads are implemented, both with manual and automatically compiled versions.

**PolyBench:**
  `PolyBench <https://github.com/bollu/polybench-c>`__ is a collection of simple benchmarks containing static control parts, primarily used for testing the compiler.

Internal Suites
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**DianNao:**
  Simple single-threaded convolution/pooling/classification kernels from `DianNao <https://doi.org/10.1145/2644865.2541967>`__ research paper.

**DSP:** 
  Digital signal processing workloads adapted from the `REVEL <https://doi.org/10.1109/HPCA47549.2020.00063>`__ work.

**Tests:** 
  Unit tests to verify the functionality of each module.

Toolchains
-------------------------------------------

**riscv-tools**
  A collection of software toolchains used to develop and execute software on the RISC-V ISA.
  
  This toolchain is largely unmodified, except for the assembler which can handle control instructions
  from the stream-ISA.

  Stream-Dataflow programs can be written in assembly, and compiled purely with the GNU riscv toolchain
  and spatial scheduler without need for the LLVM-based compiler.
    
**LLVM and Clang**
  LLVM is a collection of modular and reusable compiler and toolchain technologies.  Clang is
  a C language frontend for LLVM. 
 
  These tools are used for generating stream-dataflow programs from C-based source code with
  pragmas.


