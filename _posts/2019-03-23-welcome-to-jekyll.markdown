---
layout: post
title:  "CRYPTO new"
date:   2019-08-07 07:00:33
categories: CTF Crypto
---
最近对CTF中的CRYPTO部分比较感兴趣，所以在这里记录下学习过程，主要题源是XCTF io。

这一部分主要是新手区的题。


#### 01 base64
题目上都给了base64，一看
```
Y3liZXJwZWFjZXtXZWxjb21lX3RvX25ld19Xb3JsZCF9
```
直接拿base64解码就是flag


#### 02 Caesar
就像题目说的，就是凯撒密码，顶多遍历26次，实际偏移是12

```
oknqdbqmoq{kag_tmhq_xqmdzqp_omqemd_qzodkbfuaz}

cyberpeace{you_have_learned_caesar_encryption}
```

#### 03 Morse
摩斯密码，需要转化一下，用‘/’分割开来，1是-，0是.

```
11 111 010 000 0 1010 111 100 0 00 000 000 111 00 10 1 0 010 0 000 1 00 10 110

--/---/.-./..././-.-./---/-.././../.../.../---/../-./-/./.-././.../-/../-./--.

MORSECODEISSOINTERESTING
```

PS:flag格式为cyberpeace{xxxxxxxxxx},均为小写


#### 04 Railfence



#### 05 easy_RSA
```
p=473398607161
q=4511491
e=17
```
直接给了p，q，e，数论里边直接代求解就可得到d，d就是flag

PS:flag格式为cyberpeace{xxxxxxxxxx},均为小写


#### 06 不仅仅是Morse

先摩斯解密
```
--/.-/-.--/..--.-/-..././..--.-/..../.-/...-/./..--.-/.-/-./---/-/...././.-./..--.-/-.././-.-./---/-.././..../..../..../..../.-/.-/.-/.-/.-/-.../.-/.-/-.../-.../-.../.-/.-/-.../-.../.-/.-/.-/.-/.-/.-/.-/.-/-.../.-/.-/-.../.-/-.../.-/.-/.-/.-/.-/.-/.-/-.../-.../.-/-.../.-/.-/.-/-.../-.../.-/.-/.-/-.../-.../.-/.-/-.../.-/.-/.-/.-/-.../.-/-.../.-/.-/-.../.-/.-/.-/-.../-.../.-/-.../.-/.-/.-/-.../.-/.-/.-/-.../.-/.-/-.../.-/-.../-.../.-/.-/-.../-.../-.../.-/-.../.-/.-/.-/-.../.-/-.../.-/-.../-.../.-/.-/.-/-.../-.../.-/-.../.-/.-/.-/-.../.-/.-/-.../.-/.-/-.../.-/.-/.-/.-/-.../-.../.-/-.../-.../.-/.-/-.../-.../.-/.-/-.../.-/.-/-.../.-/.-/.-/-.../.-/.-/-.../.-/.-/-.../.-/.-/-.../.-/-.../.-/.-/-.../-.../.-/-.../.-/.-/.-/.-/-.../-.../.-/-.../.-/.-/-.../-.../.-

MAY_BE_HAVE_ANOTHER_DECODEHHHHAAAAABAABBBAABBAAAAAAAABAABABAAAAAAABBABAAABBAAABBAABAAAABABAABAAABBABAAABAAABAABABBAABBBABAAABABABBAAABBABAAABAABAABAAAABBABBAABBAABAABAAABAABAABAABABAABBABAAAABBABAABBA
```
看到前面说可能是另一种编码，后面又都是A、B，所以有可能是培根加密，解密：

```
ATTACKANDDEFENCEWORLDISINTERESTING
attackanddefenceworldisinteresting
```
所以flag就是下面小写的字符串。

#### 07 混合编码

感觉有点想base64，base64解码试试：
```
JiM3NjsmIzEyMjsmIzY5OyYjMTIwOyYjNzk7JiM4MzsmIzU2OyYjMTIwOyYjNzc7JiM2ODsmIzY5OyYjMTE4OyYjNzc7JiM4NDsmIzY1OyYjNTI7JiM3NjsmIzEyMjsmIzEwNzsmIzUzOyYjNzY7JiMxMjI7JiM2OTsmIzEyMDsmIzc3OyYjODM7JiM1NjsmIzEyMDsmIzc3OyYjNjg7JiMxMDc7JiMxMTg7JiM3NzsmIzg0OyYjNjU7JiMxMjA7JiM3NjsmIzEyMjsmIzY5OyYjMTIwOyYjNzg7JiMxMDU7JiM1NjsmIzEyMDsmIzc3OyYjODQ7JiM2OTsmIzExODsmIzc5OyYjODQ7JiM5OTsmIzExODsmIzc3OyYjODQ7JiM2OTsmIzUwOyYjNzY7JiMxMjI7JiM2OTsmIzEyMDsmIzc4OyYjMTA1OyYjNTY7JiM1MzsmIzc4OyYjMTIxOyYjNTY7JiM1MzsmIzc5OyYjODM7JiM1NjsmIzEyMDsmIzc3OyYjNjg7JiM5OTsmIzExODsmIzc5OyYjODQ7JiM5OTsmIzExODsmIzc3OyYjODQ7JiM2OTsmIzExOTsmIzc2OyYjMTIyOyYjNjk7JiMxMTk7JiM3NzsmIzY3OyYjNTY7JiMxMjA7JiM3NzsmIzY4OyYjNjU7JiMxMTg7JiM3NzsmIzg0OyYjNjU7JiMxMjA7JiM3NjsmIzEyMjsmIzY5OyYjMTE5OyYjNzc7JiMxMDU7JiM1NjsmIzEyMDsmIzc3OyYjNjg7JiM2OTsmIzExODsmIzc3OyYjODQ7JiM2OTsmIzExOTsmIzc2OyYjMTIyOyYjMTA3OyYjNTM7JiM3NjsmIzEyMjsmIzY5OyYjMTE5OyYjNzc7JiM4MzsmIzU2OyYjMTIwOyYjNzc7JiM4NDsmIzEwNzsmIzExODsmIzc3OyYjODQ7JiM2OTsmIzEyMDsmIzc2OyYjMTIyOyYjNjk7JiMxMjA7JiM3ODsmIzY3OyYjNTY7JiMxMjA7JiM3NzsmIzY4OyYjMTAzOyYjMTE4OyYjNzc7JiM4NDsmIzY1OyYjMTE5Ow==

&#76;&#122;&#69;&#120;&#79;&#83;&#56;&#120;&#77;&#68;&#69;&#118;&#77;&#84;&#65;&#52;&#76;&#122;&#107;&#53;&#76;&#122;&#69;&#120;&#77;&#83;&#56;&#120;&#77;&#68;&#107;&#118;&#77;&#84;&#65;&#120;&#76;&#122;&#69;&#120;&#78;&#105;&#56;&#120;&#77;&#84;&#69;&#118;&#79;&#84;&#99;&#118;&#77;&#84;&#69;&#50;&#76;&#122;&#69;&#120;&#78;&#105;&#56;&#53;&#78;&#121;&#56;&#53;&#79;&#83;&#56;&#120;&#77;&#68;&#99;&#118;&#79;&#84;&#99;&#118;&#77;&#84;&#69;&#119;&#76;&#122;&#69;&#119;&#77;&#67;&#56;&#120;&#77;&#68;&#65;&#118;&#77;&#84;&#65;&#120;&#76;&#122;&#69;&#119;&#77;&#105;&#56;&#120;&#77;&#68;&#69;&#118;&#77;&#84;&#69;&#119;&#76;&#122;&#107;&#53;&#76;&#122;&#69;&#119;&#77;&#83;&#56;&#120;&#77;&#84;&#107;&#118;&#77;&#84;&#69;&#120;&#76;&#122;&#69;&#120;&#78;&#67;&#56;&#120;&#77;&#68;&#103;&#118;&#77;&#84;&#65;&#119;
```
后面就感觉是ASCII码了，48-57：0-9；65-90：A-Z；97-122：a-z

刚好都在这个区间范围内

#### 08 Normal_RSA

是一个文件夹，里面有.enc和.pem格式，直接带到CTF_RSA_tool里面跑，flag就可以出来.

[CTF_RSA_tool][link]

```
python solve.py --verbose -k examples/crypto7/pubkey.pem --decrypt examples/crypto7/flag.enc
```

#### 09 轮转机加密


#### 10 easychallenge
.pyc格式的，反编译一下得到py代码：

``` python
import base64

def encode1(ans):
    s = ''
    for i in ans:
        x = ord(i) ^ 36
        x = x + 25
        s += chr(x)
    
    return s


def encode2(ans):
    s = ''
    for i in ans:
        x = ord(i) + 36
        x = x ^ 36
        s += chr(x)
    
    return s


def encode3(ans):
    return base64.b32encode(ans)

flag = ' '
print 'Please Input your flag:'
flag = raw_input()
final = 'UC7KOWVXWVNKNIC2XCXKHKK2W5NLBKNOUOSK3LNNVWW3E==='
if encode3(encode2(encode1(flag))) == final:
    print 'correct'
else:
    print 'wrong'
```
把它所有的都反一下就可以了：

``` python
import base64

def encode1(ans):
    s = ''
    for i in ans:
        x = ord(i)-25
        x = x^36
        s+=chr(x)
    return s


def encode2(ans):
    s = ''
    for i in ans:
        x = ord(i)^36
        x = x - 36
        s += chr(x)
    return s


def encode3(ans):
    return base64.b32decode(ans)


flag = ' '
print 'Please Input your flag:'

final = 'UC7KOWVXWVNKNIC2XCXKHKK2W5NLBKNOUOSK3LNNVWW3E==='

final1 = encode3(final)
# print final1
print encode1(encode2(final1))

```
得到flag

#### 11 幂数加密

直接套用二进制加解密代码进行解密：
``` python
#! /usr/bin/env python
#coding=utf-8

a="8842101220480224404014224202480122"
a=a.split("0")
flag=''
for i in range(0,len(a)):
     str = a[i]
     list=[]
     sum=0
     for j in str:
        list.append(j)
        length = len(list)
     for k in range(0,length):
        sum+=int(list[k])
     flag+=chr(sum+64)
print flag

```

得到flag。

#### 12 easy_ECC

原来在Jarvis OJ平台上做过，直接粘代码：
``` python

```

[link]: https://github.com/3summer/CTF-RSA-tool
