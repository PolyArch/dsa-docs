ADG File Format
=================

ADG Files contain two parts:

* ADG Module Declaration

* ADG Link Declaration

ADG Module Declaration
----------------------

The ADG is composed of different hardware modules, or nodes, with each containing their own attributes. Broadly, the ADG demarcates three different node types (`spatial`, `sync`, and `data` nodes) based on their typical placement and function within the adg. 

Spatial Nodes
~~~~~~~~~~~~~

Spatial Nodes perform the computation and routing network inside the ADG. Consisting of processing elements and switches, these nodes are interlinked, performing computation and recieving inputs/outputs from the sync nodes. 

Processing Elements
^^^^^^^^^^^^^^^^^^^

Processing Elements are the basic computational unit of the ADG. They are the nodes that perform the actual computation. Each processing element has a set of defined operations, taking inputs and then performing the operation upon it.

**Passthroughs**

Processing Elements can act as passthroughs, or perform the copy operation, during scheduling. This is useful to allow generality in scheduling.


Switches
^^^^^^^^

Switches perform routing within the ADG, allowing greater generality in designs. In hardware, switches act as a series of muxes allowing data to move from any input to any output.

**Broadcast**

Switches are also helpful as they have the capability to broadcast, or one input go to two different outputs. This functionality is required for several schedules where broadcasting is needed. Processing elements are not able to broadcast data.


Spatial Node Properties
^^^^^^^^^^^^^^^^^^^^^^^

**Fifo Depths**

Each spatial node has a fifo, allowing it to balance delays and hopefully remove pipeline stalls. These fifos can be set by the `fifo_depth` property. Currently, the fifo can't be eliminated without potentially hurting the frequency, thus the fifo depth must be set to at least 1.

Sync Nodes
~~~~~~~~~~

Sync Nodes bring data into the spatial architecture from the data. It consists of input vector ports and output vector ports.

Input Vector Ports
^^^^^^^^^^^^^^^^^^

Input vector ports act as the input. They generate the data requests and stream data into the spatial part of the ADG.

Output Vector Ports
^^^^^^^^^^^^^^^^^^^

Output vector ports act as the output. These hardware modules take data produced from the spatial architecture and then feed them into different data nodes.

Sync Node Properties
^^^^^^^^^^^^^^^^^^^^

**Stated**

Both Input and Output Vector ports can be stated, meaning the first link is reserved for the stated control inputs from the DFG.


Data Nodes
~~~~~~~~~~

Data nodes interact with memory, and deal with streaming requests and different levels of the memory heirarchy. Currently, there are 5 different data node types, `DMA`, `Scratchpad`, `Recurrance`, `Generate`, and `Register`. Each node performs different types of data movement, and has its own associated functionality.

DMA
^^^

DMA nodes stream data from the DRAM and L2 cache.

Scratchpad
^^^^^^^^^^

Scratchpad nodes act as a private cache for each accelerator tile. The scratchpad has an associated size and is replicated within each tile.

Recurrance
^^^^^^^^^^

Recurrance Nodes directly stream data from the output back into the input vector port. 

Generate
^^^^^^^^

Register
^^^^^^^^

Data Node Properties
^^^^^^^^^^^^^^^^^^^^

Data Nodes all interconnect on a bus. Thus, the bandwidth mechanism works similarly for all data nodes, depending on their replication across cores.




.. toctree::
   :maxdepth: 1