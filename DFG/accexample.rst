Accumulate Example
==================

The following is an example of a DFG file for a non-vectorized add operation:

::

   # Declare sub-dfg meta properties
   # Frequency is 0 as no work happens in this sub-dfg
   #pragma group frequency 0

   # Array Declaration
   Array array_a 131072 dma
   Array array_b 131072 dma

   ----
   # Declare sub-dfg meta properties

   #pragma group frequency 255
   #pragma group unroll 1

   # Port Declaration
   Input64 a source=array_a
   Input64 b source=array_b

   # Operation Declaration
   c = add(a, b)

   # Output Declaration
   Output64 c destination=array_c

This produces a dataflow graph that looks like the following:

.. toctree::
   :maxdepth: 2