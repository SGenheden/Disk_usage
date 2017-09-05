# Tips and tricks

Here follows some useful tips and tricks

## Copy files between a PDC and C3SE

Both the PDC and C3SE computer clusters are hidden from the outside; PDC machines require a Kerberos ticket and C3SE machine require you to be within the Chalmers network.

To copy files between a PDC and a C3SE machine with `scp` is therefore not entirely straightforward. You could copy all the files to a third computer, like your local machine, but that is cumbersome and unnecessary.

Instead, you can set up an **ssh tunnel**, a way to "remove" the extra layer of protection that C3SE has setup.

1. Log into Beskow

2. Type the following to open the ssh config-file in `vi`

        vi ~/.ssh/config

3. Type `i` to enter insert-mode and add the following lines

        Host c3setunnel
        HostName remote11.chalmers.se
        LocalForward 8024 hebbe.c3se.chalmers.se:22
        User genheden

        Host hebbe
        HostName localhost
        Port 8024
        User genheden

    Be sure to change `genheden` to your own username

4. Type `esc` to exit insert-mode and then `wq` to save and exit `vi`

Now we have edit a new alias `c3setunnel` that we can logon to and thereby open up the tunnel to `hebbe`.

5. Type

    `ssh c3setunnel`

    and enter your password.

    You are now on the `remote11.chalmers.se` machine, and the **ssh tunnel** is open.

6. Open a **new** terminal with the `beskow` logon node  

    You can now use `scp` as usually

7. For instance, type

        scp * hebbe:/priv/c3-teobio/genheden/My_folder/

    to copy all the files from the current folder to `My_folder` in the common disk on `hebbe`.
