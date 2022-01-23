# Bandit overthewire

Bandid is a set of games to learn and effort knowledgments in Linux an some bash commands

### Level 0
The goal of this level is for you to log into the game using ssh. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level1 page to find out how to beat level1.

#### answer

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
### Level 1
the password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using ssh. Whenever you find a password for a level, use ssh(on port 2220) to log into that level and continue the game

#### answer
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
cat readme # password for user bandit1: boJ9jbbUNNfktd78OOpsqOltutMc3MY1
ssh bandit1@bandit.labs.overthewire.org -p 2220
```
### Level 2
the password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using ssh. Whenever you find a password for a level, use ssh(on port 2220) to log into that level and continue the game

#### answer
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
cat ./- # new password CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

### level 3
The password for the next level is stored in a file called spaces in this filename located in the home directory

#### answer
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
cat spaces\ in\ this\ filename # new password UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

### level 4
The password for the next level is stored in a hidden file in the inhere directory.


#### answer
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
cd inhere
ls -la
cat .hidden # new pass pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

### level 4 -> 5
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

#### answer
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
cd inhere
ls -la
cat ./-file07 # new pass koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
### level 5-> 6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the folling properties

#### answer
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
cd inhere
cat $(find -type f -size 1033c) # new password DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

### level 6 -> 7
the password for the next level is stored somewhere on the server and has all of the following properties:
  owned by user bandit7
  owned by group bandit6
  33 bytes in size

####
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -user bandit7 -group bandit6
cat /var/lib/dpkg/info/bandit7.password   # new password HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

### level 7 -> 8 

the password for the next level is stored in the file data.txt next to the word millionth

#### answer
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
cat data.txt | grep 'millionth'   # new password cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

### level 8 -> 9
the password for the next level is stored in the file data.txt and is the only line of text that occurs only once

#### answer
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
cat data.txt | sort | uniq -u   # new password UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

### level 9 -> 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several '======' characters.

#### answer
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
strings data.txt | grep '=='   # new password truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
### level 10 -> 11
the password for the next level is stored in the file data.txt, which contains base64 encoded data

#### answer
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
base64 -d data.txt   # new password IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

### level 11-> 12
the password for the next leve is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

#### answer
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' # new password 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

### level 12 -> 13
the passowrd for the next level isstored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. for this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example mkdir /tmp/myname123. Then copy de datafile using cp, and rename it using mv

#### answer
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
ls
mkdir /tmp/jensen
cp data.txt /tmp/jensen/
cd /tmp/jensen
xxd -r data.txt data

file data
mv data data.gz
gzip -d data.gz

file data
mv data data.bz2
bzip2 -d data.bz2

file data
mv data data.gz
gzip -d data.gz

file data
mv data data.tar
tar -xvf data.tar


file data5.bin
mv data5.bin data5.tar
tar -xvf data5.tar

file data6.bin
mv data6.bin data6.tar
tar -xvf data6.tar

file data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
file data8
cat data8  # the password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL 

```
### level 13 -> 14
the password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For his level, you don't get the next password, but you get a private ssh key that can be used to log into the nest level Note:localhost is ahostname that refers to the machine you are working on

#### answer
```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
cat sshkey.private
ssh -i sshkey.private bandit14@localhost
cat /etc/bandit_pass/bandit14 # new password 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

### level 14 -> 15

The passowrd for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost

#### answer
```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
telnet localhost 30000 # paste the latest password, the password obtained is BfMYroe26WYalil77FoDi9qh59eK5xNr

```

### level 15 -> 16
the password for the next level can be retrieved by submiting the password of the current level to port 30001 on localhost using ssl ecryption

Helpful note: Getting  HEARTBEATING and Read R BLOCK, use -ign_eof and read the CONNECTED COMMANDS section in the manpage. Next to R and Q the B command also works in this version of that command

#### answer
```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
openssl s_client -connect localhost:30001 # paste the latest password, the password obtained is cluFn7wTiGryunymYOu4RcffSxQluehd
```

### level 16 -> 17

the credentials for the next level can be retrieved by submitting the password fo the current level to a port on localhost in the range 31000 to 32000. First find outwich of these ports have a server stening on them, Then fin outwhich of those spal SSL and which dont. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
``` bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
nmap -p 31000-32000 localhost
cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -quiet

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

vim /tmp/jensen/ssh.private 
ssh -i /tmp/jensen/ssh.private bandit17@localhost
ssh 400 sshkey.private
ssh -i /tmp/jensen/ssh.private bandit17@localhost
cat /etc/bandit_pass/bandit17 # the password is xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
exit
rm -rf sshkey.private
```
### level 17 -> 18

there are 2 files in the homedirectory: passwords.old and passwords.new . The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this lveel and see ByeBye! when tryung to log into bandit18, this is related to the next level, bandit 19.

#### answer
```bash
diff passwords.old passwords.new # the password is kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```

### level 18 -> 19
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

#### answer
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash
ls -la
cat readme # the password is IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

### level 19 -> 20
to gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary

#### answer
```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220
 ./bandit20-do cat /etc/bandit_pass/bandit20 # the pass is GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
### level 20 -> 21
There is a setuid in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a conmmandile argument, It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level()


#### answers

first in terminal 1
```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
ls -la
./suconnect
nmap localhost
nc -lp 6000
```
next on terminal 2
```bash
./succonect 6000
```
finally on terminal 1:
```bash
paste the last pass in console # this will generate gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```


### level 21 -> 22
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

#### answers

```bash
ssh bandit21@bandit.labs.overthewire.org -p 2220

cat cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh 
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv 


#  Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```


### level 22 -> 23

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

#### answers
```bash
ssh bandit22@bandit.labs.overthewire.org -p 2220
cd /etc/cron.d
cat cronjob_bandid23
cat /usr/bin/cronjob_bandit23.sh
echo I am user bandit23 | md5sum
ls -l /usr/bin/cronjob_bandit23.sh
cat /tmp/8ca319486bfbbc3663ea0fbe81326349 ## pass jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n

```

### level 23 -> 24
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

#### answers
```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220
cd /etc/cron.d
cat cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh
mkdir /tmp/bandit24
chmod 777 /tmp/bandit24
cd /tmp/bandit24
vim index.sh
## inside file 
cat /etc/bandit_pass/bandit24 > /tmp/myname123/banditpass
## save file
chmod 777 index.sh
cp index.sh /var/spool/bandit24/
ls -la
cat banditpass ### password UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
rm -rf user123
```

### level 24-> 25

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

#### answers
```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220
nmap -p- localhost
 mkdir /tmp/myBandit24
cd /tmp/myBandit24
 vim index.sh
#inside file
#!/bin/bash
for i in {0000..9999}; do
    echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ" $i >> combinations.txt
done
# end of file

cat index.sh
chmod +x index.sh
./index.sh

cat combinations.txt | nc localhost 30002 # finally this will response you  uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

rm /tmp/myBandit24

exit
```
### level 25 -> 26
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

#### answers
```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
cat /etc/passwd | grep bandit26
cat /usr/bin/showtext
ls
# resising the terminal to minimal
ssh -i bandit26.sshkey bandit26@localhost 
# press v to enable edit
type:
:e /etc/bandit_pass/bandit26 
# the password is
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
```
### level 26 -> 27
Good job getting a shell! Now hurry and grab the password for bandit27!

#### answers
```bash
# minimizing terminal
ssh bandit26@bandit.labs.overthewire.org -p 2220

press v to start editor

:set shell ?
:set shell=/bin/bash
:set shell ?
:!ls
:!./bandit27-do cat /etc/bandit_pass/bandit27
# pass 3ba3118a22e93127a4ed485be72ef5ea
```
### level 27 -> 28
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user bandit27-git is the same as for the user bandit27.

#### answers
```bash
ssh bandit27@bandit.labs.overthewire.org -p 2220
mkdir /tmp/user123
cd /tmp/user123
git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
cd repo
cat readme # password 0ef186ac70e04ea33b4c1853d2526fa2
rm /tmp/user123
```

### level 28 -> 29
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

#### answers
```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
mkdir /tmp/user123
cd /tmp/user123
git clone ssh://bandit28-git@localhost/home/bandit27-git/repo
cd repo
git log 
git show edd**** # copy pass  bbc96594b4e001778eee9975372716b2
cd
rm -rf /tmp/user123

```

### level 29 -> 30
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.

####
```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
mkdir /tmp/user123
cd /tmp/user123
git clone ssh://bandit29-git@localhost/home/bandit27-git/repo
cd repo
git branch -a
git checkout dev
cat README.md # Passoword 5b90576bedb2cc04c86a9e924ce42faf
cd
rm -rf /tmp/user123

```


### level 30 -> 31
There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.
#### answer

```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
mkdir /tmp/user123
cd /tmp/user123
git clone ssh://bandit29-git@localhost/home/bandit27-git/repo
cd repo
git branch -a
git checkout dev
cat README.md
git tag
git show secret  # copy secret 47e603bb428404d265f59c42920d81e5
cd
rm -rf /tmp/user123

```

### level 31 -> 32
There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.

#### answers
```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
mkdir /tmp/user123
cd /tmp/user123
git clone ssh://bandit29-git@localhost/home/bandit27-git/repo
cd repo
cat README.md
echo "May I come in?" > key.txt
cat key.txt
git add -f key.txt
git commit -m "key.txt" 
git push origin master  # copy pass 56a9bf19c63d650ce78e6ec0354ee45e
cd
rm -rf /tmp/user123

```


### level 32 -> 33
After all this git stuff its time for another escape. Good luck!

#### answers
```bash
$0
ls -la
whoami
cat /etc/bandit_pass/bandit33 # pass c9c3199ddf4121b10cf581a98d51caee
```

### level 33 -> 34
```bash
cat README.txt
```








