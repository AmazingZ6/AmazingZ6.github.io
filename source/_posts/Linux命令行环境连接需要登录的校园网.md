---
title: Linux命令行环境连接需要登录的校园网
date: 2023-03-06 09:48:28
tags: linux
---
# Linux命令行环境连接需要登录的校园网

本方法适用于未安装图形化界面的linux环境连接采用802.1x认证的网络。

使用nmcli命令不能直接连接需要认证的wifi，无论是需要网页登录的，还是802.1x这种需要登录验证的。但是可以通过以下方法连接。

首先需要创建一个指定这个wifi的connection，然后再对connection进行设置，具体设置如下：

CONNECTION_NAME可以自己定义，SSID是你wifi的名称。

```
# nmcli con add type wifi ifname wlan0 con-name CONNECTION_NAME ssid SSID
# nmcli con edit id CONNECTION_NAME
nmcli> set wifi-sec.key-mgmt wpa-eap  //设置安全类型，“wpa-eap”为WPA2企业
nmcli> set ipv4.method auto    
nmcli> set 802-1x.eap peap            //设置认证方式，PEAP版本为“自动”
nmcli> set 802-1x.phase2-auth mschapv2 //设置内部认证
nmcli> set 802-1x.identity USERNAME
nmcli> set 802-1x.password PASSWORD
nmcli> save
nmcli> activate
```

以上设置适用于ECUST校园网，其他网络可能需要根据实际情况进行设置更改。
