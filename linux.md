# Linux commands

This is a short list of useful Linux commands

## `scp`

Copy files between different machines

**Usage:**

    scp [file1] [file2] [file3] ... [target path]

Remote machine is prefixed to either source or target path. Syntax is `[username]@[machine name]:`

**Examples:**

    scp genheden@hebbe.c3se.chalmers.se:My_folder/ .

Copy the folder `My_folder` from machine `hebbe` to current folder (denoted with `.`)

    scp genheden@hebbe.c3se.chalmers.se:My_folder/* .

Copy all the files in `My_folder` from machine `hebbe` to current folder

    scp * genheden@hebbe.c3se.chalmers.se:My_folder/

Copy all the files in the current folder to `My_folder` on `hebbe`.

## `tar`

Creates a tar-ball of files, which is a folder packed into a single file. Convenient way to reduce number of files.

**Usage:**

    tar [-flags] [name of tar-ball] [path]

**Examples:**

    tar -czf my_tarball.tar.gz My_folder/

Create (`-c` flag) a tar-ball `my_tarball.tar.gz` of the content in the folder `My_folder` and compress with Gzip (`-z` flag)

    tar -cjf my_tarball.tar.bz2 My_folder/

Same as above but compress with it with Bzip2 (`-j` flag), which is better for text files.

    tar -xzf my_tarball.tar.gz

Unpack (`-x` flag) the contents on `my_tarball.tar.gz` in the current folder.

 
