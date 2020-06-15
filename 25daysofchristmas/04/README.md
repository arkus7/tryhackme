# Day 4: Training

![Linux Tux in Christmas Hat](https://i.imgur.com/yHpBtpX.png)

With the entire incident, McElferson has been very stressed.

_We need all hands on deck now_

To help resolve things faster, she has asked you to help the new intern(mcsysadmin) get familiar with Linux. 
Access the machine via SSH on port 22 using the command

```sh
ssh mcsysadmin@[your-machines-ip]
```

username: `mcsysadmin`
password: `bestelf1234`

[Supporting materials - Linux File Structure](https://docs.google.com/document/d/1CpwM_MdHgRqlPSe4eCC_-rVgi8F1xh88PKOySTRSkxU/edit)

---

## 1. How many visible files are there in the home directory(excluding ./ and ../)?

```sh
ls -l 
```

Answer:

```
8
```

## 2. What is the content of file5?

```sh
cat file5
```

Answer:

```
recipes
```

## 3. Which file contains the string ‘password’?

```sh
grep -r password
# output:
# file6:passwordHpKRQfdxzZocwg5O0RsiyLSVQon72CjFmsV4ZLGjxI8tXYo1NhLsEply
```

Answer:
```
file6
```

## 4. What is the IP address in a file in the home folder?

Find IP by using part of the pattern with `grep`

```sh
grep -r -E "[0-9]+\."
```

Answer:
```
10.0.0.05
```

## 5. How many users can log into the machine?

Use `/etc/passwd` file to check who can log into the machine.

_Note: If the entrypoint is `/sbin/nologin` it means they can't login_

```sh
cat /etc/passwd | grep bash
# output:
# root:x:0:0:root:/root:/bin/bash
# ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
# mcsysadmin:x:1001:1001::/home/mcsysadmin:/bin/bash
```

Answer:
```
3
```

## 6. What is the sha1 hash of file8?

Use `sha1sum` to generate hash of the file.

```sh
sha1sum file8
```

Answer:
```
fa67ee594358d83becdd2cb6c466b25320fd2835
```

## 7. What is mcsysadmin’s password hash?

Typically we would check contents of `/etc/shadow` file, but we don't have read access to it on this machine from `mcsysadmin` account.

Check what the user was doing before we took control over the machine. After listing files in home directory we can see that there is a `.bash_history` file which might contain some useful information.

```sh
ls -la

cat .bash_history
```

Output:
```
ls -la
cd /home/ec2-user/
ls
cd /home/mcsysadmin/
ls
rm -rf generate.sh 
cat .bash_history 
rm -rf .bash_history 
exit
```

As we can see above, user was using some scripts that were removed.

Let's try to find backup files by looking for files with `*.bak` extension

```sh
find / -name *.bak 2>/dev/null
```

_Note: Since we can't read many files as this user, let's forward error output to `/dev/null` so we can see only files we have read access to._

Output:
```
/etc/nsswitch.conf.bak
/var/shadow.bak
```

`shadow.bak` file looks promising, and it's contents look like `/etc/shadow` file could look like. We can find the password hash in this file.

Answer:
```
$6$jbosYsU/$qOYToX/hnKGjT0EscuUIiIqF8GHgokHdy/Rg/DaB.RgkrbeBXPdzpHdMLI6cQJLdFlS4gkBMzilDBYcQ
```
