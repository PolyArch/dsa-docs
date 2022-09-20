SDK Walkthrough
===============

This section explains our software development kit, which allows
users to rapidly start writing your own applications. Please refer to
`this repo <https://github.com/PolyArch/dsa-apps/tree/polyarch/sdk>`__.

Automated Compilation
---------------------

In the example `vecadd <https://github.com/PolyArch/dsa-apps/blob/polyarch/sdk/compiled/vecadd.c>`__,
by simply typing the command below, the generated binaries can be simulated in Gem5. 

.. code-block:: shell
   $ cd sdk/compiled
   $ ./run.sh ss-vecadd.out

The explanation is separated into two aspects, the programming interfaces, and the build infrastructures.
To explain the programming interfaces, we provide a set unified interfaces (in this case, declared in
`common/interface.h` and implemented in `vecadd.c`) for you to write application kernels and model its performance.

- `struct Arguments` are the input of the benchmark kernel, which will be initialized by `init_data` and
  used as input argument of `run_*`.
- `init_data` initializes the input of application. We provide several convinence function macros in `common/test.h`
  to initialize the data.
- `run_reference` is the function invoke the host execution for a golden reference of the application result.
- `run_accelerator` is the function to invoke the accelerator. The `is_warmup` indicates if it is cache warmup invocation.
- `sanity_check` verifies the result of compilation. We provide several convinence function macros in `common/test.h`
  to check the result correctness.

Feel free to copy and rename `vecadd.c` and write other kernels and use the following command to simulate.

.. code-block:: shell
    $ ./run.sh ss-%.ou

`%` is the name of the the kernel c file without suffix.
All the files share the same main function implemented in `common/gem5-harness.c` --- the main function invokes
each function sequentially, and invokes `run_accelerator` twice to warm up the cache and time it.

To explain the build infrastructures, we overview the flow of compilation:

1. The kernel file is first parsed by our extended `clang` and generate an LLVM IR file (see `vecadd.ll`).
2. This IR file is fed to an LLVM pass for decoupled-spatial transformation.
    1. The decoupled memory access are encoded in control commands and embedded in the host assemly code (see `ss-vecadd.ll`).
    2. The decoupled computation are in dfg file(s) (see `vecadd_%.dfg` where % is the unrolling degree).
3. The transformed IR is fed to LLVM code generator to generate assembly code (see `ss-vecadd.s`).
4. The generated assembly code will be fed to riscv-gnu linker to generate the binaries (see `ss-vecadd.out`).


Because Chipyard Rocket core adopts a different model of RISCV CPU as Gem5 implements,
it requires different compilation flags and link options. For the RTL simulation purpose,
by simply type

.. code-block:: shell
   $ make ss-vecadd.riscv

The Chipyard compatible main function will be linked.

Manually Program
----------------


.. toctree::
   :maxdepth: 2
