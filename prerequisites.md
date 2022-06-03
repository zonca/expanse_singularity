### Prerequisites

The purpose of this tutorial is to enable you to use XSEDE\'s Expanse
supercomputer at [SDSC](http://www.sdsc.edu) to run your jobs using Singularity. You will
need the following:

-   Basic familiarity with using Expanse
    -   [Expanse User Guide](https://www.sdsc.edu/support/user_guides/expanse.html)
    -   [Getting Started with Expanse](https://education.sdsc.edu/training/interactive/202009_expanse_101/index.php) tutorial
-   An account on Expanse; there are several options if you do not already have an account on Expanse. All of these will require that you first create a free account on the [XSEDE User Portal](https://portal.xsede.org/)
    -   Currently, Expanse is unique in its status as an XSEDE system on which users may request a [trial allocation](https://portal.xsede.org/allocations/announcements#trial) to evaluate resources
    -   If you are at a site with a [Campus Champion](https://www.xsede.org/web/site/community-engagement/campus-champions/current), you can request a small amount of compute time
    -   If your research is limited by the limited compute power you have in your research lab, you can request a [Startup Allocation](https://portal.xsede.org/allocations-overview#types-trial)

Tutorials on how to get started with Singularity generally do not
include details specific to running Singularity on XSEDE systems such as
Expanse. In this tutorial, we will review how to access a compute node
on Expanse and provide a simple example of how to run a Tensorflow job
with Singularity on Expanse to help get you started.
