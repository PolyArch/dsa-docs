ADG Visualization
=================

We have developed two different methods (one using graphviz and another using html) to visualize the adg, each having their own tradeoffs. Both these methods are useful in gaining an underlying insight into ADG structure.

Using Dot Files
---------------

To get an ADG Graphviz file, you must first run the scheduler using the following command:

.. code-block:: bash

   ss_sched adg.json -f

A graphviz file should appear in the newly created viz directory. To view the dot file, you must first install the graphviz package. Then, you can run the following command:

.. code-block:: bash

   dot -Tpng viz/adg.gv -o viz/adg.png

Alternatively, we have found more structured results using:

.. code-block:: bash

   neato -Goverlap=false -Gstart=self -Gepsilon=.0000001 -Tpng -o viz/adg.png viz/adg.gv

Visualizing Using HTML
----------------------

To get a HTML visualization of the ADG, you must run the python script `adg_visualize.py` on the file specified file. Thus, it looks like this:

.. code-block:: bash

   python3 adg_visualize.py adg.json

Then, you can open the generated html file in your browser to view the ADG. This script is interactive, allowing a rearrangement of modules. We have also found the physics-based simulation to be more instructive, producing a grid-like format for mesh designs, which hasn't necessarily been true of graphviz-based designs.



.. toctree::
   :maxdepth: 1