---
title: JAVA基础知识
date: 2019-09-17 10:56:16
tags: JAVA基础知识
---
本人刚学JAVA，写个博客来给自己巩固一下基本知识 (=・ω・=)


# 1.JAVA数据输出格式的控制
```javascript
 String.format.("格式串"，数值数据）//方法一
 System.out.print("格式串"，数值数据) //方法二
```
# 2.用float时数后要加F
```javascript
float a=3.4F;
```
# 3.数字不能自动转化为Boolean
# 4.字符检测的方法
```javascript
char ch='a';
Character.isLetter(ch) -- ch是否是字母
Character.isDigit(ch)  -- ch是否是数字
Character.isLetterOrDigit(ch) -- ch是否是字母或数字
Character.isWhitespace(ch) -- ch是否是空格
Character.isLowerCase(ch) -- ch是否是小写字母
Character.isUpperCase(ch) -- ch是否是大写字母
```
# 5.自定义符号常量加final
```javascript
final double PI=3.14159;
```
# 6.在方法外定义的变量会自动初始化
# 7.String加其他类型变量时会将其他类型转化为字符类型
# 8.字符串转数值
方法1：
```javascript
 int i = Integer.parseInt("123");       (常用)
 double d = Double.parseDouble("1.23");
```
方法2：
```javascript
 int i =Integer.valueOf("123").intValue(); 
```
# 9.数值转字符串
 方法1： 
 ```javascript
 String s=String.valueOf(value); 
 ```
 其中value为任一种数字类型。

方法2：
```javascript
 String s = Integer.toString(123);
```
方法3：最直接
```javascript
String s = "" + value;  其中value为任意一种数字类型。
```
 # 10.字符数组转字符串
 ```javascript
 char[ ] c={'a','b','c'};
String str=new String(c);
 ```
 # 11.字符串转字符数组  
```javascript
String str="abc";
char[ ]  c=str.toCharArray(); 
```
 # 12."=="和equals的区别
```javascript
String s1="abc";  //方法以
String s2="abc";
String s3=new String("abc"); //方法二
String s4=new String("abc");
System.out.println(s1==s2); 
System.out.println(s1.equals(s2));
System.out.println(s3==s4);
System.out.println(s3.equals(s4));            
```
得到的结果为true,true,false,true.
方法一属于常量式创建，会存放一个在一个叫String pool 的地方，再次创建时会直接引用存在的相同变量
而方法二属于对象式创建，是运行时在Heap内存里面创建对象，每new一次都一定会创建对象
而“==”是比较两者的地址是否一样，所以第三个为false
equals是比较变量是否一样。
# 13.%也能用于浮点型变量
# 14.类型转换
当没有信息丢失时，变量可被自动升级为一个较长的形式（如：int至long的升级）
```javascript
long bigval = 6;  // 6 is an int type, OK
int smallval = 99L;  // 99L is a long, error 
double z = 12.414F;  // 12.414F is float, OK
float z1 = 12.414;  // 12.414 is double, error
//但升级也可能会导致出错
short  a，b，c
a=1；b=2；c= a+b；//上述程序会因为在操作short之前提升每个short至int而出错。
//然而，如果c被声明为一个int，或按如下操作进行类型转换：
c = (short)(a+b);//则上述代码将会成功通过
```
我的个人博客 amazingz6.github.io
我的CSDN https://blog.csdn.net/qq_44105654
我的简书 https://www.jianshu.com/u/607ef08e5825
我的github https://github.com/AmazingZ6?tab=repositories
我的bilibili https://space.bilibili.com/66908429







 


 	









 


 	

