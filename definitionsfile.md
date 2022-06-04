### Build from a Definitions File

Singularity allows you to use a 'definition file' so you can
reproduce the resulting container configurations on demand. Let's say
you want to create a container with Ubuntu with Anaconda. First, we need
our definition file. Here's an example Anaconda definition file:

[Singularity.anaconda3-py39-2021.11-ubuntu-20.04](https://github.com/mkandes/naked-singularity/blob/master/definition-files/anaconda/Singularity.anaconda3-py39-2021.11-ubuntu-20.04)

The following command creates an ubuntu-anaconda.sif image from the
definition file `Singularity.anaconda3-py39-2021.11-ubuntu-20.04`:

    cd naked-singularity
    sudo singularity build ubuntu-anaconda.sif definition-files/anaconda/Singularity.anaconda3-py39-2021.11-ubuntu-20.04

This may take a while to complete.
