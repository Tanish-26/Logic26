
# HackTheBox RenderQuest

![Open Lightbox](../assets/RenderQuest1.webp){ .glightbox .center width="600" }
```
HTB-Challenges- Web  
Challenge Info:- Web  
Challenge level:- Easy
```

---

CHALLENGE DESCRIPTION
```
You’ve found a website that lets you input remote templates for rendering. Your task is to exploit this system’s vulnerabilities to access and retrieve a hidden flag. Good luck!
```
download and the files and unzip it

![Open Lightbox](../assets/RenderQuest2.webp){ .glightbox .center width="500" }

In requirments file you will see a main.go file which basiclly contain all the request parameters for when you visit the the given ip and port you will be able to see a web page with a parameter which take inputs

so we can try using webhook here beccause it allows entering external link

we can externally build quires and the program will execute this

why ???

lets take a look at the source code the program that is executing all the progam after we click on the render now button


![Open Lightbox](../assets/RenderQuest3.webp){ .glightbox .center width="500" }
main.gowe will build the request accordingly using

[https://webhook.site/](https://webhook.site/#!/010b4caf-8d2b-4a73-b677-d5424f27af77/43e500a2-38e9-44df-a8f7-a76a5e067ac8/1)

lets try the FetchServerInfo first and test if it works or not

![Open Lightbox](../assets/RenderQuest4.webp){ .glightbox .center width="500" }
Now copy the user and paste it in the given parameter on the website

![Open Lightbox](../assets/RenderQuest5.webp){ .glightbox .center width="500" }
So it did work lets take step back in the directory and check

modiying the request accordingly

![Open Lightbox](../assets/RenderQuest6.webp){ .glightbox .center width="500" }

![Open Lightbox](../assets/RenderQuest7.webp){ .glightbox .center width="500" }

And we can see the flag you can modify the request and make it

![Open Lightbox](../assets/RenderQuest8.webp){ .glightbox .center width="500" }

Thank you for reading

