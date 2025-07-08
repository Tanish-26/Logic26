# TryHackMe Committed

<div style="text-align: center;">
  <img src="/assets/committed1.webp" alt="mannaully
" width="600">
</div>

```
TryhackMe Machine:- Git Happens
Machine Info:- (Git)
Machine Level:- Easy
```

---

As soon as you start the machine a new window will open up and a web-based VM machine will start.

<div style="text-align: center;">
  <img src="/assets/committed2.webp" alt="mannaully
" width="600">
</div>

Now you will be able to see a zip file commited.zip.This file does not have a password to unzip. So you can just use unzip commited.zip to unzip it, and you will be able to see its contents.

<div style="text-align: center;">
  <img src="/assets/committed3.webp" alt="mannaully
" width="600">
</div>

There are 2 files and a “.git” folder; there is nothing in the main.py and “readme.md”, i looked in the “.git”.

<div style="text-align: center;">
  <img src="/assets/committed4.webp" alt="mannaully
" width="600">
</div>

I have used git show command to check the history of the repo.

<div style="text-align: center;">
  <img src="/assets/committed5.webp" alt="mannaully
" width="600">
</div>

In the logs folder, “HEAD” found the commits and found a weird commit called Oops.

<div style="text-align: center;">
  <img src="/assets/committed6.webp" alt="mannaully
" width="600">
</div>

So i copied the ID and used it.

git show (followed by the id).

<div style="text-align: center;">
  <img src="/assets/committed7.webp" alt="mannaully
" width="600">
</div>

We got the flag.

Although these labs are very easy, they cover the basics of git That's why im doing these labs. I will soon start medium-level labs too.thank you for reading.
