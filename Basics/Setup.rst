Setup
=====

Prerequisites
-------------

We highly recommend you use `Docker <https://docs.docker.com/desktop/install/linux-install/>`__ to setup
the environment. By downloading this `Dockerfile <https://github.com/PolyArch/dsa-framework/blob/micro-tutorial/Dockerfile>`__,
you can simply setup the environment by typing to build a docker image:

.. code-block:: shell

     $ sudo docker build . -t polyarch/dsa-framework:latest

Then you can start a docker container by executing command below. The docker option `-v /home/<user>/dsa-share:/root/dsa-share` allows you to share files between 
host machine and docker container.

.. code-block:: shell

        $ sudo docker run -tid [-v /home/<your username>/dsa-share:/root/dsa-share] --name=overgen polyarch/dsa-framework:latest /bin/bash


Or, more aggressively, you can build the image and start the container with one command

.. code-block:: shell

     $ sudo docker run -tid [-v /home/<your username>/dsa-share:/root/dsa-share] --name=overgen \
         `sudo docker build . | tail -1 | awk '{ print $3 }'` /bin/bash

NOTE: `zsh <https://www.zsh.org/>`__ is required. If we use the default bash,
the behaviors of our environement setup script are undesired.


Build
-----

Our docker only resolves all the dependences, and clone the repos. Therefore, after the docker
container starts, you should build the framework infrastructures from the source code:

.. code-block:: shell

     # Attach to docker container
     $ sudo docker attach overgen

     # Switch from `bash` to `zsh`, DO NOT use zsh when start docker container
     $ zsh

     # Inside the docker, enter dsa-framework root folder
     $ cd /root/dsa-framework
      
     # Initialize all submodules, SKIP this step if you are using docker
     $ ./scripts/init-submodules.sh

     # Setup dsa-framework environment variables
     $ source ./setup.sh # setup environement variables
     
     # Compile the entire dsa-framework
     $ make all -j #  If you only use a single thread, the process may take 5 hours.
     
     # Please source chipyard/env.sh manually if this is a first time build
     $ source chipyard/env.sh

NOTE: If you just want temporarily leave the container (detach, not close),
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

Prebuilt
--------

You can also download a pre-built docker image (~70GB) `here <https://drive.google.com/drive/folders/1ymP61tObuChBcKl_1_cPC37o4DzbkHSU?usp=sharing>`__, which
contains the entire dsa-framework with all toolchains built.

You can import the docker image and use dsa-framework by doing:

.. code-block:: shell

   $ docker import <downloaded tar file>.tar polyarch/dsa-framework:latest
