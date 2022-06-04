### Installing Singularity

Use the following steps to install a recent version of  Singularity and its
dependencies on your Linux desktop, laptop, or virtual machine.

    git clone https://github.com/mkandes/naked-singularity.git
    cd naked-singularity

If you have older versions of singularity installed, uninstall them now:

    sudo ./naked-singularity.sh uninstall

Install Singularity and its requirements:

    sudo ./naked-singularity.sh install

Once the installation is completed:

    which singularity
    singularity --version
