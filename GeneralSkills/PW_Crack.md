# PW Crack
## PW Crack 1
**Description**

> Can you crack the password to get the flag?
> Download the password checker here and you'll need the encrypted flag in the same directory too.

<br />

**Guideline**

After download, we get two files that are `level1.py` and `level1.flag.txt.enc`. When we try to run those two files in terminal, we will get
```
$ python level1.py level1.flag.txt.enc
Please enter correct password for flag:
```

To get the password, open the `level1.py` and we can see this function
```
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "1e1a"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
```

From the `if( user_pw == "1e1a")`, we can get the password "1e1a"

After entering the password, we can get the flag `picoCTF{545h_r1ng1ng_fa343060}`

<br />

## PW Crack 2
**Description**

> Can you crack the password to get the flag?
> Download the password checker here and you'll need the encrypted flag in the same directory too.

<br />

**Guideline**

After download, we get two files that are `level2.py` and `level2.flag.txt.enc`.

Having the experience before, we open `level2.py` file directly and look into the following function
```
def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
```

It seems that the password is `chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)` which still need the convertion from hexidecimal number to ASCII character. Of course you can convert them one by one using `echo` command or corresponding converter. However, you can use a little trick to print the password directly as followed
```
def level_2_pw_check():
    print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
```

Then when you run those files in terminal, you will see that the password just showing up at the first line
```
$ python level2.py level2.flag.txt.enc
de76
Please enter correct password for flag: de76
```

After entering the password, we can get the flag `picoCTF{tr45h_51ng1ng_489dea9a}`

<br />

## PW Crack 3
**Description**

> Can you crack the password to get the flag?
> Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
> There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

<br />

**Guideline**

After getting the provided file, we open the `level3.py` first and look into the following code block
```
def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]
```

Based on the description, the correct password is inside the `pos_pw_list`. So we can use `for` loop to solve that lengthy work rather than try it one by one. The specific operation is as followed 
```
def level_3_pw_check():
    #user_pw = input("Please enter correct password for flag: ")
    pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]
    for user_pw in pos_pw_list:
        user_pw_hash = hash_pw(user_pw)
        
        if( user_pw_hash == correct_pw_hash ):
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), user_pw)
            print(decryption)
            return
        #print("That password is incorrect")
```

After that when we run the files, it will show us the pico flag directly even without password

The flag is `picoCTF{m45h_fl1ng1ng_cd6ed2eb}`

<br />

## PW Crack 4
**Description**

> Can you crack the password to get the flag?
> Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
> There are 100 potential passwords with only 1 being correct. You can find these by examining the password checker script.

<br />

**Guideline**

The solution is the same as PW Crack 3

<br />

## PW Crack 5
**Description**

> Can you crack the password to get the flag?
> Download the password checker here and you'll need the encrypted flag and the hash in the same directory too. Here's a dictionary with all possible passwords based on the password conventions we've seen so far.

<br />

**Guideline**

The difference between Crack 5 and Crack 3,4 is that the correct is inside one txt file but not a list, which means we have to read the file and transfer data in list using `split()`. The specific changes to python file is as below
```
def level_5_pw_check():
    password = open('dictionary.txt', 'r').read().split()
    for user_pw in password:
        
        user_pw_hash = hash_pw(user_pw)
        
        if( user_pw_hash == correct_pw_hash ):
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), user_pw)
            print(decryption)
            return
        #print("That password is incorrect")
```

After that we can easily get the flag when running it. The flag is `picoCTF{h45h_sl1ng1ng_40f26f81}`