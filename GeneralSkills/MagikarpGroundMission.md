# Magikarp Ground Mission
## Description
>Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `b60940ca`

<br />

Before showing the specific steps to figure out the flag, there are several knowledge points need to be understood during the process

## Shell
**1. What is Shell?**

Before understanding Shell, we have to get familiar with all the following terminologies: **Kernel, Shell, Terminal**

- **Kernel** is a computer program that is the core of a computer’s operating system, with complete control over everything in the system.
- **Shell** is a special user program that provides an interface for the user to use operating system services. Shell accepts human-readable commands from users and converts them into something which the kernel can understand. It is a command language interpreter that executes commands read from input devices such as keyboards or from files. The shell gets started when the user logs in or starts the terminal.
- **Terminal** is a program which is responsible for providing an interface to a user so that he/she can access the shell.

> So if we are using any major operating system, we are **indirectly** interacting with the shell

Shell is broadly classified into two categories: **Command Line Shell** and **Graphical shell**

<br />

**2. Basic Shell Command**
- Display the File Content
  - **cat, less, more**
  - **nano**: use text editor
  - **head, tail**: print the first n / last (n-1) lines
- File and Directory Manipulation 
  - **mkdir**: create a directory 
  - **rmdir**: delete a directory if it is empty
  - **cp**: copy the files and directories from the source path to the destination path
  - **mv**: move the files or directories
  - **rm**: remove files or directories
  - **touch**: create or update a file 
- Extract, Sort and Filter Data
  - **strings**: cast binary/executable file to human-readable string 
  - **grep**: search for the specified text in a file
  - **sort**: sort the contents of files
  - **wc**: count the number of characters, words in a file
  - **cut**: cut a specified part of a file
- Basic Navigation Commands
  - **ls**: list all the files or folders
  - **ls -a**: list all files including the hidden files
  - **cd**: change the directory
  - **du**: show disk usage
  - **pwd**: show the present working directory
  - **man**: show all commands in Linux

For more details, please check:

- [Linux Document](https://linux.die.net/)
- [Unix and Shell commands](https://afni.nimh.nih.gov/pub/dist/edu/data/CD.expanded/AFNI_data6/unix_tutorial/misc/unix_commands.html#u-mcc-amp)
- [Open a text file in Linux terminal](https://itslinuxfoss.com/do-i-open-text-file-linux-terminal/#:~:text=To%20open%20a%20text%20file%20in%20a%20Linux%20terminal%2C%20we,the%20content%20on%20the%20terminal)

<br />

**3. Shell Script**

Shell scripts or shell program are the files where we can write shell commands to avoid repetitive work. These files is saved with `.sh` extension.

<br />

## SSH
**1. What is SSH?**
   
SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users a secure way to access a computer over an unsecured network. SSH also refers to the suite of utilities that implement the SSH protocol.

SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner.
> There are three different encryption technologies used by SSH:
> 1. Symmetrical encryption
> 2. Asymmetrical encryption
> 3. Hashing

<br />

**2. How does SSH work?**

To log in to a remote computer called **sample.ssh.com**:
<br /> `ssh sample.ssh.com`
> Each server has a **host key** which is normally generated automatically when the computer is first booted. It is a cryptographic key used for authenticating computers in the SSH protocol. 

<br />Specifying a different user name:
<br /> `ssh username@sample.ssh.com` or `ssh -l username sample.ssh.com`

<br />Configuring port forwarding:
<br /> `ssh -p port username@sample.ssh.com` or `ssh username@sample.ssh.com -p port`

<br />For more SSH commands, find them here: https://www.ssh.com/academy/ssh/command#ssh-command-in-linux

<br />

## Guideline
At the beginning, enter the command provided in the instance with terminal and log in with the provided password.

```
% ssh ctf-player@venus.picoctf.net -p 60264
The authenticity of host '[venus.picoctf.net]:60264 ([3.131.124.143]:60264)' can't be established.
ED25519 key fingerprint is SHA256:P1f6h95BrSVnJbm2AKhphfHHGEyAeThib/rN/AwKs24.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:3: [venus.picoctf.net]:60063
    ~/.ssh/known_hosts:6: [venus.picoctf.net]:60128
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[venus.picoctf.net]:60264' (ED25519) to the list of known hosts.
ctf-player@venus.picoctf.net's password: 
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-1041-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$
```
> Based on the default shell prompt, we can tell the shell type
> <br />Bourne shell: $
> <br />C shell: % 

<br />Continue to enter 'ls' once connected and there are 2 files turning up.

`1of3.flag.txt  instructions-to-2of3.txt`

<br/>Open the '1of3.flag.txt' file with command 'cat', we will get the first part of flag.

```
$ cat 1of3.flag.txt 
picoCTF{xxsh_
```

<br/>Open the 'instructions-to-2of3.txt', we get the instruction to the next part.

```
$ cat instructions-to-2of3.txt 
Next, go to the root of all things, more succinctly `/`
```

<br/>Follow the instruction, we go to the root and can list all file in that directory.

```
$ cd /
$ ls
2of3.flag.txt  boot  etc   instructions-to-3of3.txt  lib64  mnt  proc  run   srv  tmp  var
bin	       dev   home  lib			     media  opt  root  sbin  sys  usr
```

<br/>Open the '2of3.flag.txt', we will get the second part of flag.

```
$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
```

<br/>Open the 'instructions-to-3of3.txt', we get the instruction to the next part.

```
$ cat instructions-to-3of3.txt 
Lastly, ctf-player, go home... more succinctly `~`
```

<br/>Follow the instruction, we go to the home and can list all file in that directory.

```
$ cd ~
$ ls
3of3.flag.txt  drop-in
```

<br/>Now we open the '3of3.flag.txt' to get the final part of flag. (Hooray!)

```
$ cat 3of3.flag.txt 
c1754242}
```

<br/>Finally, assemble selected parts in order to the complete flag, that is 'picoCTF{xxsh_0ut_0f_\/\/4t3r_c1754242}'. Type it in the answer box, the connection will terminate automatically and you capture the flag successfully!


