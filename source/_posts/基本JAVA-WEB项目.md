---
title: 基本JAVA_WEB项目
date: 2020-07-29 15:42:33
tags:

---
# Javaweb实训学习

由于疫情原因只能呆在家，但也阻止不了学校的实习呀，本次实习采用网上教学的方式,老师讲的东西有点多，在这里总结一下。

## 1，准备工作

安装好JDK,Mysql,eclipse或idea,navicat,tomcat（最基础的版本，没有用到框架）

## 2,大致流程

1,需求分析

对你的目标项目做一个大致分析，找出需要可能需要实现的功能。		

2,页面设计

设计出最终项目的所有静态页面，在实际项目中一般用于做展示。

3，数据库设计

根据你要实现的功能设计出对应的数据库表结构

4，实际代码编写

将代码部署到tomcat上，在本地进行查看与调试

## 3，详细流程（以KFC网页端点餐为例）

1，需求分析

要点餐，首先要登陆，然后要将要点的东西加入购物车，最后进行结算。

想要快速的找到商品，分类与搜索是必须要的，同时需要能够查看到商品详情。

对于购物车中的货物可以经行勾选，勾中才会结算，同时在购物车页面实现商品数量的加减

对于之前的订单可以在历史订单中找到，在历史订单详情页中找到自己之前买了啥

2，页面设计

包含登陆页面，主页面，商品页，商品详情页，购物车页面，历史订单页，订单详情页

在设计这些页面时会用到jstl以及er表达式，需要添加依赖包以及在jsp文件开始加上一段说明

3，数据库设计

要能登陆，需要user表经行登陆判断

显示商品，需要一个food表，以及foodtype商品分类表

显示订单需要order表，以及orderdetail订单详情表

这里在实际中对于外键并没有直接设置，而是在创建一个键，用0，1表示这个数据是否存在，便于数据的删除，但在这里为了简便，没有经行类似的设置。

4，实际代码编写

在eclipse创建一个JAVA项目

首先是与数据库建立连接,即JDBC,需要提前导入JDBC对应的的依赖包，在properties中配置好信息后，创建一个工具类来封装JDBC的方法来建立连接，然后创建实体层entity来与数据库中的表相对应，DAO层写入对应的方法（这里的方法只能是直接用sql语句就能完成的方法），然后在DAOImpl中实现这些方法，正常流程是再创建service层来封装更高级的方法，由于这个项目的方法需求比较简单，所以直接调用DAO层方法来实现就行。在conroller层中编写servlet与用户的需求经行对接，正常时是调用service层方法，这里为了简单直接调用DAO层方法。

![xxx](1.PNG)

[代码下载](https://pan.baidu.com/s/1Oa_UYstTzfb2cQwVSRa_Og) 提取码adsi

我的个人博客 amazingz6.github.io
我的bilibili https://space.bilibili.com/66908429
我的CSDN https://blog.csdn.net/qq_44105654
我的简书 https://www.jianshu.com/u/607ef08e5825
我的github https://github.com/AmazingZ6?tab=repositories