## Lab 3

Today we will learn the basics of scripts, as well as how to properly use an HPC. 

## Scripts

Scripts are the foundation of bioinformatics. They provide automation, flexibility, and speed in analyses--particularly tasks that are repeated over days, months, or years. Scripts can run a single command, or a hundred million (don't do this, that makes debugging impossible and you will hate your past self). Although in some cases it may be possible to run commands one by one, and in fact this can be really helpful for assembling pipelines/troubleshooting, it is not fun or feasible in most cases. 

Scripts add a lot of flexibility and speed. In Linux environments we use shell scripts, which typically end in `.sh` (but do not have to.

All scripts must start with a `shebang` which is a `#!`. This is a weird term. Here is what Wikipedia says about it:

> The name shebang for the distinctive two characters may have come from an inexact contraction of SHArp bang or haSH bang, referring to the two typical Unix names for them. Another theory on the sh in shebang is that it is from the default shell sh, usually invoked with shebang.

Anyway, the shebang statement must occur starting at the first character of the first line in the script. This statement tells the computer which interpreter to use. You'll notice that it looks like a following the shebang is the location of the interpreter. You may end up using different interpreters for python, r, c, bash, etc. We will use bash in class, though you are welcome to use other languages for your final project if you feel comfortable doing so.

Assuming that your interpreter is in your `/bin/` (which is a good assumption, generally), your shebang statement would look like this:

```bash
#!/bin/bash
```

By Linux law, we are contractually obligated to create a Hellow World script as our first script. Open up your nano text editor and write the following in the file (hint, you may need to go back to lab 1 for help with this):

```bash
#!/bin/bash

echo Hello World!
```

Save this as `hello_world.sh`.

**Question 1:** What command did you use to open the text editor and how did you save it?

You've now saved your first script! 

Let's take a look at this script with the `ls -l` command (the `-l` flag is for "long"). It should look something like this:

```
drwxr-xr-x 8 adamstuckert adamstuckert 4096 Dec 20  2022 sshfs-win
```

The first group of characters and hyphens are the permissions. The first character is either a `d` for directory or `-` for file. The next 9 characters are in  groups of 3 (like codons!), and represent wether the owner, group, and everyone have read (r), write (w), and executable (x) privileges in that order. If those are represented by a `-` then that person/group does not have permission for that task. The first number represents the number of links or files in a directory. 

After this there are two string characters. These represent the owner of the file/directory, and finally what group they are in. 

The two right most fields are the name (rightmost field) and the date this was last modified (second field from the right).

**Question 2:** What group are you in?





