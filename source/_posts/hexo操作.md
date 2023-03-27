---
title: hexo操作
date: 2020-12-11 09:50:28
tags:
---

## 怕自己忘了，所以在这里写一下OVO

新建blog
```javascript
hexo new "博客名"
```
启动本地服务
```javascript
hexo server //可以简写成hexo s
```
遇到问题就用以下三步
```javascript
hexo clean //清除部署緩存,可以简写成hexo c
hexo generate //生成静态页面至public目录,可以简写成hexo g
hexo deploy //将.deploy目录部署到GitHub,可以简写成hexo d
```