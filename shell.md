### Shell Access

Once the container is downloaded, you can `shell` into it with the
following:

    singularity shell ubuntu-anaconda.sif

\

Once you enter the container you should see a different command prompt.
At this new prompt, try typing:

    whoami

\

Your user id should be identical to your user id outside the container.
However, the operating system will probably be different. Try issuing
the following command from inside the container to see what the OS
version is:

    cat /etc/*-release

\

Check the python version within the container

    python3 --version
    Python 3.8.5

\
