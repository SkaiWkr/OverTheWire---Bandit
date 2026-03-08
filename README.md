# OverTheWire Bandit Walkthrough

---

## Bandit Level 0 → 1

Logged in using:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Password was in **readme**.

```
passwd: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

← bandit1 passwd

---

## Bandit Level 1 → 2

Logged in using:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

A file with name `-` was found.

Read it using:

```bash
cat ./-
```

```
passwd: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

← bandit2 passwd

---

## Bandit Level 2 → 3

Logged in using:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

A file with name:

```
--spaces in this filename--
```

Read it using:

```bash
cat "./--spaces in this filename--"
```

```
passwd: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

← bandit3 passwd

---

## Bandit Level 3 → 4

Logged in using:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

File was in **inhere**.

```bash
cd inhere
```

Hidden file found:

```
...hiding-from-you
```

Read it.

```
passwd: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

← bandit4 passwd

---

## Bandit Level 4 → 5

Logged in using:

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

9 files were present and only **one was human readable**.

Used:

```bash
file *
```

Only `-file07` was ASCII.

```
passwd: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

← bandit5 passwd

---

## Bandit Level 5 → 6

Logged in using:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Needed to find file:

* human readable
* size **1033 bytes**

Used:

```bash
find . -type f -size 1033c -exec file {} + | grep text
```

```
passwd: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

← bandit6 passwd

---

## Bandit Level 6 → 7

Logged in using:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Password stored in file:

* owned by **bandit7**
* group **bandit6**
* size **33 bytes**

Command used:

```bash
cd /
find . -type f -size 33c -user bandit7 -group bandit6
```

```
passwd: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

← bandit7 passwd

---

## Bandit Level 7 → 8

Logged in using:

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

Search for word **millionth**.

```bash
cat data.txt | grep millionth
```

```
passwd: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

← bandit8 passwd

---

## Bandit Level 8 → 9

Logged in using:

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

Find unique line.

```bash
sort data.txt | uniq -u
```

```
passwd: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

← bandit9 passwd

---

## Bandit Level 9 → 10

Logged in using:

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

Use `strings`.

```bash
strings data.txt | grep ====
```

```
passwd: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

← bandit10 passwd

---

## Bandit Level 10 → 11

Logged in using:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

File was **Base64 encoded**.

```bash
base64 -d data.txt
```

```
passwd: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

← bandit11 passwd

---

## Bandit Level 11 → 12

Logged in using:

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

Data was **ROT13 encoded**.

Decoded and got:

```
passwd: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

← bandit12 passwd

---

## Bandit Level 12 → 13

File was **hexdump of multiple compressed files**.

Steps:

```bash
xxd -r data.txt > recovered.data
```

Then repeatedly **uncompressed** recognizing formats until ASCII file appeared.

```
passwd: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

← bandit13 passwd

---

## Bandit Level 13 → 14

Private SSH key found.

Copied locally:

```bash
chmod 700 sshkey
```

Login using:

```bash
ssh -i sshkey bandit14@bandit.labs.overthewire.org -p 2220
```

Password stored in:

```
/etc/bandit_pass/bandit14
```

```
passwd: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

---

## Bandit Level 14 → 15

Submit password to port **30000**.

```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

```
Correct!
```

```
passwd: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

← bandit15 passwd

---

## Bandit Level 15 → 16

SSL connection required.

```bash
echo 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo | ncat --ssl localhost 30001
```

```
passwd: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

← bandit16 passwd

---

## Bandit Level 16 → 17

Scanned ports.

```
31046 echo
31518 ssl/echo
31691 echo
31790 ssl/unknown
31960 echo
```

Only **31790** worked.

```bash
openssl s_client -connect localhost:31790 -quiet
```

Returned **private RSA key**.

Used again to login via SSH.

```
passwd: EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```

← bandit17 passwd

---

## Bandit Level 17 → 18

Compare files.

```bash
cmp old new
```

Difference at **line 42**.

```
passwd: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

← bandit18 passwd

---

## Bandit Level 18 → 19

`.bashrc` forced logout.

Bypassed shell:

```bash
ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh
```

Read `readme`.

```
passwd: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

← bandit19 passwd

---

## Bandit Level 19 → 20

Used **setuid binary**.

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

```
passwd: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

← bandit20 passwd

---

## Bandit Level 20 → 21

Listener trick.

```bash
echo 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO | nc -l -p 6996
```

Then:

```bash
./suconnect 6996 passwdOfCurrentUser
```

Password sent to listener.

```
passwd: EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```

← bandit21 passwd

---

## Bandit Level 21 → 22

Checked cron jobs.

```
/etc/cron.d
```

Script:

```
/usr/bin/cronjob22.sh
```

Temp file contained password.

```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

```
passwd: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

← bandit22 passwd

---

## Bandit Level 22 → 23

Script:

```
cronjob_bandit23.sh
```

Generated tmp file path:

```bash
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```

Then:

```bash
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

```
passwd: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

← bandit23 passwd

---

## Bandit Level 23 → 24

Cron executed files in:

```
/var/spool/bandit24
```

Created script:

```bash
cat /etc/bandit_pass/bandit24 > /tmp/paswd.txt
```

Waited for cron execution.

```
passwd: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

← bandit24 passwd

---

## Bandit Level 24 → 25

Brute forced 4-digit PIN.

```bash
for i in {0000..9999}; do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i"; done | nc localhost 30002
```

```
passwd: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

← bandit25 passwd

---

## Bandit Level 25 → 26

SSH login immediately exited.

Opened **small terminal**, triggered **vim**.

```vim
:e /etc/bandit_pass/bandit26
:set shell=/bin/bash
```

```
passwd: s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```

← bandit26 passwd

---

## Bandit Level 26 → 27

Used:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

```
passwd: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```

← bandit27 passwd

---

## Bandit Level 27 → 28

Cloned repo.

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

`README` contained password.

```
passwd: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

← bandit28 passwd

---

## Bandit Level 28 → 29

Checked git history.

```bash
git log
git show <commit>
```

```
passwd: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```

← bandit29 passwd

---

## Bandit Level 29 → 30

Listed branches.

```bash
git branch -a
git switch dev
```

Dev branch README had password.

```
passwd: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

← bandit30 passwd

---

## Bandit Level 30 → 31

Checked git tags.

```bash
git tag
```

Tag **secret** contained password.

```
passwd: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

← bandit31 passwd

---

## Bandit Level 31 → 32

Needed to push file.

```bash
echo "May I come in?" > key.txt
git add -f key.txt
git commit -a
git push
```

```
passwd: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

← bandit32 passwd

---

## Bandit Level 32 → 33

Terminal forced **uppercase**.

Escape using:

```bash
$0
```

Then:

```bash
cat /etc/bandit_pass/bandit33
```

```
passwd: tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

---

## Bandit Level 33

```
Level 34 doesn't exist :)
```

---

### End of Bandit
