# HackTheBox Illumination

![Open Lightbox](../assets/Illumination1.webp){ .glightbox .center width="600" }

```
HTB-Challenges:- Forensics  
Challenge Info:- Forensics (Git)  
Challenge level:- Easy
```

Downloaded the file and unzipped it.

![Open Lightbox](../assets/Illumination2.webp){ .glightbox .center width="500" }

And there were 3 files .git, bot.js and config.json I looked into the .git file and found a few more files.

![Open Lightbox](../assets/Illumination3.webp){ .glightbox .center width="500" }

Looked into the logs files and used git command to look into the logs.

```bash
git logs
```
![Open Lightbox](../assets/Illumination4.webp){ .glightbox .center width="500" }


See carefully that author has removed a unique token lets look into this.

```bash
git show 47241a47f62ada864ec74bd6dedc4d33f4374699
```
![Open Lightbox](../assets/Illumination5.webp){ .glightbox .center width="500" }


Now there is a token and a username both looks like a base64 encoding so   
lets decode them first lets try with the username.

![Open Lightbox](../assets/Illumination6.webp){ .glightbox .center width="500" }



And nothing now again i tried with token

![Open Lightbox](../assets/Illumination7.webp){ .glightbox .center width="500" }

And got the flag

Thank you for reading
