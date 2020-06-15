# Day 3: Evil Elf

![Evil Elf](https://i.imgur.com/Tjpbxgq.png)

An Elf-ministrator, has a network capture file from a computer and needs help to figure out what went on! Are you able to help?

[Supporting materials - Wireshark and Password Cracking](https://docs.google.com/document/d/1ZVsOtW7mM-4neZZ4QtYCEp__exiMrvlUCXTxhB-zyxk/edit)

---

## 1. Whats the destination IP on packet number 998?

Open file in Wireshark -> check Destination column of 998th packet.

Answer:
```
63.32.89.195
```

## 2. What item is on the Christmas list?

Filter packets by telnet. There are 3 packets. In the first one (#2255) there is a command visible in packet data:

```bash
echo 'ps4' > christmas_list.txt
```

Answer:
```
ps4
```

## 3. Crack buddy's password!

In the second telnet packet (#2906) we can see that `/etc/shadow` file was printed on the console. This file contains password hashes.

```sh
cat /etc/shadow
```

In the next telnet packet (#2908) we can see the results of this command. We can see that the packet data contains hash of the `buddy` user's password hash.

```sh
root:*:18171:0:99999:7:::
daemon:*:18171:0:99999:7:::
bin:*:18171:0:99999:7:::
sys:*:18171:0:99999:7:::
sync:*:18171:0:99999:7:::
games:*:18171:0:99999:7:::
man:*:18171:0:99999:7:::
lp:*:18171:0:99999:7:::
mail:*:18171:0:99999:7:::
news:*:18171:0:99999:7:::
uucp:*:18171:0:99999:7:::
proxy:*:18171:0:99999:7:::
www-data:*:18171:0:99999:7:::
backup:*:18171:0:99999:7:::
list:*:18171:0:99999:7:::
irc:*:18171:0:99999:7:::
gnats:*:18171:0:99999:7:::
nobody:*:18171:0:99999:7:::
systemd-network:*:18171:0:99999:7:::
systemd-resolve:*:18171:0:99999:7:::
syslog:*:18171:0:99999:7:::
messagebus:*:18171:0:99999:7:::
_apt:*:18171:0:99999:7:::
lxd:*:18171:0:99999:7:::
uuidd:*:18171:0:99999:7:::
dnsmasq:*:18171:0:99999:7:::
landscape:*:18171:0:99999:7:::
sshd:*:18171:0:99999:7:::
pollinate:*:18171:0:99999:7:::
ubuntu:!:18232:0:99999:7:::
buddy:$6$3GvJsNPG$ZrSFprHS13divBhlaKg1rYrYLJ7m1xsYRKxlLh0A1sUc/6SUd7UvekBOtSnSyBwk3vCDqBhrgxQpkdsNN6aYP1:18233:0:99999:7:::
```

Save hash to the file
```sh
echo '$6$3GvJsNPG$ZrSFprHS13divBhlaKg1rYrYLJ7m1xsYRKxlLh0A1sUc/6SUd7UvekBOtSnSyBwk3vCDqBhrgxQpkdsNN6aYP1' > hash.txt
```

_Note: use single quotes, otherwise the `$6$3` is evaluated before writing to file as environmental variables -> hash is invalid._

Check the method number for cracking by comparing the first characters from the hash to the example hashes [on this site](https://hashcat.net/wiki/doku.php?id=example_hashes) - `$6` for `hashcat` is `1800`.

And start cracking using `hashcat` and wordlist from `rockyou`

```sh
hashcat -m 1800 hash.txt ~/Downloads/rockyou.txt --force --status
```

Answer:
```
rainbow
```

------

**Main: [The Story](../)**

**Previous: [Day 2: Arctic Forum](../02/)**

**Next: [Day 4: Training](../04/)**