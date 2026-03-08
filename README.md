# OverTheWire---Bandit

logged in using ssh bandit0@bandit.labs.overthewire.org -p 2220
passwd was in readme
passwd: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If <- bandit1 passwd

logged in using ssh bandit1@bandit.labs.overthewire.org -p 2220
a file with name '-' was found
read it using cat ./-
passwd: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx <- bandit2 passwd

logged in using ssh bandit2@bandit.labs.overthewire.org -p 2220
a file with name '--spaces in this filename--'
read it using cat "./--spaces in this filename--"
passwd: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx <- bandit3 passwd

logged in using ssh bandit3@bandit.labs.overthewire.org -p 2220
file was inhere, did cd and hidden file '...hiding-from-you' was found
read it
passwd: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ <- bandit4 passwd

logged in using ssh bandit4@bandit.labs.overthewire.org -p 2220
9 files were present and only one was human readable,
did file command on all and only -file07 file was ascii
passwd: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw <- bandit5 passwd

logged in using ssh bandit5@bandit.labs.overthewire.org -p 2220
used find . -type f -size 1033c -exec file {} + | grep text
as it was told to find the file with human readable text and size only 1033 bytes
passwd: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG <- bandit6 passwd

logged in using ssh bandit6@bandit.labs.overthewire.org -p 2220
was said that the passwd was stored in a file owned by bandit7 and group was bandit6
did cd / and then find . -type f -size 33c -user bandit7 -group bandit6
passwd: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj <- bandit7 passwd

logged in using ssh bandit7@bandit.labs.overthewire.org -p 2220
cat data.txt | grep millionth
passwd: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc <- bandit8 passwd

logged in using ssh bandit8@bandit.labs.overthewire.org -p 2220
did sort data.txt | uniq -u to find the only one unique line 
passwd: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM <- bandit9 passwd

logged in using ssh bandit9@bandit.labs.overthewire.org -p 2220
strings data.txt | grep ====
passwd: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey <- bandit10 passwd

logged in using bandit10@bandit.labs.overthewire.org -p 2220
got data.txt and got base64 decoded and got passwd
passwd: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr <- bandit11 passwd

logged in using ssh bandit11@bandit.labs.overthewire.org -p 2220
this time the data was rotated by 13 places
passwd: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 <- bandit12 passwd

logged in using ssh bandit12@bandit.labs.overthewire.org -p 2220
found the hexdump of a multiple times zipped file
copied the hexdump and created a local text file with that dump
performed xxd -r data.txt > recovered.data
then uncompressed the recovered.data file multiple times by recognizing the extensions
finally a bin file was recovered with ascii value
passwd: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn <- bandit13 passwd

logged in using ssh bandit13@bandit.labs.overthewire.org -p 2220
got a private ssh key
copied it and made a local file names sshkey on linux local attack machine
did chmod 700 sshkey to make it accessible for owner only

logged in using ssh -i sshkey bandit14@bandit.labs.overthewire.org -p 2220 <- this was logging in without passwd and only sshkey
it was said that the passwd for next level is in /etc/bandit_pass/bandit14 
which was only readable by user bandit14, did cat and passwd was recovered
passwd: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS <- bandit14 passwd

logged in using ssh bandit14@bandit.labs.overthewire.org -p 2220 <- this was with actual passwd
said t o submit the passwd of current level to the port 30000 of localhost
performed cat /etc/bandit_pass/bandit14 | nc localhost 30000
got Correct!
passwd: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo <- bandit15 passwd

logged in using ssh bandit15@bandit.labs.overthewire.org -p 2220 
echo 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo | ncat --ssl localhost 30001
got the passwd by the system giving back correct
passwd: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx <- bandit16 passwd

logged in using ssh bandit16@bandit.labs.overthewire.org -p 2220 
PORT      STATE SERVICE     REASON  VERSION
31046/tcp open  echo        syn-ack
31518/tcp open  ssl/echo    syn-ack
31691/tcp open  echo        syn-ack
31790/tcp open  ssl/unknown syn-ack
31960/tcp open  echo        syn-ack
All ports contain echo service that gives the same stuff back except 31790
openssl s_client -connect localhost:31790 -quiet <- used quite because the starting of passwd of bandit16 was being treated as part of some syntax
for the private rsa key
used the same method as bandit14 by chmod the local sshkey file
passwd: EReVavePLFHtFlFsjn3hyzMlvSuSAcRD <- bandit17 passwd

logged in using ssh bandit17@bandit.labs.overthewire.org -p 2220 
did cmp old new
returned that line 42 in new is different
copied and that was the passwd
passwd: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO <- bandit18 passwd

logged in using ssh bandit18@bandit.labs.overthewire.org -p 2220 
but as the challenge said that there were some misconfigurations in the .bashrc file that immediately logged the player out when tried to ssh
to solve the issue tried to perform: ssh with /bin/bash --noprofile --norc
which didn't work as the ssh was stuck after entering the password
then tried to do ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh as that tries to avoid being logged out from a remote server
it worked and got logged in but as a guest I think and got a readme and performed cat on it
passwd: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8 <- bandit19 passwd

logged in using ssh bandit19@bandit.labs.overthewire.org -p 2220 
was given the setuid file for bandit20 user
saw how different plausible commands can be used with the setuid executable file
performed './bandit20-do cat /etc/bandit_pass/bandit20'
passwd: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO <- bandit20 passwd

logged in using ssh bandit20@bandit.labs.overthewire.org -p 2220 
at first did ./suconnect 6996 passwdOfCurrentUser
but then it returned an error and the file on the other end that was supposed to compare the passwd, compared the error string instead
to solve this, as mentioned, made a listener on the other end by echo 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO | nc -l -p 22
it returned permission denied as 22 is a root privilege port only accessible by allowed users.
echo 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO | nc -l -p 6996 on the listener end
./suconnect 6996 passwdOfCurrentUser -> said it was correct and sent the passwd to the listener side
passwd: EeoULMCra2q0dSkYj561DX7s1CpBuOBt <- bandit21 passwd

logged in using ssh bandit21@bandit.labs.overthewire.org -p 2220 
it was said to look into /etc/cron.d
a file by name cronjob22 was present
that file consisted of a command that mentioned the dir : /usr/bin/cronjob22.sh
it gave back a the script consisting of bandit22 passwd
passwd: t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv <- bandit22 passwd {that was not the actual passwd, it was part of the command and temp file that stored the read passwd}
performed cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv which gave back the actual passwd
passwd: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q <- bandit22 passwd

logged in using ssh bandit22@bandit.labs.overthewire.org -p 2220 
this time, I read the file named cronjob_bandit23.sh in /usr/bin which was mentioned in /etc/cron.d/cronjob23
in it a certain command was being used to write the password to tmp file for the bandit23 user
performed the given command: echo I am user bandit23 | md5sum | cut -d ' ' -f 1 <- got the tmp path
again did cat /tmp/8ca319486bfbbc3663ea0fbe81326349
passwd: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga <- bandit23 passwd

logged in using ssh bandit23@bandit.labs.overthewire.org -p 2220
for this a cron script was given which was executing a file that was foo located in /var/spool/bandit24 named foo, it was not permitted to be read
it was said that cron job was executing this file constantly as a particular time interval so whatever written in it was being executed
tried to made a blank paswd.txt file in /tmp dir, giving it chmod 777
also made sh.sh which consisted:
cat /etc/bandit_pass/bandit24 > /tmp/paswd.txt
gave chmod 777 to sh.sh also
as cronjob was being executed repeatedly, the passd was copied after a while in paswd.txt
passwd: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 <- bandit24 passwd

logged in using ssh bandit24@bandit.labs.overthewire.org -p 2220
created a sh.sh file in /tmp
bandit24@bandit:/tmp$ cat sh.sh
#!/bin/bash
for i in {0000..9999}; do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i" done | nc localhost 30002
passwd: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4 <- bandit25 passwd

logged in using ssh bandit25@bandit.labs.overthewire.org -p 2220
a private ssh key for bandit26 was present in the bandit25 default directory
tried to login in but was logged out fro mthe sessioin and also user shell was not in /bin/shell
opened and logged in to user in a small terminal size
pressed v to open up vim
typed :e /etc/bandit_pass/bandit26 and got the passwd
typed :set shell=/bin/bash
passwd: s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ <-bandit 26 passwd

was already in bandit26@bandit.labs.overthewise.org -p 2220
and got a bandit27-do
did ./bandit27-do cat /etc/bandit_pass/bandit27
passwd: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB <- bandit27 passwd

logged in using ssh bandit27@bandit.labs.overthewire.org -p 2220
performed 'git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo'
got the clone on local machine of mine and repo had a readme with bandit28 passwd
passwd: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN <- bandit28 passwd

logged in using git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
did git log, there was a commit that fixed some kind of leak
did git show <commit name>
passwd: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

logged in using git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
nothing wsa there except readme saying no password in production 
so listed all the available branches by git branch -a
a dev branch was vailable so did git switch dev
there was the readme that gave direct passwd
passwd: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL <- bandit30 passwd

logged in using git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
did git tag -a to show all the tags done in hostory
showed a tag named secret
passwd: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy <- bandit31 passwd

logged in using git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
the readme said to push a file key.txt with May I come in? text
created the file with echo "text" > key.txt
git add -f key.txt
git commit -a
git push
passwd: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K <- bandit32 passwd

logged in using ssh bandit32@bandit.labs.overthewire.org -p 2220
it said uppercase terminal
excaped the terminal using $0
got the normal shell
did cat /etc/bandit_pass/bandit33
passwd: tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

logged in using ssh bandit33@bandit.labs.overthewire.org -p 2220
got to know that level 34 doesn't exists :)
