# What's a net cat
## Description
> Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `25103` to get the flag?

<br />

## Net Cat
**1. What is Net Cat?**

Netcat is a networking utility with the help of TCP/IP protocol which reads and writes data across network connections. Netcat is built as a secure back-end tool and can be used to send files from a client to a server and back directly with other programmes and scripts.

Netcat Uses Include:
- Data transfer
- Relays
- Port scanning
- Reverse shell
- Creating chats
- TCP commands

<br />

**2. Basic Netcat Command**

To connect to somewhere: `nc [-option] host port[s] port`
<br />To list all available commands: `nc -h`

For more details, please check: https://linux.die.net/man/1/nc

<br />

## Guideline

Enter the connect command into terminal and capture the flag

```
$ nc jupiter.challenges.picoctf.org 25103
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_d0c64587}
```
