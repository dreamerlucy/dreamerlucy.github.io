---
layout: post
title:  "CRYPTO new"
date:   2019-08-07 07:00:33
categories: Javascript NodeJS
---
最近对CTF中的CRYPTO部分比较感兴趣，所以在这里记录下学习过程，主要题源是XCTF io。
这一部分主要是新手区的题。


#### 01 base64
题目上都给了base64，一看
```
Y3liZXJwZWFjZXtXZWxjb21lX3RvX25ld19Xb3JsZCF9
```
直接拿base64解码就是flag

#### 05 easy_RSA
```
p=473398607161
q=4511491
e=17
```
直接给了p，q，e，数论里边直接代求解就可得到d，d就是flag
PS:flag格式为cyberpeace{xxxxxxxxxx},均为小写

#### 08 Normal_RSA

是一个文件夹，里面有.enc和.pem格式，直接带到CTF_RSA_Tool里面跑，flag就可以出来.

```
python solve.py --verbose -k examples/crypto7/pubkey.pem --decrypt examples/crypto7/flag.enc
```




```C++
#include <stdio.h>
int main(int argc, char const *argv[])
{
	printf("Hello the World!!!\n");
	return 0;
}
```

这是我的[GitHub][link]，啊哈哈哈哈哈~~~

[link]: https://github.com
