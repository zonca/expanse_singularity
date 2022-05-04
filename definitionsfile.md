### Build from a Definitions File

Singularity allows you to use a \'definitions file\' so you can
reproduce the resulting container configurations on demand. Let\'s say
you want to create a container with Ubuntu with Anaconda. First, we need
our definitions file. Here\'s an example Anaconda definition file:
[ububtu-anaconda.def](https://github.com/mkandes/naked-singularity/blob/master/definition-files/anaconda/Singularity.anaconda3-py38-2020.11-ubuntu-18.04)

The following command creates an ubuntu-anaconda.sif image from the
definitions file `Singularity.anaconda3-py38-2020.11-ubuntu-18.04`:

    sudo singularity build ubuntu-anaconda.sif definition-files/anaconda/Singularity.anaconda3-py38-2020.11-ubuntu-18.04

\

This may take a while to complete.
