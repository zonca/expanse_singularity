### Build Images from Scratch

Singularity supports an image format that is writable called the sandbox
format (a directory), ideal for the development process.

The following command creates a directory called ubuntu/ with an entire
Ubuntu OS in the current working directory.

    sudo singularity build --sandbox ubuntu/ library://ubuntu

To modify the contents of the directory use `--writable` option. For
example, the following creates a file named test.

    sudo singularity exec --writable ubuntu touch /test

Convert the sandboxed image to the default immutable image format
(Singularity Image File - sif):

    sudo singularity build ubuntu.sif ubuntu
