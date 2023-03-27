---
title: LeetCode 课程表 II
date: 2020-03-23 13:32:51
tags:
---

**名称：210. 课程表 II**

**题目描述：**
现在你总共有 n 门课需要选，记为 0 到 n-1。

在选修某些课程之前需要一些先修课程。 例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们: [0,1]

给定课程总量以及它们的先决条件，返回你为了学完所有课程所安排的学习顺序。

可能会有多个正确的顺序，你只要返回一种就可以了。如果不可能完成所有课程，返回一个空数组。

示例 1:
```
输入: 2, [[1,0]] 
输出: [0,1]
解释: 总共有 2 门课程。要学习课程 1，你需要先完成课程 0。因此，正确的课程顺序为 [0,1] 。
```
示例 2:
```
输入: 4, [[1,0],[2,0],[3,1],[3,2]]
输出: [0,1,2,3] or [0,2,1,3]
解释: 总共有 4 门课程。要学习课程 3，你应该先完成课程 1 和课程 2。并且课程 1 和课程 2 都应该排在课程 0 之后。
     因此，一个正确的课程顺序是 [0,1,2,3] 。另一个正确的排序是 [0,2,1,3] 。
```

解题思路：首先是要判断是否可以完成全部的课程，很明显，我们应该用拓扑排序来做，那么数据结构我们就应该采用图（用map来存），再加上一个简单的bfs即可解出此题。
c++代码
```javescript
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<int> result;
        vector<int> fake;
        vector<int> degree(numCourses , 0);
        unordered_map<int, vector<int>> map;
        for(vector<int> prerequisite : prerequisites) {
            map[prerequisite[1]].push_back(prerequisite[0]);
            degree[prerequisite[0]]++;
        }
        queue<int> q;//用来做拓扑排序的队列
        for(int i = 0; i < numCourses ; i++){
            if(degree[i] == 0){
                q.push(i);
            }
        }
        while(!q.empty()){
            int cur = q.front();
            result.push_back(cur);//把每次的结果存起来，最终得到的就是顺序
            q.pop();
            for(int next : map[cur]){
                degree[next]--;
                if(degree[next] == 0)
                    q.push(next);
            }
        }
        return result.size() == numCourses ? result : fake;//fake是一个空的数组，如果找不到就输出空数组
    }
};
```

我的个人博客 amazingz6.github.io
我的bilibili https://space.bilibili.com/66908429
我的CSDN https://blog.csdn.net/qq_44105654
我的简书 https://www.jianshu.com/u/607ef08e5825
我的github https://github.com/AmazingZ6?tab=repositories