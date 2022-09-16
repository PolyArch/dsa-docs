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


Passthroughs
""""""""""""

Processing Elements can act as passthroughs, or perform the copy operation, during scheduling. This is useful to allow generality in scheduling.


Switches
++++++++




## ADG Node Types

The ADG is composed of different hardware modules, each containing their own attributes. These hardware modules are then connected to form the whole ADG. The different hardware modules are as follows:

1. Spatial Nodes
 
 * Processing Elements
 * Switches

2. Sync Nodes
 
 * Input Vector Port
 * Output Vector Port

3. Data Nodes
 
 * Direct Memory Access
 * Scratchpad
 * Register
 * Generate
 * Recurrance

In this section, we will go through each category and describe both their functionality and ADG attributes.

### Spatial Nodes

Spatial Nodes envelop the actual computation and datapath of the CGRA. Thus, these nodes make up a majority of the ADG resources. 

#### Processing Elements

Processing Elements operate as the functional units within the CGRA. Their main purpose is to perform computation. As such, their attributes are as follows:






.. toctree::
   :maxdepth: 1