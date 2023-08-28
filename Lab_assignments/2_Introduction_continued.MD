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

## While loops

## Scripts


## HPC LOGIN???????
