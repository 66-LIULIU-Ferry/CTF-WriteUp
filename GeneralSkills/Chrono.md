# Chrono
## Description
> How to automate tasks to run at intervals on linux servers?
> Additional details will be available after launching your challenge instance.

<br />

## Crontab

The cron command-line utility is a job scheduler on Unix-like operating systems. Users can use cron to schedule jobs to run periodically at fixed times, dates, or intervals.

The actions of cron are driven by a **crontab** file which is a list of commands that you want to run on a regular schedule.

**1. Write a cronjob**
<br />To create a cronjob, edit `crontab` using the `-e` option:
<br /> `$ crontab -e`

This opens crontab with default text editor. To set the text editor explictly, use the `EDITOR` environment variable:
<br /> `$ EDITOR=nano crontab -e`

**2. Crontab Syntax**

```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of the month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday;
# │ │ │ │ │                                   7 is also Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * <command to execute>
```

- **Asterisk (*)**: represent "all"
- **Comma (,)**: seperate items 
- **Dash (-)**: defines ranges
- **Slash (/)**: combined with range to specify step value
- **@reboot**: run once after reboot
- **@yearly**
- **@annually**
- **@monthly**
- **@weekly**
- **@daily**
- **@hourly**
> '* * * * *' means running at every minute

**3. Files**
<br /> `/etc/crontab`: main system crontab file
<br /> `/etc/cron.d`: directory for storing system crontabs
<br /> `/var/spool/cron/`: directory for storing crontabs defined by users

<br />

## Solution

First connect to the sever in the instance
<br /> `$ ssh picoplayer@saturn.picoctf.net -p 60767`

After connected, go to the home directory and check out all directories
```
$ cd /
$ ls
bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp  var
```

There are two ways to get the flag, first is go to the `challenge` directory and check the file inside
```
$ cd challenge
/challenge$ ls
metadata.json
/challenge$ cat metadata.json 
{"flag": "picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}", "username": "picoplayer", "password": "a-8nJGZCTa"}
```

The second way is turning to `etc/crontab` to search in system crontab file
```
/etc$ cat crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}
```

So the flag is `picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}`
