### Use a prebuilt Singularity image maintained by SDSC

Marty Kandes, from SDSC User services, maintains a list of pre-built containers
which are specifically designed to run on Expanse, they are hosted
on the Github container registry at:

<https://github.com/users/mkandes/packages/container/package/naked-singularity>

See on the repository the [list of currently available image types](https://github.com/mkandes/naked-singularity/tree/master/definition-files), among which `anaconda`, `tensorflow`, `gromacs`, `spark` and many more.

For example see the [Ubuntu-based PyTorch containers](https://github.com/mkandes/naked-singularity/tree/master/definition-files/pytorch).
These containers are already in a format suitable for Singularity, therefore Singularity is only downloading them, so we can run the `pull` command from the login node:

    $ singularity pull oras://ghcr.io/mkandes/naked-singularity:pytorch-1.10.2-ubuntu-20.04-cuda-11.2-mlnx-ofed-4.9-4.1.7.0-openmpi-4.1.3

The container is large, so downloading will take some time:

    $ du -h naked-singularity_pytorch-1.10.2-ubuntu-20.04-cuda-11.2-mlnx-ofed-4.9-4.1.7.0-openmpi-4.1.3.sif
    9.3G    naked-singularity_pytorch-1.10.2-ubuntu-20.04-cuda-11.2-mlnx-ofed-4.9-4.1.7.0-openmpi-4.1.3.sif
