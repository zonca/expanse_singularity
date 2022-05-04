### Installing Singularity

Use the following steps to install Singularity 3.5.3 and its
dependencies on your Linux desktop, laptop, or virtual machine.

    git clone https://github.com/mkandes/naked-singularity.git

\

    cd naked-singularity

\

If you have older versions of singularity installed, uninstall them now:

    sudo ./naked-singularity.sh uninstall

\

Install Singularity 3.5.3:

    sudo ./naked-singularity.sh install

\

Once the installation is completed, you can check to see if it succeeded
in a few different ways:

    which singularity
    singularity -version
