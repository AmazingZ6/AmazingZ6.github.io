---
title: JAVAString类常用方法
date: 2019-09-18 08:53:20
tags:
---

# 1.创建新String
```javescript
String concat(String s);//返回一个新串，在原串后附加上s。
String replace(String old, String new);//返回一个新串，将原串中出现的old替换成new。
String substring(int start, int end);//返回一个新串，它是原串中从start到end的一部分。
String toLowerCase();//返回一个新串，它将原串中的大写字母变成小写。
String toUpperCase();//返回一个新串，它将原串中的小写字母变成大写。
```
# 2.查找方法
```javescript
boolean endsWith(String s);//如原串以s串为结尾，则返回true。
boolean startsWith(String s);//如原串以s串为开始，则返回true。
int indexOf(String s);//返回串中第一次出现s串的序号值。
int indexOf(String s, int offset);//返回串中从offset开始查找，第一次出现s串的序号值。
```
# 3.比较方法
```javescript
boolean equals(String s);//如果原串与s串相等，则返回true。
boolean equalsIgnoreCase(String s);//如果在忽略大小写的情况下，原串与s串相等，则返回true。
int  compareTo(String s);//进行字典序比较，如果原串小于s串则返回负数；如果原串大于s串则返回正数；如果原串等于s串则返回零。
```
# 4.其它方法
```javescript
str.split(",");//根据字符来拆分字符串，当我们需要以‘|’、‘：’、‘+’、‘.’、‘^’等特殊字符作为拆分条件的话，则需要加上 \\ 转义字符
charAt(int index)//返回index处的字符。
int length()//返回串的长度。
str.trim();//裁除首、尾空格符
str.contains("");//是否包含 ""
```



