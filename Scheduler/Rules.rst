Spatial Mapping Rules
=====================

The following list contains the rules that are used to determine whether a given schedule is valid or not.

#. Vertex slots must be mapped to even slots.

Example:

::
   
   - Invalid:    | ___ | OPA | OPA | ___ |
   - Valid:      | OPA | OPA | ___ | ___ |
   - Valid:      | ___ | ___ | OPA | OPA |

#. Two DFG ports can not be mapped to a single VectorPort.
#. The stated dfg edge is always 8 bits wide.
#. A stated DFG port can not be mapped to a non-stated vectorport.
#. The stated dfg edge is always mapped to a stated VectorPort on bits [0-8]. The first link of a vector port only includes the stated edge.
#. The other links of the vectorport are statically assigned according to their value id. A InputPort value can not stradle two different links.
#. Memory DFG Edges, or those with either their source or destination vertex being a data node, can't utilize switches.

Exampe:

::

   - Invalid: SPM0 -> SWITCH0 -> IVP0

#. A dfg edge entering a non-switch must come in at an even slot

Example:

::

   - Invalid:    | ___ | OPA | OPA | ___ |
   - Valid:      | OPA | OPA | ___ | ___ |
   - Valid:      | ___ | ___ | OPA | OPA |

#. A switch can map to any contiguous slot.

Example:

::
   - Valid:      | ___ | OPA | OPA | ___ |
   - Valid:      | OPA | OPA | ___ | ___ |
   - Valid:      | OPA | ___ | ___ | OPA |
   - Invalid:    | OPA | ___ | OPA | ___ |

#. A lower bitwidth edge must always be mapped to the lower bits of a granularity.

Example:

::

   A 16 bit edge mapped to a Node with granularity 32 and datawidth 64 bit granularity
   - Valid: Mapping edge to bits: [0:16] or [32:48]
   - Invalid: Mapping edge to bits: [16:32] or [48:64]



.. toctree::
   :maxdepth: 2
