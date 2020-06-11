# Day 1: Inventory Management

![Elf](https://i.imgur.com/aRLtv7m.gif)

Elves needed a way to submit their inventory - have a web page where they submit their requests and the elf mcinventory can look at what others have submitted to approve their requests. It’s a busy time for mcinventory as elves are starting to put in their orders. mcinventory rushes into McElferson’s office.


>I don’t know what to do. We need to get inventory going. Elves can log on but I can’t actually authorise people’s requests! How will the rest start manufacturing what they want.  

McElferson calls you to take a look at the website to see if there’s anything you can do to help. 

[Support materials](https://docs.google.com/document/d/1PHs7uRS1whLY9tgxH1lj-bnEVWtXPXpo45zWUlbknpU/edit)

---

## 1. What is the name of the cookie used for authentication?

Inspect cookies in browser developer view.

Answer:
```
authid
```

## 2. If you decode the cookie, what is the value of the fixed part of the cookie?

Register different users with different usernames and decode the cookie value for each of them -> username is part of the cookie value but there is some common part for all of them.

```bash
echo dXNlcm5hbWV2NGVyOWxsMSFzcw== | base64 -d
```

Answer:
```
v4er9ll1!ss
```

## 3. After accessing his account, what did the user mcinventory request?

Login as `mcinventory` user by preparing user cookie:
`${username}v4er9ll1!ss`

```bash
echo "mcinventoryv4er9ll1!ss" | base64
```

Answer:
```
firewall
```

------

**Main: [The Story](../)**
**Next: [Day 2: Arctic Forum](../02/)**