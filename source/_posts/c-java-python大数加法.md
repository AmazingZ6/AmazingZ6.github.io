---
title: c++ java python大数加法
date: 2019-07-30 17:39:01
tags: 算法
toc: true
---


转自：https://blog.csdn.net/weixin_43871885/article/details/97797871 
### c++代码
```javascript
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
#define MAXN 1000
int a[MAXN],b[MAXN];
int main(int argc, const char * argv[])
{
    string str1,str2;//保存输入
    long int len1,len2;
    long int i,j,k;
    int up;

    /*输入流程*/
    cin>>str1>>str2;

    /*初始化各量*/
    len1 = str1.length();
    len2 = str2.length();
    memset(a, 0, sizeof(a));
    memset(b, 0, sizeof(b));

    /*注意，必须倒着保存数据*/
    for (i = len1 - 1, k = 0; i != -1; -- i)
    {
        a[k] = str1[i] - '0';
        k++;
    }
    for (j = len2 - 1, k = 0; j != -1; -- j)
    {
        b[k] = str2[j] - '0';
        k++;
    }
    for (i = 0, up = 0; i < MAXN; ++ i)
    {
        a[i] = a[i] + b[i] + up;
        up = a[i] / 10;
        a[i] %= 10;
    }
    for (i = MAXN - 1; i != -1; -- i)
    {
        if (a[i])
        {
            break;
        }
    }
    for (k = i; k != -1; --k)
    {
        cout<<a[k];
    }
    return 0;
}
```
<!-- more --> 




### java代码
```javascript
package my;
import java.math.BigInteger;
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        BigInteger a, b;
        Scanner in = new Scanner(System.in);
            a = in.nextBigInteger();
            b = in.nextBigInteger();
            System.out.println(a + " + " + b + " = " + a.add(b) );
            System.out.println();
    }
} 
```


### Python大数代码
```javascript
a = int(input());b = int(input());print(a+b);
```

我的个人博客 amazingz6.github.io
我的CSDN https://blog.csdn.net/qq_44105654
我的简书 https://www.jianshu.com/u/607ef08e5825
我的github https://github.com/AmazingZ6?tab=repositories
我的bilibili https://space.bilibili.com/66908429