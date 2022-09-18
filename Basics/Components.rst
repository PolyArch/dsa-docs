DSAGEN Components
===============================

Software Stack
---------------------
In term of functionality, the compilation of decoupled-spatial architecture can be separated into two aspects,
host control command, and spatial mapping. We develop a spatial scheduler to map the dataflow graph onto
the spatial architecture, and this is available in repo **spatial-scheduler**. Refer [placeholder] for more
details on the spatial architecture programming interface and mapping.

In term of programming interface, we expose both manually embedded assembly code, and high-level language 
programming interface. We use RISCV toolchains to extend the ISA encoding for our decoupled-spatial architecture.
The ISA encoding patch as well as the macro intrinsics are available in repo **dsa-riscv-ext**.
The patch will be applied on **riscv-gnu-toolchain** (as a part of our **chipyard** repo). We use riscv-gnu-toolchain
for binary generation.

In order to provide a productive programming interface, we define pragma hints (refer [placeholder] for more
detials). We extend the Clang frontend to parse and encode these pragmas, and we implement an LLVM pass to
take advantage of this additional information and transform the program into the decoupled-spatial ISA. All
these are available in repo **llvm-project**.


Workloads
---------

We have three benchmark suites implemented for demonstration.

**MachSuite:**
  `Machsuite <http://breagen.github.io/MachSuite/>`__ is a benchmark suite intended for accelerator-centric research.  A subset of workloads are implemented.

**DSP:**
  Digital signal processing (DSP) is a benchmark suite from our prior work `REVEL <http://https://ieeexplore.ieee.org/document/9065593>`__ for applications with moderate irregularity and imbalanced execution frequency within loop bodies.


**Xilinx Vision:**
  `Xilinx Vitis <https://github.com/Xilinx/Vitis_Libraries>`__ is a benchmark suite for HLS demonstration. We select a subset
  of workloads to target.

To develop your own applications, we also provide SDKs for both manual and high-level programming (refer [placeholder] for more details).

Functional Simulation
---------------------
Our framework extends gem5 by integrating a spatial architecture simulator to simulate the functionality and model the performance
of our decoupled-spatial architecture.

 
RTL Generation and Simulation
-----------------------------
@Sihao
