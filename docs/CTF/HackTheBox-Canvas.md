# HackTheBox Canvas

<div style="text-align: center;">
  <img src="/assets/Canvas1.webp" alt="mannaully
" width="600">
</div>
```
HTB-Challenges:- Mics  
Challenge Info:- Mics encryption based  
Challenge level:- Easy
```

---
The lab is simple and doesn't require much efforts but i did the lab it is becoz you can earn points so i did the lab.

downloaded the zip file and unzipped.

there were 4 files.

<div style="text-align: center;">
  <img src="/assets/Canvas2.webp" alt="mannaully
" width="550">
</div>
I opend index.html but found nothing.

Just a simple login page when i enter admin:admin it gave a mock flag.

<div style="text-align: center;">
  <img src="/assets/Canvas3.webp" alt="mannaully
" width="550">
</div>

<div style="text-align: center;">
  <img src="/assets/Canvas4.webp" alt="mannaully
" width="550">
</div>
I looked around and in /js found login.js and opend it.

<div style="text-align: center;">
  <img src="/assets/Canvas5.webp" alt="mannaully
" width="550">
</div>
So if you didn’t get it yet we need to Obfuscate js.

![](https://cdn-images-1.medium.com/max/800/1*YKnZyPm86n7556LlDvA2pg.png)
<div style="text-align: center;">
  <img src="/assets/Canvas6.webp" alt="mannaully
" width="550">
</div>
Now analyzing javascript code we understond how the code work  
also found it stores the result in ASCII.

now we just need to decode ASCII code to get to the flag.

![](https://cdn-images-1.medium.com/max/800/1*CPs1erNINMiBHAvF19vJmQ.png)
<div style="text-align: center;">
  <img src="/assets/Canvas7.webp" alt="mannaully
" width="550">
</div>

Thank you for reading
