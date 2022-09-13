Acc Vectorization Example
=========================


The following is an example of a DFG file for a vectorized-by-four add operation:

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
   #pragma group unroll 4

   # Port Declaration
   Input64 a[4] source=array_a
   Input64 b[4] source=array_b

   # Operation Declaration
   c_0 = add(a_0, b_0)
   c_1 = add(a_1, b_1)
   c_2 = add(a_2, b_2)
   c_3 = add(a_3, b_3)

   # Output Declaration
   Output64 c destination=array_c

This produces a dataflow graph that looks like the following:

.. toctree::
   :maxdepth: 2