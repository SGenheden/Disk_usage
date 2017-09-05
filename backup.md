# Backup

These are some guidelines how to do backup, and tips on what to do backup on and how the storage space can be optimized.

## Rule 1: backup often

Otherwise, you **will** loose data.

## Rule 2: backup often

Otherwise, you **have to** re-do unnecessary work.    

## Use `rsync` to backup your files.

The preferred way to do backup, i.e. copy important files to the backup directory is with the command `rsync`

**Example:**

    rsync -av --exclude="*.xtc" --exclude="*_prev.cpt" --exclude="q-*" Ala ../backup/genheden/

This backups up the folder `Ala` to my backup folder (`../backup/genheden`). The `-a` flag turns on archive mode, which is a fast way to tell `rsync` to recurse your folders and maintain meta-data when copying the files. The `-v` flag turns verbose mode, i.e. `rsync` is explicit what is copying. The `--exclude` files add filters to the procedure so that only "important" files are backup. Here, I don't want to copy xtc-files, files ending with _prev.cpt (Gromacs restart files) and queue files.

**Save your command to do backup in a file!** In this way you can repeat it over and over again.

## What to backup?

### Rule 1: you need to be able to re-run your calculation

Save **all** input files so that you repeat the calculation if necessary.

### Rule 2: if the output file took less than a week to generate automatically, don't bother

The calculation (MD, docking etc.) was so quick that, given the same input and code, you can re-generate the data.

That is why I excluded the xtc-files in the example above. The MD simulation took less than 1 week to run, and I have the input file (tpr-file) to regenerate it.  
