## Lab 2: Introduction to programming continued 

Today we will be continuing to learn about introduction to programming for biologists. We will focus on conditionals and scripts to start. Again, the examples I'm giving you are for a bash Linux system, but the ideas behind these are generally true for programming languages at large (although the syntax will be different).


## Conditionals

Conditionals are a programming staple. There are three main types that we will cover in class:

1. For loops
2. While loops
3. If then statements

Each of these have their own unique uses in programming, and programming languages all have their own
For loops are meant to run through every item in a list and do a series of tasks. While loops are similar to for loops, but they run only *while a condition is true*. If then statements are basically a decision flow chart, but in code. We will be talking about each of these in class, and here we will go through examples of them.

## If then statements.

If then statements are extremely useful for parsing data and enacting different actions, regardless of the programming language. You can use them to do a task if a value is less than 5, enable an action if a file does not exist, etc. The most basic way to use these is to enact a particular command only in one condition. For example, you can test if a file exists:

```bash
touch testfile.txt # the touch command creates an empty file
if [ -f testfile.txt ]
  then
    echo "testfile.txt exists."
fi
```

**Question 1:** paste in a screenshot of this from your terminal.

A more complicated version of this is to do a command if a condition is met, and a followup command if that condition is not met.

```bash
rm testfile.txt
if [ -f testfile.txt ]
  then
    echo "testfile.txt exists."
else
    echo "testfile.txt does not exist."
fi
```

There is also a third variation of the if/then statement: the elif statement. These are where you can really add in a lot of conditionals. As many as you want! Or at least as many as you can keep track of. The basic structure is this:

```bash
if test
  then
    perform actions
elif test
  then
    perform elif action(s)
else
    perform else action(s)
fi
```

Design code to run through three conditions:
1. If a number is greater than 10 ( `-gt 10` ) print that the number is greater than 10
2. If a number is less than 10 ( `-lt 10` ) print that the number is less than 10
3. If a number is equal to 10 ( `-eq 10` ) print that the number is equal to 10
Use a variable `$num` that you specify, per last week.

**Question 2**: What is your code? Make sure to test it under each condition!

## For loops

For loops execute a series of commands repeatedly. They run through iterations of a variable/file and run the same code over and over, generally until it has gone through all possible iterations. At its simplest, a for loop looks like this:

```bash
for i in 2 4 6 8 10
do
echo "$i coog"
done
```

**Question 3**: What is the output of this command?

**Question 4**: What is `i` in this command? What does `i` represent the 4th time this loop is run?

A fun trick, you can set something to run through a range of numbers using the format `{START..END..INCREMENT}`. So you could run numbers 1 to 10 by 2.

**Question 5**: Write a for loop to print every 5th number from 5 to 100 (eg, it would go 5,10,15 and so on until 100). Paste in your code.

Last weel we ran commands within a single line of code to set the output as a variable. We can do the same thing within a for loop. I will often use this to run a series of commands on all the raw data I have for a particular project. For example, if I want to run through all the fasta files in a I can use the `ls` functino to identify all the fasta files in a directory and set them as my variable. Assuming that I have all my data in a directory called `raw_data` and they all end in `.fasta` I can use the `ls` command and a wildcard character `*` to find all the fasta files like this: `ls raw_data/*.fasta`. This finds all the files that are in the `raw_data` directory whose file names end in `.fasta`.

**Question 6**: Write a for loops that uses `ls` to print all the fasta file names in the directory `/project/stuckert/bioinformatics/lab2/fasta_files` to screen. Paste in the code. 

**Question 7**: Paste in the output.

## While loops

While loops are meant to run repeatedly *while a condition is true*. The simplest form of this is to run while  a number is less than X. This can be useful if you want to run a set number of iterations of code. While loops follow the same format as for loops, but switch out `while` for `for`. Syntax thus looks like this:

```bash
while CONDITION
do
DO THE THING
done
```

If, for example, you wanted to run from 1 to 10, you could make a "counter" variable, and run a while loop as long as that `$counter` is less than or equal to 10. 
```bash
counter=1
while [ $counter -le 10 ]
do
echo $counter
((counter++))
done
```

## Nesting loops

Loops can be nested within each other like a set of Russian dolls. You can have a series of for loops within each other, you can intermingle for loops and if/else statements. etc. 

I used the following command to generate all the shasta fasta files:

```bash
for file in i ii iii iv v vi vii
do
touch shasta_${file}.fasta
done
```

BUT, we are missing Louie! We need to add the itty bitty kitty to the itty bitty kitty committee. 

**Question 9??**: Use my for loop above and a nested conditional to make files that start with "shasta" for each shasta, but do not start with "shasta" for Louie. Hint: start a command with `for file in i ii iii iv v vi vii louie` and go from there. Paste in your code.


## Scripts


## HPC LOGIN???????
