# TryHackMe HeartBleed

<div style="text-align: center;">
  <img src="/assets/HeartBleed1.webp" alt="mannaully
" width="600">
</div>
```
TryhackMe Machine:- HeartBleed
Machine Info:- SSL
Machine Level:- Easy
```

---
Lab description

Task 2 Protecting Data In Transit.

In this task, you need to obtain a flag using a very well-known vulnerability. Make sure you pay attention to all the information and errors displayed. Pay particular attention to how web servers are configured.

The server may take 3–4 minutes to deploy and configure. Please be patient.

I started nmap scan.

```bash
 nmap -sV --script vuln 34.255.10.109Starting Nmap 7.94 ( https://nmap.org ) at
 2023-11-08 15:43 ISTPre-scan script results:| broadcast-avahi-dos:|   Discovered
 hosts:|     224.0.0.251|   After NULL UDP avahi packet DoS (CVE-2011-1002).|_  
 Hosts are all up (not vulnerable).Nmap scan report for ec2-34-255-10-109.
 eu-west-1.compute.amazonaws.com (34.255.10.109)Host is up (0.15s latency).Not 
 shown: 995 closed tcp ports (conn-refused)PORT    STATE    SERVICE  VERSION22/
 tcp  open     ssh      OpenSSH 7.4 (protocol 2.0)| vulners:|   cpe:/
 a:openbsd:openssh:7.4:|      PRION:CVE-2019-6111 5.8 https://vulners.com/prion/
 PRION:CVE-2019-6111|      EXPLOITPACK:98FE96309F9524B8C84C508837551A19 5.8 
 https://vulners.com/exploitpack/EXPLOITPACK:98FE96309F9524B8C84C508837551A19 
 *EXPLOIT*|      EXPLOITPACK:5330EA02EBDE345BFC9D6DDDD97F9E97 5.8 https://vulners.
 com/exploitpack/EXPLOITPACK:5330EA02EBDE345BFC9D6DDDD97F9E97 *EXPLOIT*|      
 EDB-ID:46516 5.8 https://vulners.com/exploitdb/EDB-ID:46516 *EXPLOIT*|      
 EDB-ID:46193 5.8 https://vulners.com/exploitdb/EDB-ID:46193 *EXPLOIT*|      
 CVE-2019-6111 5.8 https://vulners.com/cve/CVE-2019-6111|      1337DAY-ID-32328 5.
 8 https://vulners.com/zdt/1337DAY-ID-32328 *EXPLOIT*|      1337DAY-ID-32009 5.8 
 https://vulners.com/zdt/1337DAY-ID-32009 *EXPLOIT*|      SSH_ENUM 5.0 https://
 vulners.com/canvas/SSH_ENUM *EXPLOIT*|      PRION:CVE-2018-15919 5.0 https://
 vulners.com/prion/PRION:CVE-2018-15919|      PRION:CVE-2018-15473 5.0 https://
 vulners.com/prion/PRION:CVE-2018-15473|      PRION:CVE-2017-15906 5.0 https://
 vulners.com/prion/PRION:CVE-2017-15906|      PACKETSTORM:150621 5.0 https://
 vulners.com/packetstorm/PACKETSTORM:150621 *EXPLOIT*|      
 EXPLOITPACK:F957D7E8A0CC1E23C3C649B764E13FB0 5.0 https://vulners.com/exploitpack/
 EXPLOITPACK:F957D7E8A0CC1E23C3C649B764E13FB0 *EXPLOIT*|      
 EXPLOITPACK:EBDBC5685E3276D648B4D14B75563283 5.0 https://vulners.com/exploitpack/
 EXPLOITPACK:EBDBC5685E3276D648B4D14B75563283 *EXPLOIT*|      EDB-ID:45939 5.0 
 https://vulners.com/exploitdb/EDB-ID:45939 *EXPLOIT*|      EDB-ID:45233 5.0 
 https://vulners.com/exploitdb/EDB-ID:45233 *EXPLOIT*|      CVE-2018-15919 5.0 
 https://vulners.com/cve/CVE-2018-15919|      CVE-2018-15473 5.0 https://vulners.
 com/cve/CVE-2018-15473|      CVE-2017-15906 5.0 https://vulners.com/cve/
 CVE-2017-15906|      1337DAY-ID-31730 5.0 https://vulners.com/zdt/
 1337DAY-ID-31730 *EXPLOIT*|      PRION:CVE-2019-16905 4.4 https://vulners.com/
 prion/PRION:CVE-2019-16905|      CVE-2021-41617 4.4 https://vulners.com/cve/
 CVE-2021-41617|      CVE-2020-14145 4.3 https://vulners.com/cve/
 CVE-2020-14145|      PRION:CVE-2019-6110 4.0 https://vulners.com/prion/
 PRION:CVE-2019-6110|      PRION:CVE-2019-6109 4.0 https://vulners.com/prion/
 PRION:CVE-2019-6109|      CVE-2019-6110 4.0 https://vulners.com/cve/
 CVE-2019-6110|      CVE-2019-6109 4.0 https://vulners.com/cve/CVE-2019-6109|      
 PRION:CVE-2018-20685 2.6 https://vulners.com/prion/PRION:CVE-2018-20685|      
 CVE-2018-20685 2.6 https://vulners.com/cve/CVE-2018-20685|      
 PACKETSTORM:151227 0.0 https://vulners.com/packetstorm/PACKETSTORM:151227 
 *EXPLOIT*|      MSF:AUXILIARY-SCANNER-SSH-SSH_ENUMUSERS- 0.0 https://vulners.com/
 metasploit/MSF:AUXILIARY-SCANNER-SSH-SSH_ENUMUSERS- *EXPLOIT*|_     
 1337DAY-ID-30937 0.0 https://vulners.com/zdt/1337DAY-ID-30937 *EXPLOIT*111/tcp 
 open     rpcbind  2-4 (RPC #100000)| rpcinfo:|   program version    port/proto  
 service|   100000  2,3,4        111/tcp   rpcbind|   100000  2,3,4        111/
 udp   rpcbind|   100000  3,4          111/tcp6  rpcbind|   100000  3,4          
 111/udp6  rpcbind|   100024  1          35465/tcp   status|   100024  1          
 36511/udp   status|   100024  1          58279/tcp6  status|_  100024  1          
 58851/udp6  status179/tcp filtered bgp443/tcp open     ssl/http nginx 1.15.7| 
 ssl-ccs-injection:|   VULNERABLE:|   SSL/TLS MITM vulnerability (CCS 
 Injection)|     State: VULNERABLE|     Risk factor: High|       OpenSSL before 0.
 9.8za, 1.0.0 before 1.0.0m, and 1.0.1 before 1.0.1h|       does not properly 
 restrict processing of ChangeCipherSpec messages,|       which allows 
 man-in-the-middle attackers to trigger use of a zero|       length master key in 
 certain OpenSSL-to-OpenSSL communications, and|       consequently hijack 
 sessions or obtain sensitive information, via|       a crafted TLS handshake, aka 
 the "CCS Injection" vulnerability.||     References:|       https://cve.mitre.org/
 cgi-bin/cvename.cgi?name=CVE-2014-0224|       http://www.openssl.org/news/
 secadv_20140605.txt|_      http://www.cvedetails.com/cve/2014-0224| 
 http-vuln-cve2011-3192:|   VULNERABLE:|   Apache byterange filter DoS|     State: 
 VULNERABLE|     IDs:  CVE:CVE-2011-3192  BID:49303|       The Apache web server 
 is vulnerable to a denial of service attack when numerous|       overlapping byte 
 ranges are requested.|     Disclosure date: 2011-08-19|     References:|       
 https://www.securityfocus.com/bid/49303|       https://www.tenable.com/plugins/
 nessus/55976|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-3192|
 _      https://seclists.org/fulldisclosure/2011/Aug/175| vulners:|   cpe:/
 a:igor_sysoev:nginx:1.15.7:|_     PRION:CVE-2018-16844 7.8 https://vulners.com/
 prion/PRION:CVE-2018-16844|_http-server-header: nginx/1.15.7|_http-csrf: Couldn't 
 find any CSRF vulnerabilities.|_http-dombased-xss: Couldn't find any DOM based 
 XSS.|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.| 
 ssl-heartbleed:|   VULNERABLE:|   The Heartbleed Bug is a serious vulnerability 
 in the popular OpenSSL cryptographic software library. It allows for stealing 
 information intended to be protected by SSL/TLS encryption.|     State: 
 VULNERABLE|     Risk factor: High|       OpenSSL versions 1.0.1 and 1.0.2-beta 
 releases (including 1.0.1f and 1.0.2-beta1) of OpenSSL are affected by the 
 Heartbleed bug. The bug allows for reading memory of systems protected by the 
 vulnerable OpenSSL versions and could allow for disclosure of otherwise encrypted 
 confidential information as well as the encryption keys themselves.||     
 References:|       http://www.openssl.org/news/secadv_20140407.txt|       https://
 cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-0160|_      http://cvedetails.com/
 cve/2014-0160/646/tcp filtered ldpService detection performed. Please report any 
 incorrect results at https://nmap.org/submit/ .Nmap done: 1 IP address (1 host 
 up) scanned in 151.60 seconds
```

So you will see alot of noice in the nmap scan but we will stick to the title and here we will use metasploit to exploit the vulnerablity.

<div style="text-align: center;">
  <img src="/assets/HeartBleed2.webp" alt="mannaully
" width="550">
</div>

We will use auxiliary/scanner/ssl/openssl_heartbleed.

Now to use the auxiliary just enter <use 2> it will be automatically selected.

Now firstly set these parameters.
RHOSTS [IP] Verbose True Set Action scan and then run the.

<div style="text-align: center;">
  <img src="/assets/HeartBleed3 .webp" alt="mannaully
" width="550">
</div>

If you read this carefullly you will see the flag.

Thank you for reading
