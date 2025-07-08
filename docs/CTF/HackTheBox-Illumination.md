# HackTheBox Illumination

<div style="text-align: center;">
  <img src="/assets/Illumination1.webp" alt="mannaully
" width="600">
</div>

```
HTB-Challenges:- Forensics  
Challenge Info:- Forensics (Git)  
Challenge level:- Easy
```

Downloaded the file and unzipped it.

<div style="text-align: center;">
  <img src="/assets/Illumination2.webp" alt="mannaully
" width="550">
</div>

And there were 3 files .git, bot.js and config.json I looked into the .git file and found a few more files.


<div style="text-align: center;">
  <img src="/assets/Illumination3.webp" alt="mannaully
" width="550">
</div>

Looked into the logs files and used git command to look into the logs.

```bash
git logs
```
<div style="text-align: center;">
  <img src="/assets/Illumination4.webp" alt="mannaully
" width="550">
</div>

See carefully that author has removed a unique token lets look into this.

```bash
git show 47241a47f62ada864ec74bd6dedc4d33f4374699
```
<div style="text-align: center;">
  <img src="/assets/Illumination5.webp" alt="mannaully
" width="550">
</div>


Now there is a token and a username both looks like a base64 encoding so   
lets decode them first lets try with the username.

<div style="text-align: center;">
  <img src="/assets/Illumination6.webp" alt="mannaully
" width="550">
</div>


And nothing now again i tried with token

<div style="text-align: center;">
  <img src="/assets/Illumination7.webp" alt="mannaully
" width="550">
</div>

And got the flag

Thank you for reading
