---
title: 网络分层
tags:
  - 面试题
  - 网络
  - TCP
categories:
  - 计算机网络
date: 2020-06-20 15:34:22
---

本文简单介绍一下两种分层模型：OSI网络分层和TCP/IP网络分层。

### OSI模型
> OSI模型一共分为七层，由上至下分别是：
+ 应用层
+ 表达层
+ 会话层
+ 传输层
+ 网络层
+ 数据链路层
+ 物理层
<!--more-->

#### 应用层(Application)
        应用层的协议一般有：HTTP、FTP、DNS等，这一层是最接近用户的一层。

#### 表达层(Presentation)
        该层的主要功能：转换，压缩和加密，常见的加密协议为SSL。

#### 会话层(Session)
        我们可以把会话层理解为两个应用进程之间的逻辑连接，同时会话层还负责了管理和确定传输模式
        计算机传输数据有三种模式：单向、半双工、全双工

#### 传输层(Transport)
        传输层就是表面意思传输了，端到端，主机到主机的传输
        这一层最主要的就是TCP、UDP啦，包括三次握手、四次挥手是必须要会的

#### 网络层(Network)
        网络层需要提供三个最基本的功能：地址、路由、分段和重组
        网络层上最重要的协议IP（Internet Protocol），就是为了这些功能而设计的。目前有IPv4和IPv6两个版本。

#### 数据链路层(Data Link)
        数据链路层又分为两个子层：逻辑链路控制层(Logical Link Control)和介质访问控制层(Media Access Control)
        数据链路层就是关心如何把数据从一个设备发送到另一个设备

#### 物理层(Physical)
        物理层位于OSI的底层，所有其他层的数据最终都必须经由物理层才能发送出去。

-------------

### TCP/IP模型
        TCP/IP模型分为四层：应用层（Application）、传输层（Host-to-Host Transport）、互联网层(Internet)、网络接口层(Network Interface)。

在TCP/IP模型中并不包含物理层。另外，两个重要的协议ARP（Address Resolution Protocol，地址解析协议）和RARP（Reverse Address Resolution Protocol，反向地址转换协议），在OSI模型中一般被认为是在位于第二层数据链路层和第三层网络层之间，而在TCP/IP模型中则位于网络接口层。(此段转载自掘金：https://juejin.im/post/5a98e1f7f265da237410694e 作者：MinGRn）
