### Write into a Singularity Container

Try writing into the container (as root, you might be prompted for your
password):

    sudo singularity shell --writable ubuntu

Create a "test" file in the `root` directory and view its contents

    Singularity> echo "my test file" > /test
    Singularity> cat /test
    my test file
