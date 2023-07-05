# Permission

## Description
> Can you read files in the root file?
> Additional details will be available after launching your challenge instance.

<br />

## Solution

Connect to the server and go to the root with `cd /`
```
$ cd /
$ ls
bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp  var
```

Then find the flag in `challenge` directory
```
$ cd challenge/
challenge$ ls
metadata.json
challenge$ cat metadata.json 
{"flag": "picoCTF{uS1ng_v1m_3dit0r_021d10ab}", "username": "picoplayer", "password": "dLAqMvm7xv"}
```

So the flag is `picoCTF{uS1ng_v1m_3dit0r_021d10ab}`