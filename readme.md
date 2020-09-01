# 01 -  信息收集
## 存活主机识别
### arping
### fping

Fping类似于ping，但比ping强大。Fping与ping不同的地方在于，fping可以在命令行中指定要ping的主机数量范围，也可以指定含有要ping的主机列表文件。

目标IP地址的输入方式：

fping IP1 IP2 IP3 ...；

fping -f filename；

fping -g IP1 IP2（IP1地址开始范围，IP2地址结束范围）；
