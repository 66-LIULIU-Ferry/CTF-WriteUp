# Plumbing
## Description
> Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to jupiter.challenges.picoctf.org 14291.

<br />

## Pipe

A pipe is a form of redirection (transfer of standard output to some other destination) that is used in Linux and other Unix-like operating systems to send the output of one command/program/process to another command/program/process for further processing. You can make it do so by using the pipe character **'|'**. 

**1. Syntax**
<br /> `command_1 | command_2 | command_3 | ... | command_N`

**2. Example**

Find a list of files that match the search term using `grep`
<br /> `ls | grep file.txt`

Sort a list of files by size using `sort`
<br /> `ls -l | sort -k 5`

Use `sort` and `uniq` command to sort a file and print unique values
<br /> `sort record.txt | uniq`

Use `head` and `tail` to print lines in a particular range in a file
<br /> `cat sample.txt | head -7 | tail -5`

Use `ls` and `find` to list and print all lines matching a particular pattern in matching files
<br /> `ls -l | find ./ -type f -name "*txt" -exec grep "program"`
<br />This command selects files with **.txt** extension in the given directory and searches for patterns like “program” in the above example and prints those which have program in them. 

<br />

## Solution
```
$ nc jupiter.challenges.picoctf.org 14291 | grep pico
picoCTF{digital_plumb3r_ea8bfec7}
```