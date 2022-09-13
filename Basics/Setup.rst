Setup
========================================================

Prerequisites
-------------

Packages
~~~~~~~~

::

    $ sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev        \
                           libgmp-dev gawk build-essential bison flex texinfo gperf libtool   \
                           patchutils bc qt4-dev-tools libqt4-dev python-dev scons flex bison \
                           libgoogle-perftools-dev python-six libssl-dev zlib1g-dev

Misc
~~~~

CMake 3.12 is required. You can go to `CMake official
page <https://cmake.org/download/>`__ to get the latest one.

Python hex package is required for riscv-opcode. It seems to be a
default package from
`Anaconda <https://www.anaconda.com/products/individual>`__.

Build the Stack
---------------

Build the decoupled-spatial architecture stack from the source.

::

    $ git clone --recursive [this repo]
    $ source setup.sh
    $ source $HOME/anaconda/bin/activate
    $ make

Run an Example
--------------

Run a manually programmed example:

::

    cd ss-workloads/dsp-benchmarks/gemm
    make sb-new.log

Run a compiled example:

::

    cd ss-workloads/Compilation/MachSuite/
    ./run.sh opt-ss-gemm.out


