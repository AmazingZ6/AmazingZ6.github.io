---
title: LeetCode 字符串转换整数 (atoi)
date: 2020-05-05 13:45:55
tags: LeetCode
---

# LeetCode 字符串转换整数 (atoi)

## 题目描述

请你来实现一个 `atoi` 函数，使其能将字符串转换成整数。

首先，该函数会根据需要丢弃无用的开头空格字符，直到寻找到第一个非空格的字符为止。接下来的转化规则如下：

- 如果第一个非空字符为正或者负号时，则将该符号与之后面尽可能多的连续数字字符组合起来，形成一个有符号整数。
- 假如第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成一个整数。
- 该字符串在有效的整数部分之后也可能会存在多余的字符，那么这些字符可以被忽略，它们对函数不应该造成影响。

注意：假如该字符串中的第一个非空格字符不是一个有效整数字符、字符串为空或字符串仅包含空白字符时，则你的函数不需要进行转换，即无法进行有效转换。

在任何情况下，若函数不能进行有效的转换时，请返回 0 。

**提示：**

- 本题中的空白字符只包括空格字符 `' '` 。
- 假设我们的环境只能存储 32 位大小的有符号整数，那么其数值范围为 [−231, 231 − 1]。如果数值超过这个范围，请返回  INT_MAX (231 − 1) 或 INT_MIN (−231) 。

**示例 1:**

```
输入: "42"
输出: 42
```

**示例 2:**

```
输入: "   -42"
输出: -42
解释: 第一个非空白字符为 '-', 它是一个负号。
     我们尽可能将负号与后面所有连续出现的数字组合起来，最后得到 -42 。
```

**示例 3:**

```
输入: "4193 with words"
输出: 4193
解释: 转换截止于数字 '3' ，因为它的下一个字符不为数字。
```

**示例 4:**

```
输入: "words and 987"
输出: 0
解释: 第一个非空字符是 'w', 但它不是数字或正、负号。
     因此无法执行有效的转换。
```

**示例 5:**

```
输入: "-91283472332"
输出: -2147483648
解释: 数字 "-91283472332" 超过 32 位有符号整数范围。 
     因此返回 INT_MIN (−231) 。
```



其实这个就是官方题解，我觉得很巧妙，所以来分享一下

他采用了自动机的方法（本人刚好在学编译原理哈哈哈），将所有的状态分为四类 start(起始状态)，signed（'+'或'-'号）,number(数字)，end(结束状态)

具体的状态之间的转换如下表

|               | ' '   | +/-    | number    | other |
| ------------- | ----- | ------ | --------- | ----- |
| **start**     | start | signed | in_number | end   |
| **signed**    | end   | end    | in_number | end   |
| **in_number** | end   | end    | in_number | end   |
| **end**       | end   | end    | end       | end   |





```c++
class Automaton {
    string state = "start";
    unordered_map<string, vector<string>> table = {//状态转换表，与上表对应
        {"start", {"start", "signed", "in_number", "end"}},
        {"signed", {"end", "end", "in_number", "end"}},
        {"in_number", {"end", "end", "in_number", "end"}},
        {"end", {"end", "end", "end", "end"}}
    };
    int getchar(char c){//与上面的无向图对应，决定了无向图二维下标
        if(isspace(c)) return 0;//为空格
        if(c == '+' or c == '-') return 1;//为 '+','-'
        if(isdigit(c)) return 2;//为数字
        return  3;//为其他
    }
public:
    int sign = 1;//初始为1，因为当没有'+','-'号时默认是正数
    long long ans = 0;
    void getc(char c){
        state = table[state][getchar(c)];//找到对应的下一个状态
        if(state == "in_number"){//判断如果是数字，就将当前数字加入结果中
            ans = ans * 10 + c - '0';
            ans = sign == 1 ? min((long long)INT_MAX, ans) : min(-(long long)INT_MIN, ans);//判断是否超出范围是正数则与INT_MAX比较，负数则与INT_MIN比较
        }
        if(state == "signed"){//如果当前是'+'或'-'
            if(c == '+') sign = 1; //1表示正数
            else sign = -1;//-1表示负数
        }//其他情况不用写出来，因为到了end状态后就只可能到达end状态，不会到达任何有用的状态，或者说除了上面两个状态之外的状态不需要做任何的操作
    }
    
};

class Solution {
public:
    int myAtoi(string str) {
        Automaton automaton;
        for(char c:str)
            automaton.getc(c);
        return automaton.sign * automaton.ans;//与符号位相乘，决定他的正负
    }
};
```



转载自[leetcode](leetcode%C2%A0https://leetcode-cn.com/problems/string-to-integer-atoi/solution/zi-fu-chuan-zhuan-huan-zheng-shu-atoi-by-leetcode-/%C2%A0leetcode)

我的个人博客 amazingz6.github.io
我的bilibili https://space.bilibili.com/66908429
我的CSDN https://blog.csdn.net/qq_44105654
我的简书 https://www.jianshu.com/u/607ef08e5825
我的github https://github.com/AmazingZ6?tab=repositories