Usage
=====

The design space explorer is run through by using the `ss_sched` command, with the `-x` flag. To run the scheduler by default run:

.. code-block:: bash
    ss_sched dfgs.list adg.json -x -f

.. IMPORTANT:: Currently the Design-Space Explorer only explorers fpga-based accelerators and doesn't support ASIC-based optimization. Thus it must be run with the `-f` flag.


The design-space explorer shares the same flags as the default scheduler.:

* `-e` or `--seed`

   Sets the random seed for the scheduler. This defaults to a random value.

* `--dse-timeout`

   Sets the timeout for the DSE process, in seconds. This defaults to `-1` or no timeout.

* `-w` or `--sched-workers`

   The number of workers used during scheduling. Workers schedule different dfg files in parallel. Defaults to `1`.

File Outputs
------------

The design-space explorer outputs a number of files to the `vis` directory. The files are:

* `objectives.csv`
   
   A logfile of different dse-iterations. Useful for debugging and visualizing the design-space explorers progress.

* `final-schedadg.json`
   
   The produced adg file from the dse. Contains extra fields describing the system parameters and information about how the finalized schedules were mapped onto the accelerator.

* `prunned-schedadg.json`
   
   The prunned version of final-schedadg. Contains extra fields describing the system parameters and information about how the finalized schedules were mapped onto the accelerator.

* `iters` directory
   
   A directory containing improved schedules. Each time the DSE improves the ADG, it will store that iterations ADG within this folder. This folder is useful for understanding what the DSE did at each iteration.

.. toctree::
   :maxdepth: 2