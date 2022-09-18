Setup
========================================================

Prerequisites
-------------

We highly recommend you use `Docker <https://docs.docker.com/desktop/install/linux-install/>`__ to setup
the environment. By downloading this `Dockerfile <./Dockerfile>`, you can simply setup the environment
by typing

.. code-block:: shell

     $ sudo docker build .


Or, more aggressively, you can build the image and start the container with one command

.. code-block:: shell

     $ sudo docker run -tid --privileged=true --hostname=og --name=og \
         `sudo docker build . | tail -1 | awk '{ print $3 }'` /usr/bin/zsh

`zsh <https://www.zsh.org/>`__ is required because the behaviors of our environement setup script
will change if we use the default bash.


Build
-----

Our docker only resolves all the dependences, and clone the repos. Therefore, after the docker
container starts, you should build the framework infrastructures from the source code:

.. code-block:: shell

      $ cd dsa-framework
      $ source setup.sh # setup environement variables
      $ make all
      $ source setup.sh # soruce it again after building

