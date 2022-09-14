Usage Overview
==============

The scheduler is run through by using the `ss_sched` command. To run the scheduler by default run:

.. code-block:: bash

    ss_sched [dfg-file] [adg-file] [options]

Optionally, the scheduler includes different flags that can help with compilation. We list these below:

* `-v` or `--verbose` 

Prints the help message.


DFG Model
---------

By just supplying the DFG file, the scheduler can print the resulting dataflow graph visualization. For instance, to get a dfg visualization for `workload.dfg` run:

.. code-block:: bash

    ss_sched workload.dfg

ADG Model
---------

By just supplying the ADG file, the scheduler can both print the graph and estimate the single-core power/area/resources, depending on whether the FPGA flag is set.

For instance, to get the single-core estimated resource breakdown of the ADG file `adg.json`:

.. code-block:: bash

    ss_sched adg.json -f

The schedule will also provide a dot file that can be used to visualize results. However, we recommed using the visualization script described here to get a better visualization.

.. toctree::
   :maxdepth: 2
   