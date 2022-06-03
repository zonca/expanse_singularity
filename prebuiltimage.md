### Import a Prebuilt Image

Importing a Docker or a Singularity prebuilt container requires resources that are limited on the login node, so first we need to get a terminal on a debug computing node. Find out the available projects:

    module load sdsc
    expanse-client user -r expanse

copy-paste the more suitable "Project" into an environment variable:

    export PROJECT=xxx123

Now we can request 30 minutes in the debug partition:

    srun --partition=debug --pty --account=$PROJECT --nodes=1 --ntasks-per-node=4 \
    --mem=8G -t 00:30:00 --wait=0 --export=ALL /bin/bash

For example we can import one of the Docker container by the Jupyter Project that can be used to run JupyterLab on Expanse via the [Galyleo script](https://github.com/mkandes/galyleo):

    singularity pull docker://jupyter/r-notebook:latest

This will create the Singularity container file:

    $ du -sh r-notebook_latest.sif
    878M    r-notebook_latest.sif

We can get a terminal inside the container and verify it is an Ubuntu release:

    $ singularity shell r-notebook_latest.sif
    Singularity> cat /etc/lsb-release
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=20.04
    DISTRIB_CODENAME=focal
    DISTRIB_DESCRIPTION="Ubuntu 20.04.4 LTS"

Finally execute a command through the container with `singularity exec`:

    $ python --version
    Python 3.6.8
    $ singularity exec r-notebook_latest.sif python --version
    Python 3.10.4
