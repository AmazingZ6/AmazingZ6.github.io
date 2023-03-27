---
title: N皇后
date: 2020-06-12 20:40:9
tags: LeetCode
---

# 51. N 皇后

难度困难1219

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n×n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回所有不同的 **n 皇后问题** 的解决方案。

每一种解法包含一个不同的 **n 皇后问题** 的棋子放置方案，该方案中 `'Q'` 和 `'.'` 分别代表了皇后和空位。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

```
输入：n = 4
输出：[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

**示例 2：**

```
输入：n = 1
输出：[["Q"]]
```

**提示：**

- `1 <= n <= 9`

来源:leetcode

[51. N 皇后 - 力扣（LeetCode） (leetcode-cn.com)](https://leetcode-cn.com/problems/n-queens/)

思路：之前写过n皇后，不过是只用算出有多少种情况，这题是要把棋盘给画出来，不过大差不差。大致思路还是dfs加回溯，在递归的时候检查当前位置的正上方有没有皇后（这里是从上到下一行一行来所以不用考虑下方），左上方一条线有没有皇后，右上方一条线有没有皇后，没有就可以进入下一层递归。

c++代码：

```c++
class Solution {
public:
    vector<vector<string>> ans;
    vector<string> temp;
    int size;

    void dfs(int n){
        if(n == size){
            ans.push_back(temp);
            return;
        }
        for(int i = 0; i < size; i++){
            string s;
            int flag = 0;
            for(int j = 0; j < n; j++){
                if(temp[j].at(i) == 'Q'){//当前位置上方
                    flag = 1;
                    break;
                }    
                if(i + n - j < size){
                    if(temp[j].at(i + n - j) == 'Q'){//当前位置右上方
                        flag = 1;
                        break;
                    }
                }
                if(i - n + j >= 0){
                    if(temp[j].at(i - n + j) == 'Q'){//当前位置左上方
                        flag = 1;
                        break;
                    }
                }
            }
            if(flag) continue;
            for(int j = 0; j < i; j++) s += ".";
            s += "Q";
            for(int j = i + 1; j < size; j++) s += ".";
            temp.push_back(s);
            dfs(n + 1);
            temp.pop_back();//回溯
        }
    }


    vector<vector<string>> solveNQueens(int n) {
        size = n;
        dfs(0);
        return ans;
    }
};
```



