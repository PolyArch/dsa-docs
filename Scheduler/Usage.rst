Usage Overview
==============

The scheduler is run through by using the `ss_sched` command. To run the scheduler by default run:

.. code-block:: bash

    ss_sched [dfg-file] [adg-file] [options]

Optionally, the scheduler includes different flags that can help with compilation. We list these below:

* `-v` or `--verbose` 

    Makes the logging more verbose, providing in-depth information about the scheduler's progress. This defaults to `False`.

* `-x` or `--design-explore`

    Enables Design-Space Exploration (DSE) for the scheduler. See Design Space Exploration.This defaults to `False`.

* `-f` or `--fpga`

    Assumes model is using the FPGA-based hardware. Defaults to using ASIC-based hardware.

* `-p` or `--print-bitstream`

    Dumps the binary bitstream upon successful scheduling. This defaults to `False`.

* `-t` or `--timeout`

    Kills scheduling if the process takes longer, in seconds, than the timeout. This defaults to `86400` or 24 hours.

* `-m` or `--max-iters`

    Maximum scheduling iterations. Oftentimes, the scheduler will reach this before the timeout. This defaults to `20000`.

* `-e` or `--seed`

    Sets the random seed for the scheduler. This defaults to a random value.

* `--dse-timeout`

    Sets the timeout for the DSE process, in seconds. This defaults to `-1` or no timeout.

* `-w` or `--sched-workers`

    The number of workers used during scheduling. Workers schedule different dfg files in parallel. Helpful for when the Design-Space Exploration is enabled. Defaults to `1`.

* `-h` or `--help`

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
   