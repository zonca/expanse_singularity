### Run the Container on Expanse

Once the file is transferred, login to Expanse:

    ssh <username>@login.expanse.sdsc.edu

Navigate to your scratch directory on Expanse, which should be something
like:

    cd /expanse/lustre/scratch//temp_project/

Next, you should request an interactive session on one of Expanse\'s
compute, debug, or shared nodes.

    srun --pty --nodes=1 --ntasks-per-node=10 -A  -p compute -t 01:00:00  --wait 0 /bin/bash 

Once your request is approved your command prompt should reflect the new
node id.

Before you can run your container you will need to load the Singularity
module (if you are unfamiliar with modules on Expanse, you may want to
review the [Expanse User
Guide](https://www.sdsc.edu/support/user_guides/expanse.html)). The
command to load Singularity on Expanse is:

    module load singularitypro

You may issue the above command from any directory on Expanse. Let\'s
try executing the following commands:

    python3 --version
    Python 3.6.8
    singularity shell ubuntu-anaconda.sif 
    Singularity> python3 --version
    Python 3.8.5

If all goes well, you should see above outputs corresponding to the
commands. You might also see some warnings pertaining to non-existent
bind points. You can resolve this by adding some additional lines to
your definitions file before you build your container. We did not do
that for this tutorial, but you can find more information about [bind
paths and
mounts](https://sylabs.io/guides/3.0/user-guide/bind_paths_and_mounts.html).

Additional examples are located on Expanse at
`/cm/shared/apps/containers/singularity/`.
