# HackTheBox Debugging Interface

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface1.webp" alt="mannaully
" width="600">
</div>

```
Challenge type:- Hardware
Challenge Info:- Embedded device Transmitted data decoding
Challenge level:- Easy
```

---
First of all, this is the first time I’m engaging in hardware hacking or anything related to hardware hacking this was hard for me to figure things out but I learned a lot about logic analysis and in general, i got introduced to hardware hacking.

let’s start by Downloading the files and unzipping them.

So as I unzipped the .zip file I found one file debugging_interface_singal.sal.

Again I looked on the internet about the file and it can be easily unzipped using the unzip command.

So I did and got 2 more files.

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface2.webp" alt="mannaully
" width="600">
</div>

```
meta.json and digital-0.bin
```

Again I looked at the internet for these (.bin) files in hardware and found out that I have to use a logic analyser to analyse this file and again i looked at internet to undestand what is this file and how basic analysis is done and finally got 2–3 tool but I used the SALEAE Logic Analyzer.

https://www.saleae.com/downloads/

[https://www.saleae.com/downloads/](https://www.saleae.com/downloads/)

To analyse it also i had to look a lot into the documentation to understand and analyse every step was different and difficult to understand but i managed to get it.

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface3.webp" alt="mannaully
" width="600">
</div>

I opened the .sal file and by using + magnify in and analyze.

Now I analyzed the the patterns of the wave signal and found out that there is a repetitionin between-the-lines waves and it was different.

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface4.webp" alt="mannaully
" width="600">
</div>

And in async serial changed the bit rate(Bits/s) to 31230.

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface5.webp" alt="mannaully
" width="600">
</div>

And put data to command line.

<div style="text-align: center;">
  <img src="/assets/Debugging_Interface6.webp" alt="mannaully
" width="600">
</div>

And there we go the flag.

Thank you for reading


