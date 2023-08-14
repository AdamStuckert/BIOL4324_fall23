## Lab 2: Introduction to programming continued 

Today we will be continuing to learn about introduction to programming for biologists. We will focus on some basic, but very useful information such as paths, the path, variables,  and conditionals. The examples I'm giving you are for a bash Linux system, but the ideas behind these are generally true for programming languages at large (although the syntax will be different).

### Paths

Any file/location can be specified in two ways:

1. Relative to your current working directory (folder). This is known as the *relative path* because it is *relative* to where you are. So for example if I'm in the biol4324 folder, I can point to the exam 1 key with exam1_key.txt. If I am in the stuckert/ directory, I can point to the same file with biol4324/exam1_key.txt. Alternatively, I can use the absolute path, which specifies the full path to a file. In this case, I can use /home/stuckert/biol4324/exam1_key.txt to point to this exam key no matter what directory I am currently in.
2. You can specify the *full path* of the file/directory. This is known as the *absolute path*. Using absolute paths is long and arduous, but is generally a better practice than repeated use of relative paths. These can be tricky, especially if you are using several directories/files are a few subdirectories away. You can also "cheat" and use variables to help specify absolute paths (see below).

### Variables 

Variables are an incredibly useful programming tool. I personally use them a lot, possibly excessively. They are particularly useful for calling paths, scripts, or specifying output, etc. They are frequently used in scripts, and are frequently defined based on input when you call a script. Variables can be used to specify paths, integers, executables, etc. As mentioned above, you can use variables as shorthands for paths, which is quite convenient. You can set variables like this:

```bash
genome=/full/path/to/genome.fasta
txome=/full/path/to/txome.fasta
hifi=/path/to/hifi/executable/hifi
output_dir=/path/to/output/directory
```

In each of these cases, the variable is the single string before the `=` sign. To call those variables in your script or terminal, you would use this `$genome`.

You can also specify a variable using the output of a command. To do this, you use the command inside of `$()`. For example, to set the current directory as the variable `$DIR` you would use this command:

```bash
DIR=$(pwd)
```

This is convenient, because you can use it to call the absolute path with ease, eg: `${DIR}/raw_data/alskdjfaojf.1.fa`

