# TryHackMe Grep

<div style="text-align: center;">
  <img src="/assets/grep1.webp" alt="mannaully
" width="600">
</div>

```
TryhackMe Machine:- Grep
Machine Info:- OSINT, WEB and Recon
Machine level: Easy
```

---
```
Welcome to the OSINT challenge, part of TryHackMe’s Red Teaming Path. 
In this task, you will be an ethical hacker aiming to exploit a newly 
developed web application.SuperSecure Corp, a fast-paced startup, is 
currently creating a blogging platform inviting security professionals 
to assess its security. The challenge involves using OSINT techniques 
to gather information from publicly accessible sources and exploit potentialvulnerabilities in the web application.Start by deploying 
the machine; Click on the Start Machine button in the upper-right-handcorner 
of this task to deploy the virtual machine for this room.Your goal is 
to identify and exploit vulnerabilities in the application using a 
combination of recon and OSINT skills. As you progress, you’ll look 
for weak points in the app, find sensitive data, and attempt to gain
unauthorized access. You will leverage the skills and knowledge acquired
through the Red Team Pathway to devise and execute your attack 
strategies.Note: Please allow the machine 3 - 5 minutes to fully boot. 
Also, no local privilege escalation is necessary to answer the questions.
```

There are 5 questions in total anyway I started the machine and got the IP One thing to keep in mind is that we must focus more on the OISNT and Recon.

Then did an Nmap scan.

```bash
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-26 13:03 ISTNmap scan report for 10.10.94.60Host is up (0.16s latency).Not shown: 997 closed tcp ports (reset)PORT    STATE SERVICE  VERSION22/tcp  open  ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)| ssh-hostkey:|   3072 1e:18:65:17:68:fc:06:d6:f7:21:bd:7c:16:71:e8:eb (RSA)|   256 69:ef:62:fe:d3:cb:8c:62:e3:14:f5:c1:92:10:75:b0 (ECDSA)|_  256 fa:84:c0:4d:ff:24:ca:96:a2:0d:7a:ed:19:0c:93:45 (ED25519)80/tcp  open  http     Apache httpd 2.4.41 ((Ubuntu))|_http-title: Apache2 Ubuntu Default Page: It works|_http-server-header: Apache/2.4.41 (Ubuntu)443/tcp open  ssl/http Apache httpd 2.4.41| tls-alpn:|_  http/1.1|_ssl-date: TLS randomness does not represent time|_http-title: 403 Forbidden|_http-server-header: Apache/2.4.41 (Ubuntu)| ssl-cert: Subject: commonName=grep.thm/organizationName=SearchME/stateOrProvinceName=Some-State/countryName=US| Not valid before: 2023-06-14T13:03:09|_Not valid after:  2024-06-13T13:03:09Service Info: Host: ip-10-10-94-60.eu-west-1.compute.internal; OS: Linux; CPE: cpe:/o:linux:linux_kernelService detection performed. Please report any incorrect results at https://nmap.org/submit/ .Nmap done: 1 IP address (1 host up) scanned in 26.10 seconds
```

So ports 80 (HTTP) and 443(HTTPS) are open.

I added it grep.thm to /etc/hosts.

And open again run the directory brute force attack.

<div style="text-align: center;">
  <img src="/assets/grep2.webp" alt="mannaully
" width="550">
</div>
The following were giving 200 so I visited /public/html/login.php/public/html/login.php/public/html/logout.php/public/html/register.php .

<div style="text-align: center;">
  <img src="/assets/grep3.webp" alt="mannaully
" width="550">
</div>
So I tried some default credentials and it didn’t work so I went to the registration page register a random user but it failed says.

Captured the request in the burp suite and checked now maybe we have another API key somewhere.

So I looked back at the index page it says SearchMe let’s search this on GitHub and hope to find something about there plus it is built using PHP so we have much more help in filtering.

<div style="text-align: center;">
  <img src="/assets/grep4.webp" alt="mannaully
" width="550">
</div>
And searched a bit more and found the user and also the API key in the history section in one of the file.

<div style="text-align: center;">
  <img src="/assets/grep5.webp" alt="mannaully
" width="550">
</div>

I edited the API key in the burp suite and again sent it and we successfully registered.

<div style="text-align: center;">
  <img src="/assets/grep6.webp" alt="mannaully
" width="550">
</div>

Now login as the new registered user.

<div style="text-align: center;">
  <img src="/assets/grep7.webp" alt="mannaully
" width="550">
</div>

And we got the first flag after we logged in.

Again performed a directory brute force and found 1.

```bash
/index.php (Status: 200) [Size: 1471]  /index.php (Status: 200) [Size: 1471]  /login.php (Status: 200) [Size: 1981]  /logout.php (Status: 200) [Size: 154]  /register.php (Status: 200) [Size: 2346]  /upload.php (Status: 403) [Size: 0]
```

upload.php

<div style="text-align: center;">
  <img src="/assets/grep8.webp" alt="mannaully
" width="550">
</div>

Now we can upload a reverse shell here but only jpg png so we have to do something about that Let’s first get a reserve shell and don’t forget to change your ip and port in the reverse shell.

I got the reverse shell from [https://github.com/pentestmonkey/php-reverse-shell.git](https://github.com/pentestmonkey/php-reverse-shell.git)

We can’t yet upload the file. we have to modify it by adding (ff d8 ff e0) at the beginning of the file hex in order to get valid magic bytes. I used cyber chef to do this.

<div style="text-align: center;">
  <img src="/assets/grep9.webp" alt="mannaully
" width="550">
</div>

Now we can upload this file you just need to export this file and it will be readen as a png file now we will upload this file.

<div style="text-align: center;">
  <img src="/assets/grep10.webp" alt="mannaully
" width="550">
</div>

<div style="text-align: center;">
  <img src="/assets/grep11.webp" alt="mannaully
" width="550">
</div>

Now open /api/uploads.

<div style="text-align: center;">
  <img src="/assets/grep12.webp" alt="mannaully
" width="550">
</div>

Get your listener ready and open the file.

<div style="text-align: center;">
  <img src="/assets/grep13.webp" alt="mannaully
" width="550">
</div>

And we got in.

Now go to /var/www /backup there you will find users.sql file.

<div style="text-align: center;">
  <img src="/assets/grep14.webp" alt="mannaully
" width="550">
</div>

And got the admin’s mail and also found a new subdomain.

<div style="text-align: center;">
  <img src="/assets/grep15.webp" alt="mannaully
" width="550">
</div>

Again I added this to my host fileI was unable to visit so I again did a Nmap scan this time scanning all ports using -p- flag and got a new port and added it as a port the page responded.

And on visiting and putting in the admins’ mail.

<div style="text-align: center;">
  <img src="/assets/grep16.webp" alt="mannaully
" width="550">
</div>

<div style="text-align: center;">
  <img src="/assets/grep17.webp" alt="mannaully
" width="550">
</div>

We got the final flag.

Thank you for reading
