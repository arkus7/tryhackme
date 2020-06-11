# Day 2: Arctic Forum

![North Pole](https://i.imgur.com/e03Ta3j.png)

A big part of working at the best festival company is the social live! The elves have always loved interacting with everyone. Unfortunately, the christmas monster took down their main form of communication - the arctic forum! 

Elf McForum has been sobbing away McElferson's office. _How could the monster take down the forum!_ In an attempt to make McElferson happy, she sends you to McForum's office to help. 

[Support materials - Brute Forcing Directories](https://docs.google.com/document/d/1622ejYtCmLOS0zd16CyfhA1xgQk8l55gYWMY8fnpHfQ/edit)

---

## 1. What is the path of the hidden page?

Run dirsearch

```bash
./dirsearch.py -u http://$IP:3000 -e html -w ~/Downloads/DirBuster-Lists/directory-list-2.3-medium.txt
```

_Note: It took almost 8 minutes to find this directory_

Answer:
```
/sysadmin
```

## 2. What is the password you found?

After accessing `/sysadmin` open page source - there is a comment

```html
    <!--
    Admin portal created by arctic digital design - check out our github repo
    -->
```

When you google `arctic digital design` there is a [link to the repository](https://github.com/ashu-savani/arctic-digital-design) where in README.md file is the login and password.

Answer:
```
defaultpass
```

## 3. What do you have to take to the 'partay'

Login with credentials from the step above -> there is a note what you need to bring to the 'partay'

Answer:
```
Eggnog
```

------

**Main: [The Story](../)**
**Previous: [Day 1: Inventory Management](../01/)
**Next: [Day 3: Evil Elf](../02/)**