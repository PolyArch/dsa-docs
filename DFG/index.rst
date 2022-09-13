Dataflow Graph
==============

The Dataflow Graph (DFG) is a representation of the dataflow of a program. It is a directed graph where the nodes are the operations and the edges are the data dependencies between the operations. The DFG is a static representation of the dataflow of a program. It is not a representation of the actual dataflow at runtime.

The Compiler automatically creates DFG files. The DFG files are used by the simulator and scheduler to map onto the actual hardware. DFG files can also be manually created, this section acts as a reference on reading and creating custom DFG files.

.. toctree::
   :maxdepth: 4

   fileformat
   examples