Overview
===============================

DSAGEN is a research infrastructure for studying programmable accelerators from the perspective of programming, ISAs, microarchitecture, and scaling.

The basic idea is that one can specify an accelerator as a graph, out of simple
primitives like networks, processing elements, memory, and synchronoization.
We call this an architecture description graph (ADG).  A compiler will lower
code written in either in some language (either C+Pragmas or low-level assembly
for now) to the ADG in question.  The compiler will take care of figuring out
the bitstream format based on the components of the ADG.  Finally, optimized
kernels are produced as output, composed of control code and the accelerator
bitstream.  We use a control code to sequence through the accelerator phases,
as this reduce the complexity of what is required in most accelerators.

What design space does DSAGEN target?

  Broadly, DSAGEN targets decoupled spatial designs.  By "spatial" we mean
  designs that expose the underlying network to the ISA; depending on the
  design, other low-level details like operand storage and synchronization of
  operations are also exposed to the ISA.  By "decoupled" we refer to designs
  which seprate memory pipelines from computation pipelines, so that each can have
  their own specialized primitives. [#]_


What can DSAGEN be useful for?
  
* In principle it can be used to study many different aspects of accelerator stacks.  
  
  * At the basic level, DSAGEN can be used as a baseline for other accelerators.  DSAGEN
    is fairly domain-agnostic, so it can be seen as a non-specialized spatial architecture
    baseline.  
  
  * DSAGEN can also be used in studies of novel spatial architecture features.  One can add
    a new feature, and expose it at the ISA level fairly easily (and with a little more effort
    add a compiler pass and maybe pragmas to support it).

  * The interactions between CPUs and accelerators are also extremely intersting, including
    caching, multicore, networks, etc.  DSAGEN
    has an interface with a gem5 core, can be extended to other cores).  It currently uses
    RISCV as the interface.

  * DSAGEN has a spatial architecture compiler that can be independently useful for various
    other architecture proposals, with hopefully modest implementation overhead.

  * It is our end-goal to be able to deliver reliable hardware generation, although the
    infrastructure is in the very early stages of being able to supply that. [#]_ 


.. [#] In practice, the lines between memory and computation are blurred, as some memory 
       streams embed computation, and sometimes we are computing an address.  The principle
       remains, however.
.. [#] We are a small team, and composable hardware design accross the stack takes time.  If you
       are interested in contributing, please let us know!
