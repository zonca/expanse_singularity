### Transfer the Container to Expanse

Once you have created your container on your local system, you will need
to transfer it to Expanse. There are multiple ways to do this and it can
take a varying amount of time depending on its size and your network
connection speeds.

To do this, we will use scp (secure copy). If you have a Globus account
and your containers are more than 4 Gb you will probably want to use
that file transfer method instead of scp.

Browse to the directory containing the container. Copy the container to
your scratch directory on Expanse. By issuing the following command:

    scp ./ ubuntu-anaconda.sif <username>@login.expanse.sdsc.edu:/expanse/lustre/scratch/<username>/temp_project/

The container is ~2GB so it should not take too long, hopefully.

Once on Expanse, see [How to run a container](runcontainer.html) and [How to run a GPU container](rungpucontainer.html)
