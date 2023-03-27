---
title: Z字形变换
date: 2022-03-10 22:14:48
tags: LeetCode
---

# [6. Z 字形变换](https://leetcode-cn.com/problems/zigzag-conversion/)

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/zigzag-conversion

题目描述：

将一个给定字符串 s 根据给定的行数 numRows ，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "PAYPALISHIRING" 行数为 3 时，排列如下：

P   A   H   N
A P L S I I G
Y   I   R
之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："PAHNAPLSIIGYIR"。

请你实现这个将字符串进行指定行数变换的函数：

string convert(string s, int numRows);

示例 1：

输入：s = "PAYPALISHIRING", numRows = 3
输出："PAHNAPLSIIGYIR"
示例 2：
输入：s = "PAYPALISHIRING", numRows = 4
输出："PINALSIGYAHRPI"
解释：
P     I    N
A   L S  I G
Y A   H R
P     I
示例 3：

输入：s = "A", numRows = 1
输出："A"


提示：

1 <= s.length <= 1000
s 由英文字母（小写和大写）、',' 和 '.' 组成
1 <= numRows <= 1000



题解：我的想法是，既然最后是按行来读取，那么就可以依次获取每一行的数据放入结果中，那么就需要给每一个元素来一个编号，编号就代表着这个元素的行数，所以可以用一个和s一样长的数组来字母每个元素在那一行，而他们的行数是一串循环的数字，如当总共三行时，行数就依次为0，1，2，1，0，（从0开始），c++代码如下

```c++
class Solution {
public:
    string convert(string s, int numRows) {
        if(numRows == 1) return s;
        int len = s.length();
        int x = 0;
        int flag = 0;
        int p[len];
        string ans = "";
        for(int i = 0; i < len; i++){//这里构造行数数组
            if(flag == 0)
                p[i] = x++;
            else p[i] = x--;
            if(x == numRows - 1) flag = 1;
            else if(x == 0) flag = 0;
        }
        for(int k = 0; k < numRows; k++){
            for(int i = 0; i < len; i++){
                if(p[i] == k)
                    ans += s[i];
            }
        }
        return ans;
    }
};
```



