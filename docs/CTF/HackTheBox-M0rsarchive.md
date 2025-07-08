# HackTheBox M0rsarchive

<div style="text-align: center;">
  <img src="/assets/M0rsarchive1.webp" alt="mannaully
" width="550">
</div>
```
HTB-Challenges:- Mics  
Challenge Info:- Mics cipher based  
Challenge level:- Easy
```

This is one of the easiest challenges but the use of automation is shown well in this and how automation helps very effectively in CTF or Bug bounty hunting or any place it can be used.

In this case, the Challenge description mentions unzipping the archive several times.

But here I started digging in manually after I unzipped 2–3 files I realised that I’m currently at file 997  
basically, I had to open 997 more files then I started looking for scripts that could do it.

But firstly when you unzip the file you will find 2 files pwd.png and flag\_999.zip

<div style="text-align: center;">
  <img src="/assets/M0rsarchive2.webp" alt="mannaully
" width="550">
</div>

Now to unzip the flag\_999.zip you need to open the pwd.png image and crack the morse code And use that cracked code to unzip the file

Just for sake let me show how it will be done manually but we are not going to do it manually will automate the whole process so let’s have a look at how it is done.

We open the pwd.png file first

<div style="text-align: center;">
  <img src="/assets/M0rsarchive3.webp" alt="mannaully
" width="550">
</div>
Then used an online Morse code translator to decode the Cipher text

<div style="text-align: center;">
  <img src="/assets/M0rsarchive4.webp" alt="mannaully
" width="550">
</div>
This means the answer is 9 to unzip the file and we will be successful to unzip it

<div style="text-align: center;">
  <img src="/assets/M0rsarchive5.webp" alt="mannaully
" width="550">
</div>
Now the script we are going to use is going to take the image read the morse code from the PNG file unzip the file and continue this loop until we reach the last file


```python
import re  
import os  
import sys  
import zipfile  
from PIL import Image  
  
def get\_pass(morse\_list):  
```
This code is written by some Chinese hacker let’s understand the code and break it down a bit.

### Code analysis

Now this function what is basically does is, it decodes the Morse code after it has been extracted from the PNG file and returns the decoded value into an object called password


```python
def get\_pass(morse\_list):  
 password = ""  
 MORSE\_CODE\_DICT = {'.-': 'a', '-...': 'b', '-.-.': 'c', '-..': 'd','.': 'e', '..-.': 'f', '--.': 'g', '....': 'h','..': 'i', '.---': 'j', '-.-': 'k', '.-..': 'l','--': 'm', '-.': 'n', '---': 'o', '.--.': 'p','--.-': 'q', '.-.': 'r', '...': 's', '-': 't','..-': 'u', '...-': 'v', '.--': 'w', '-..-': 'x','-.--': 'y', '--..': 'z', '-----': '0', '.----': '1','..---': '2', '...--': '3', '....-': '4', '.....': '5','-....': '6', '--...': '7', '---..': '8', '----.': '9','-..-.': '/', '.-.-.-': '.', '-.--.-': ')', '..--..': '?','-.--.': '(', '-....-': '-', '--..--': ','}  
 for morse in morse\_list:  
 password += MORSE\_CODE\_DICT.get(morse)  
 return password
```
Now this function will read the Morse code from the PNG file or image and output into an object called output in the last line of the code you can see


```python
def get\_morse():  
 fp = open('./pwd.png', 'rb')  
 image = Image.open(fp)  
 pixel = list(image.getdata())  
 background = pixel[0]  
 chars = []  
 for i,v in enumerate(pixel):  
 if v == background:  
 chars.append(" ")  
 else:  
 chars.append("*")  
 output = "".join(chars)  
 """正则匹配测试建议：https://regex101.com/  
 ^ : asserts position at start of a line  
 $ : asserts position at the end of a line  
 \s : matches any whitespace character (equivalent to [\r\n\t\f\v ])  
 * : matches the previous token between zero and unlimited times, as many times as possible, giving back as needed (greedy)  
 \* : matches the character *  
 {3}: matches the previous token exactly 3 times  
 """  
 output = re.sub(r'^\s*', '', output) #匹配开头的任意个空白字符，并替换为空  
 output = re.sub(r'\s*$', '', output) #匹配结尾的任意个空白字符，并替换为空  
 output = re.sub(r'\*{3}', '-', output) #匹配3个*号，并替换为字符"-"  
 output = re.sub(r'\*', '.', output) #匹配单个*号，并替换为字符"."  
 output = re.sub(r'\s{2,}', ' | ', output) #(用于处理多行摩斯密码的情况)匹配两个以上空白字符，如果存在，就替换为"|"  
 output = re.sub(r'\s', '', output) #匹配空白字符，并替换为空  
 output = output.split('|')  
 fp.close()  
 return output
```
This i the last function which unzips the file using the decoded Morse code and the loop continues


```python
def unzip\_file(path, number, password):  
 zip\_path = "flag\_" + str(1000-number) + ".zip"  
 fp = zipfile.ZipFile(zip\_path)  
 for file in fp.namelist():  
 fp.extract(file,"./",pwd=password.encode("utf-8"))  
 fp.close()  
  
def main():  
 path = sys.path[0] #当前脚本的运行目录  
  
 for number in range(1,1001):  
 print("Processing the "+ str(number) + "th archive.")  
 #print(os.listdir('.')) #显示当前目录下的所有文件  
 morse\_list = get\_morse()  
 password = get\_pass(morse\_list)  
 unzip\_file(path, number, password)  
 path = "./flag"  
 os.chdir(path) #切换当前工作目录(进入flag子目录)  
  
 fp = open('./flag', 'r')  
 flag = fp.readlines()  
 print(flag)  
 fp.close()  
  
  
if \_\_name\_\_ == "\_\_main\_\_":  
 main()
```
Now let’s use this script to unzip the files

<div style="text-align: center;">
  <img src="/assets/M0rsarchive6.webp" alt="mannaully
" width="550">
</div>

<div style="text-align: center;">
  <img src="/assets/M0rsarchive7.webp" alt="mannaully
" width="550">
</div>

And we got the Flag

Thank you for reading