Setup
========================================================

Prerequisites
-------------

We highly recommend you use `Docker <https://docs.docker.com/desktop/install/linux-install/>`__ to setup
the environment. By downloading this `Dockerfile <https://github.com/PolyArch/dsa-framework/blob/micro-tutorial/Dockerfile>`__,
you can simply setup the environment by typing

.. code-block:: shell

     $ sudo docker build .


Or, more aggressively, you can build the image and start the container with one command

.. code-block:: shell

     $ sudo docker run -tid --privileged=true --hostname=og --name=og \
         `sudo docker build . | tail -1 | awk '{ print $3 }'` /usr/bin/zsh

NOTE: `zsh <https://www.zsh.org/>`__ is required. If we use the default bash,
the behaviors of our environement setup script are undesired.


Build
-----

Our docker only resolves all the dependences, and clone the repos. Therefore, after the docker
container starts, you should build the framework infrastructures from the source code:

.. code-block:: shell

      $ cd dsa-framework
      $ source setup.sh # setup environement variables
      $ make all
      $ source chipyard/env.sh # soruce it for RISCV gnu toochains

