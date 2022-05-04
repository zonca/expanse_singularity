### Integrate the Container with the Slurm Job Manager

Most users simply want to submit their jobs to the Expanse queue and let
them run to completion and go on to other things while waiting. Slurm is
the job manager for Expanse.

Below is an example job script which will start a Singularity container
on a node in the Expanse compute queue and run a Python program inside
it. You must copy the Python program, `tf2-train-cnn-cifar-10.py`, into
your current working directory from
`/cm/shared/examples/sdsc/tensorflow` if you wish to run it using the
job script. The script is a modification of an example found on Expanse,
`/cm/shared/examples/sdsc/tensorflow/run-tf2-train-cnn-cifar-10-compute.sh`

    #!/usr/bin/env bash

    #SBATCH --job-name=tf2-train-cnn-cifar-10-compute
    #SBATCH --account=use300
    #SBATCH --partition=compute
    #SBATCH --nodes=1
    #SBATCH --ntasks-per-node=128
    #SBATCH --cpus-per-task=1
    #SBATCH --mem=249325M
    #SBATCH --time=00:30:00
    #SBATCH --output=%x.o%j.%N

    declare -xr SINGULARITY_MODULE='singularitypro/3.9'

    module purge
    module load "${SINGULARITY_MODULE}"
    module list
    printenv

    time -p singularity exec --bind /expanse,/scratch --nv /cm/shared/apps/containers/singularity/tensorflow/tensorflow-2.5.1-ubuntu-18.04-cuda-11.2-mlnx-ofed-4.7-3.2.9.0-openmpi-4.0.5-20211003.sif python3 -u tf2-train-cnn-cifar-10.py 

The above script requests 1 node and 128 tasks per node with a wall time
of 30 minutes. Notice that the Singularity module is loaded.

You may need to modify the line specifying with allocation to be used
for this job (\--account=use300). When you are ready to submit the job
to the Expanse queue, issue the following command (make sure you copy
the script as well the python code into a directory that you can write
into):

    sbatch run-tf2-train-cnn-cifar-10-compute.sh

To view the status of your job in the Expanse queue, issue the
following:

    squeue -u 

When the job is complete, view the output which should be written to the
output file `tf2-train-cnn-cifar-10-compute.o%j.%N` where `%j` is the
job ID and `%N` is the node\'s hostname.
