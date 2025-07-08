# TryHackMe TakeOver

<div style="text-align: center;">
  <img src="/assets/takeover1.webp" alt="mannaully
" width="600">
</div>
```
TryhackMe Machine:- Takeover
Machine Info:- 
Machine Level:- Easy
```

---
Takeover is a free room in TryHackme it is a Web-based CTF, It is an easy room that focuses mainly on recon.

as you start room you will be greeted with the message and 1 Task.

```
Hello there,    I am the CEO and one of the co-founders of futurevera.thm. 
In Futurevera, we believe that the future is in space. We do a lot of space
research and write blogs about it. We used to help students with space questions, 
but we are rebuilding our support.  Recently blackhat hackers approached us saying 
they could takeover and are asking us for a big ransom. Please help us to find 
what they can takeover. Our website is located at [https://futurevera.thm](https://
futurevera.thm/)Hint: Don't forget to add the 10.10.108.68 in /etc/hosts for 
futurevera.thm ;)
```

Got the IP and started an Nmap scan.

```bash
nmap -sC -sV 10.10.54.233Starting Nmap 7.94 ( https://nmap.org ) at 
2023-10-22 00:17 ISTStats: 0:00:58 elapsed; 0 hosts completed (1 up), 
1 undergoing Script ScanNSE Timing: About 98.58% done; 
ETC: 00:18 (0:00:00 remaining)Nmap scan report for 10.10.54.233
Host is up (0.15s latency).Not shown: 997 closed tcp ports 
(conn-refused)PORT    STATE SERVICE  VERSION22/tcp  open  ssh
OpenSSH 8.2p1 Ubuntu 4ubuntu0.4 (Ubuntu Linux; protocol 2.0)|
ssh-hostkey:|   3072 dd:29:a7:0c:05:69:1f:f6:26:0a:d9:28:cd:40:f0:20 (RSA)|   
256 cb:2e:a8:6d:03:66:e9:70:eb:96:e1:f5:ba:25:cb:4e (ECDSA)|_  256 
50:d3:4b:a8:a2:4d:1d:79:e1:7d:ac:bb:ff:0b:24:13 (ED25519)80/tcp  open  http     
Apache httpd 2.4.41 ((Ubuntu))|_http-server-header: Apache/2.4.41 (Ubuntu)|
_http-title: Did not follow redirect to https://futurevera.thm/443/tcp open  ssl/
http Apache httpd 2.4.41 ((Ubuntu))|_ssl-date: TLS randomness does not represent 
time| tls-alpn:|_  http/1.1| ssl-cert: Subject: commonName=futurevera.thm/
organizationName=Futurevera/stateOrProvinceName=Oregon/countryName=US| Not valid 
before: 2022-03-13T10:05:19|_Not valid after:  2023-03-13T10:05:19|_http-title: 
FutureVera|_http-server-header: Apache/2.4.41 (Ubuntu)Service Info: OS: Linux; 
CPE: cpe:/o:linux:linux_kernelService detection performed. Please report any 
incorrect results at https://nmap.org/submit/ .Nmap done: 1 IP address (1 host up) 
scanned in 65.61 seconds
```

So firstly added futurevera.thm to /etc/host and the IP.

<div style="text-align: center;">
  <img src="/assets/takeover2.webp" alt="mannaully
" width="550">
</div>

And opened the URL.

![Image](https://cdn-images-1.medium.com/max/800/1*Y7-Ijg285zoW5HjHVxqVhA.png)
<div style="text-align: center;">
  <img src="/assets/takeover3.webp" alt="mannaully
" width="550">
</div>

And there was nothing on the web page it was a simple web pagealso, I started with subdomain enumeration using ffuf and found two subdomainsblog and support so I added them both to /etc/hosts.

```bash
ffuf -H  "Host : FUZZ.futurevera.thm" -u https://10.10.108.64 -w 
/Users/tanish/Documents/SecLists-master/Discovery/DNS
bitquark-subdomains-top100000.txt -fs 0,4605 /'___\  /'___\ 
/'___\       /\ \__/ /\ \__/  __  __  /\ \__/       \ \ ,__\
\ \ ,__\/\ \/\ \ \ \ ,__\        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ 
\_/         \ \_\   \ \_\  \ \____/  \ \_\          \/_/    \/
_/   \/___/    \/_/       v2.1.
0-dev________________________________________________ :: Method
: GET :: URL              : https://10.10.108.64 :: Wordlist         
: FUZZ: /Users/tanish/Documents/SecLists-master/Discovery/DNS/bitquark-subdomains-top100000.txt :: Header           : Host: 
FUZZ.futurevera.thm :: Follow redirects : false :: Calibration      
: false :: Timeout          : 10 :: Threads          : 40 :: Matcher          
: Response status: 200-299,301,302,307,401,403,405,500 :: Filter           
: Response size: 0,
4605________________________________________________blog                    
[Status: 200, Size: 3838, Words: 1326, Lines: 81, Duration: 156ms]
support                 [Status: 200, Size: 1522, Words: 367, Lines: 34, Duration: 
158ms]:: Progress: [120/100000] :: Job [1/1] :: 0 req/sec :: Duration: [0:00:00] 
:: Errors: 0 ::: Progress: [160/100000] :: Job [1/1] :: 0 req/sec :: Duration: 
[0:00:00] :: Errors: 0 ::: Progress: [200/100000] :: Job [1/1] :: 313 req/sec :: 
Duration: [0:00:01] :: Errors: 0
```

And again open the support.futurevera.thm and looked at the certificate i was able to see a DNS addressagain added it to /etc/hosts.

![Image](https://cdn-images-1.medium.com/max/800/1*xhJXiOhhoPU4VZndh4fLGw.png)
<div style="text-align: center;">
  <img src="/assets/takeover4.webp" alt="mannaully
" width="550">
</div>

Opened the URL and boom we got the flag.

<div style="text-align: center;">
  <img src="/assets/takerover5.webp" alt="mannaully
" width="550">
</div>

Thank you for reading
