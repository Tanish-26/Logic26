# HackTheBox LoveTok

![Open Lightbox](../assets/lovetok1.webp){ .glightbox .center width="600" }
```
HTB-Challenges:- Web   
Challenge Info:- Web-Application-based challenge   
Challenge level:- Easy
```

---
Started off by downloading the files and starting the machine as soon as the machine started.   
there was an IP followed by a port so it was obvious that that was the only port which is open.   
I didn’t perform any Nmap scan.

again 

![Open Lightbox](../assets/lovetok2.webp){ .glightbox .center width="500" }
there was a flag which is a test flag if you see this don’t get excited.

![Open Lightbox](../assets/lovetok3.webp){ .glightbox .center width="500" }
So I opened the web page there was this fancy page and a Big GIF.

![Open Lightbox](../assets/lovetok4.webp){ .glightbox .center width="500" }
Now I also did a directory brute force bcoz I miss things easily but found nothing but on clicking.   
try again! another link opened up with a parameter.

```URL
http://142.93.32.153:30559/?format=r
```
I tried Linux commands ls and cat to check what happened and as a result, some text was changing

![Open Lightbox](../assets/lovetok5.webp){ .glightbox .center width="500" }
Now I had to look for some way to execute the command so I thought to look into the files downloaded and in a file router.php and found that when we input some text we will be prompted to error.   
what we need here is a web shell so I looked at Google for some payloads and eventually found one that was made for the lab I guess lol.

```bash
${system($\_GET[cmd])}&cmd=ls /
```
now let’s understand how this payload works.

```   
system:- The **system. functions** object allows you to call a particular Service Manager RAD function from JavaScript.  
and GET is an HTTP request   
cmd is used to call the command   
& is used to add another command or object in the parameter  
cmd=ls is basically we used cmd to store ls   
this whole works as our payload
```

![Open Lightbox](../assets/lovetok6.webp){ .glightbox .center width="500" }
This payload works we can see flagmVbY8.

![Open Lightbox](../assets/lovetok7.webp){ .glightbox .center width="500" }
And there we go we got the flag I used cat /flagmVbY8

Thank you for reading


