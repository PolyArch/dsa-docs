Setup
=====

Prerequisites
-------------

We highly recommend you use `Docker <https://docs.docker.com/desktop/install/linux-install/>`__ to setup
the environment. By downloading this `Dockerfile <https://github.com/PolyArch/dsa-framework/blob/micro-tutorial/Dockerfile>`__,
you can simply setup the environment by typing to build a docker image:

.. code-block:: shell

     $ sudo docker build . -t polyarch/dsa-framework:latest

Then you can start a docker container by typing:

.. code-block:: shell

        $ sudo docker run -tid --name=overgen polyarch/dsa-framework:latest /usr/bin/zsh


Or, more aggressively, you can build the image and start the container with one command

.. code-block:: shell

     $ sudo docker run -tid --hostname=overgen --name=overgen \
         `sudo docker build . | tail -1 | awk '{ print $3 }'` /usr/bin/zsh

NOTE: `zsh <https://www.zsh.org/>`__ is required. If we use the default bash,
the behaviors of our environement setup script are undesired.


Build
-----

Our docker only resolves all the dependences, and clone the repos. Therefore, after the docker
container starts, you should build the framework infrastructures from the source code:

.. code-block:: shell

      # out of docker container
      $ sudo docker attach og
      # in docker container
      $ cd dsa-framework
      $ ./scripts/init-submodules.sh # initialize all submodules, skip this step if you are using Docker
      $ source ./setup.sh # setup environement variables
      $ make all -j # compile all infrastructure
      $ source chipyard/env.sh # soruce it for RISCV gnu toochains, only do this for the first time

NOTE: If you just want temporarily leave the container (not close),
you should just ``<Ctrl-p><Ctrl-q>`` to detach, instead of typing ``exit``.

Examples
--------

To verify the repo is successfully built, you can

.. code-block:: shell

   $ cd dsa-apps/demo
   $ ./run.sh ss-vecadd.out

The command above make a simple vector addition example compiled by LLVM and simulated in Gem5.

All the compiled applications are developed by the same software development kit (SDK),
refer to :ref:`SDK Section <Pragma+C Programming>` for more details.
