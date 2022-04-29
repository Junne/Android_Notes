##### Computer Network

---



###### 基础知识储备:

* [计算机网络基础知识总结](https://www.runoob.com/w3cnote/summary-of-network.html) 
* [万字45张图详解计算机网络基础知识](https://www.eet-china.com/mp/a50982.html) 
* [OSI7层模型和TCP/IP4层模型](https://zhuanlan.zhihu.com/p/32059190) 
* [TCP/IP协议总结](https://zhuanlan.zhihu.com/p/303430856) 
* [IP地址](https://zh.wikipedia.org/wiki/IP地址) 
* [关于TCP三次握手和四次挥手](https://segmentfault.com/a/1190000039165592) 



###### 重点知识:

* 计算机网络分层

  * ISO(估计标准化组织)制定的OSI(Open System Interconnect)模型，将网络分为七层。

    ![OSI七层模型](https://github.com/Junne/Android_Notes/blob/master/notes/Images/OSI-TCP-IP.png) 

    ![7LayerProtocol](https://github.com/Junne/Android_Notes/blob/master/notes/Images/7LayerProtocol.png) 

    

  * TCP/IP四层模型

    - 应用层：负责各种不同应用之间的协议，如浏览器的**HTTP协议**、电子邮件的**STMP协议**等。
    - 传输层：负责**可靠传输**的**TCP协议**、**高效传输**的**UDP协议**
    - 网络层：负责寻址（准确找到对方设备）的**IP协议**
    - 数据链路层：负责将数字信号在物理通道（网线）中准确传输

  * 五层模型

* TCP的三次握手和四次挥手:

  * 三次握手

    ![TCP三次握手](https://github.com/Junne/Android_Notes/blob/master/notes/Images/TCP三次握手.webp)

  * 四次挥手

    ![TCP四次挥手](https://github.com/Junne/Android_Notes/blob/master/notes/Images/TCP四次挥手.webp) 

  

* IP地址

  * IPv6 从IPv4到IPv6最显著的变化就是网络地址的长度。RFC 2373和RFC 2374定义的IP地址，就像下面章节所描述的，有128位长；IP地址的表达形式，一般采用32个十六进制数。

    IP中可能的地址有2128≈3.4×1038个，具体数量为340,282,366,920,938,463,463,374,607,431,768,211,456（即1632)，因为32位地址每位可以取16个不同的值。 在很多场合，IP地址由两个逻辑部分组成：一个64位的网络前缀和一个64位的主机地址，主机地址通常根据物理地址自动生成，叫做EUI-64（或者64-位扩展唯一标识）。

  * IPv4有五类网址，A、B、C、D、E类:

    |                                  |         **A类IPv4地址**         |      **B类IPv4地址**      |      **C类IPv4地址**      |                 **D类IPv4地址**                 | **E类IPv4地址**                          |
    | :------------------------------: | :-----------------------------: | :-----------------------: | :-----------------------: | :---------------------------------------------: | ---------------------------------------- |
    |          **网络标志位**          |                0                |            10             |            110            |                      1110                       | 11110                                    |
    |          **IP地址范围**          |     0.0.0.0~127.255.255.255     | 128.0.0.0~191.255.255.255 | 192.0.0.0~223.255.255.255 |            224.0.0.0~239.255.255.255            | 240.0.0.0~247.255.255.255                |
    |        **可用IP地址范围**        |     1.0.0.1~127.255.255.254     | 128.0.0.1~191.255.255.254 | 192.0.0.1~223.255.255.254 |                                                 |                                          |
    |    **是否可以分配给主机使用**    |               是                |            是             |            是             |                       否                        | 否                                       |
    |        **网络数量（个）**        |           126 (27-2)            |        16384 (214)        |       2097152 (221)       |                       ---                       | ---                                      |
    | **每个网络中可容纳主机数（个）** |        16777214 (224-2)         |       65534 (216-2)       |        254 (28-2)         |                       ---                       | ---                                      |
    |           **适用范围**           |       大量主机的大型网络        |   中等规模主机数的网络    |        小型局域网         | 留给Internet体系结构委员会(IAB)使用【组播地址】 | 保留，仅作为搜索、Internet的实验和开发用 |
    |               备注               | 0.0.0.0为特殊地址，表示本网主机 |                           |                           |                                                 | 255.255.255.255为特殊地址，用于定向广播  |

* DNS(域名系统Domain name system)

* CDN(Content Delivery Network)

* HTTP协议

  * [网络基础知识之HTTP协议](https://zhuanlan.zhihu.com/p/24913080) 

  * [一个完整的HTTP请求过程](https://zhuanlan.zhihu.com/p/37436528)   [HTTP完成请求过程](https://www.cnblogs.com/guobm/p/9739704.html) 

  * 协议内容

  * HTTP请求过程图解

    ![HTTP请求过程](/Users/mac/Documents/Study/MyGitHub/Android_Notes/notes/Images/HTTP请求过程.png) 

* HTTPS协议

  * [HTTP和HTTPS协议，看一篇就够了](https://blog.csdn.net/xiaoming100001/article/details/81109617) 

  * [HTTPS详解](https://segmentfault.com/a/1190000021494676) 

  * [SSL/TLS工作原理和详细握手过程](https://segmentfault.com/a/1190000021559557?_ea=29659396) 

  * HTTPS加密解密验证及 数据传输过程:

    ![HTTPS加密解密验证及 数据传输过程](/Users/mac/Documents/Study/MyGitHub/Android_Notes/notes/Images/HTTPS加密解密验证及 数据传输过程.webp) 

    

* ARP协议

* UDP协议

