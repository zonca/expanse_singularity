### Building Singularity containers

For further constumization of images or for building images from scratch
we need access to a GNU/Linux machine with `root` privileges.

Then the Singularity workflow is composed of 3 steps:

* Build the image on the external Linux system
* Transfer to Expanse
* Run on Expanse via SLURM
