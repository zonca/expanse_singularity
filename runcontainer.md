### Run the Container on Expanse

Once we have a Singularity container on Expanse, let's check how to use it.

Navigate to your scratch directory on Expanse:

    cd /expanse/lustre/scratch/$USER/temp_project

Next, you should request an interactive session on one of Expanse\'s
compute, debug, or shared nodes.

    srun --pty --nodes=1 --ntasks-per-node=10 -A  -p compute -t 01:00:00  --wait 0 /bin/bash 

Once your request is approved your command prompt should reflect the new
node id.

Before you can run your container you will need to load the Singularity
module (if you are unfamiliar with modules on Expanse, you may want to
review the [Expanse User Guide](https://www.sdsc.edu/support/user_guides/expanse.html)). The
command to load Singularity on Expanse is:

    module load singularitypro

You may issue the above command from any directory on Expanse. Let\'s
try executing the following commands:

    CONTAINER='scipy-notebook_latest.sif'
    python3 --version
    Python 3.6.8
    singularity shell $CONTAINER
    Singularity> python3 --version
    Python 3.10.4

At this point we can create a simple SLURM script that launches a job executing a command via a Singularity container:

    #!/usr/bin/env bash
    #SBATCH --job-name=run-singularity
    #SBATCH --account=<ADD YOUR PROJECT HERE>
    ### Shared partition using 1/4 of a node
    #SBATCH --partition=shared
    #SBATCH --nodes=1
    #SBATCH --ntasks-per-node=32
    #SBATCH --cpus-per-task=1
    #SBATCH --mem=64G
    #SBATCH --time=00:10:00
    #SBATCH --output=log-run-singularity.o%j.%N

    declare -xr SINGULARITY_MODULE='singularitypro/3.9'

    module purge
    module load "${SINGULARITY_MODULE}"
    module list

    CONTAINER_FILE='scipy-notebook_latest.sif'

    time -p singularity exec --bind /expanse,/scratch $CONTAINER_FILE \
            python3 -c "import platform; print(platform.python_version())"

Singularity containers by default have access to the user home folder, in the call to `singularity exec`, we also specify `--bind /expanse,/scratch` so that the Project, Lustre scratch and local scratch filesystems are accessible from the container.

At this point we can create a simple SLURM script named `run-singularity.slurm` that launches a job executing a command via our Singularity container:

    #!/usr/bin/env bash
    #SBATCH --job-name=run-singularity
    #SBATCH --account=<ADD YOUR PROJECT HERE>
    ### Shared partition using 1/4 of a node
    #SBATCH --partition=shared
    #SBATCH --nodes=1
    #SBATCH --ntasks-per-node=32
    #SBATCH --cpus-per-task=1
    #SBATCH --mem=64G
    #SBATCH --time=00:10:00
    #SBATCH --output=log-run-singularity.o%j.%N

    declare -xr SINGULARITY_MODULE='singularitypro/3.9'

    module purge
    module load "${SINGULARITY_MODULE}"
    module list

    CONTAINER_FILE='scipy-notebook_latest.sif'

    time -p singularity exec --bind /expanse,/scratch $CONTAINER_FILE \
            python3 -c "import platform; print(platform.python_version())"

Singularity containers by default have access to the user home folder, in the call to `singularity exec`, we also specify `--bind /expanse,/scratch` so that the Project, Lustre scratch and local scratch filesystems are accessible from the container.

Finally we can submit it with:

    sbatch run-singularity.slurm

Notice we can also mix commands from the host and the container, for example we can do a bash for loop on the host, pass the variable as argument to a container execution and redirect the output to a file on the host:

    for datafile in *.hdf5
    do
        singularity exec $CONTAINER_FILE python3 process_data.py $datafile > ${datafile}_execution.log
    done
