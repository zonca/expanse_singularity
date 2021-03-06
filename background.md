### Background

### Why Singularity?

Below is a typical list of commands you would need to issue in order to
implement a functional Python installation for scientific research:

    COMMAND=apt-get -y install libx11-dev
    COMMAND=apt-get install build-essential python-libdev
    COMMAND=apt-get install build-essential openmpi-dev
    COMMAND=apt-get install cmake
    COMMAND=apt-get install g++
    COMMAND=apt-get install git-lfs
    COMMAND=apt-get install libXss.so.1
    COMMAND=apt-get install libgdal1-dev libproj-dev
    COMMAND=apt-get install libjsoncpp-dev libjsoncpp0
    COMMAND=apt-get install libmpich-dev --user
    COMMAND=apt-get install libpthread-stubs0 libpthread-stubs0-dev libx11-dev libx11-d
    COMMAND=apt-get install libudev0:i386
    COMMAND=apt-get install numpy
    COMMAND=apt-get install python-matplotlib
    COMMAND=apt-get install python3

Singularity allows you to avoid this time-consuming series of steps by
packaging these commands in a re-usable and editable script, allowing
you to quickly, easily, and repeatedly implement a custom container
designed specifically for your analytical needs.

![KNL Quadrant Cluster Mode](images/vm_container_comparisons.png){width="600px"}

Comparison of a VM vs. Docker vs. Singularity.\
Source: [Greg Kurtzer keynote at HPC Advisory Council 2017 @
Stanford](http://www.hpcadvisorycouncil.com/events/2017/stanford-workshop/pdf/GMKurtzer_Singularity_Keynote_Tuesday_02072017.pdf#43)

Additional features of Singularity include:

-   Singularity provides flexibility for a particular OS Environment.
-   Singularity has become very popular on XSEDE systems like Expanse.
-   Singularity allows groups to easily migrate complex software stacks from their campus to XSEDE systems.
-   Singularity runs in user space, and requires very little special support - in fact it actually reduces it in some cases.
-   Singularity offers a convenient way to run applications such as Tensorflow, ParaView, Torch, Fenics, and custom user applications.
-   Docker images can be imported into Singularity.
