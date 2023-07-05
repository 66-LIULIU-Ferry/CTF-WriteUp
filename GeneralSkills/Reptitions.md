# Reptitions

## Description
> Can you make sense of this file?
> Download the file here.

<br />

## Solution

After opening the download file, there will be a string of encrypted characters
```
$ cat enc_flag 
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXcE9VazFXV2toT1dHUllDbUY2UWpSWk1GWlhWa2RHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
```

Based on the two equal signs at the end, we can tell it is encrypted with `base64`.

Therefore, after several decryptions, we can get the flag `picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_492767d2}`

What to be noted here is there will be error if you decrypt line by line as this will break the completion of string encrypted in Base64.