# Find

<br />

## First Find
**Description**
> Unzip this archive and find the file named 'uber-secret.txt'

<br />

**Guideline**

After downloading the files, we can find the zip in `Downloads` directory
```
Downloads $ ls
files.zip
```

Then use `unzip` command to unzip the file and to find the path of specofic file, we can with the helip of `find` and `grep` commands
```
$ find files | grep uber-secret.txt
files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

As we get the path, we can open the txt file with `cat` to get the flag
```
$ cat files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
```

<br />

## Big Zip
**Description**
> Unzip this archive and find the flag.

<br />

**Guideline**

After downloading and unzipping the provided file, we can see that it is a large file without any possibility to open every file to search for the flag. 

Here I use `grep -rl`, where `-r` option is used to traverse all sub-directories and `-l` option is used to only print filenames of matching files, and not the matching lines (this could also improve the speed, given that `grep` stop reading a file at first match
```
Downloads $ cd big-zip-files
big-zip-files $ grep -rl "picoCTF" 
./folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt
```

Like before, open that file with command `cat` and we will get flag
```
$ cat folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt 
information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

What to be mentioned is that there are many other to solve those questions and commands in different operation system have different syntax (in this write up, MacOS). I have to admit I am still not familar with find commands so that I haven't sorted out a detailed notes about that. Supplement will be added someday. 