物理层、应用、

网络七层协议：应用层、表示层、会话层、传输层、网络层、数据链路层、物理层

**开放式系统互联通信参考模型**（英语：Open System Interconnection Reference Model，缩写为 OSI），简称为**OSI模型**（OSI model），一种[概念模型](https://baike.baidu.com/item/概念模型/3187025)，由[国际标准化组织](https://baike.baidu.com/item/国际标准化组织/779832)提出，一个试图使各种计算机在世界范围内互连为网络的标准框架

**TCP/IP（Transmission Control Protocol/Internet Protocol，传输控制协议/网际协议）**是指能够在多个不同网络间实现信息传输的协议簇。TCP/IP协议不仅仅指的是[TCP](https://baike.baidu.com/item/TCP/33012) 和[IP](https://baike.baidu.com/item/IP/224599)两个协议，而是指一个由[FTP](https://baike.baidu.com/item/FTP/13839)、[SMTP](https://baike.baidu.com/item/SMTP/175887)、TCP、[UDP](https://baike.baidu.com/item/UDP/571511)、IP等协议构成的协议簇， 只是因为在TCP/IP协议中TCP协议和IP协议最具代表性，所以被称为TCP/IP协议

![image-20220127223017075](.\assets\image-20220127223017075.png)

# 协议

 对等层的实体有一个规则集合作为通讯协议，因此复杂且不同的端可以通讯

**协议分层次：**应用层、传输层、网络层、网络接口层

- **应用层**：HTTP
- **网络层**：IP
- **传输层**：TCP、UDP等

![image-20220127230659441](.\assets\image-20220127230659441.png)

**一个协议需要包括的内容**：语法、语义、时序、动作

**服务器是什么**

- 应用层协议等级以下的应用实体

- 为分布式应用提供通讯服务的基础设施

**接入链路和骨干链路**



# 第一章：网络结构

**按照网络组成类型来划分聚类**（网络结构）：网络边缘、网络核心、接入网和物理媒体

- **网络边缘系统**：主机、应用程序（网络游戏、app应用等）
- **网络核心（起到数据交换的作用）**：网络交换节点以各个圆所组成的链路叫网络核心
- **接入网、物理媒体**：边缘网络与网路核心的链接（有线或者无线的通讯链路）

**网络核心**：是以全球范围内的路由器交换机和链接他们的链路所组成的分布式系统相互配合达到源主机到目标主机的数据传输（发布和接收）

**网络应用是互联网存在的理由**

## 按照网络类型划分

## 网络边缘 

网络边缘包括：分布式应用、主机、支持分布式应用通讯的基础设置

**基础设施**

- **作用**：为服务器的应用提供通讯服务
- **包括**：应用层以下的都是基础设施、应用层协议等级以下的应用实体

**两种模式**：C/S模式（Client/server）也就是客户端/服务器、P2P（peer-to-peer）也就是对等模式

**C/S模式**：浏览器 / web服务器

**P2P模式**：P2P打破了传统的C/S模式，在网络中每个点的地位都是对等的可以是服务器也可以实客户端，也就是说每个节点都能为其他节点提供服务同时也可以享用其他节点的服务

**PPP（point-to-point）和P2P（peer-to-peer）的不同**

- **性质不同**：PPP协议是在点对点连接上传输多个数据包所提供的一个标准方法，P2P是分配工作和工作负载的分布式应用架构
- **特点不同**：PPP是点到点串行通讯协议，P2P是一种网络结构的思想
- **模式不同**：P2P打破了传统的C/S模式，在网络中每个点的地位都是对等的可以是服务器也可以实客户端，也就是说每个节点都能为其他节点提供服务同时也可以享用其他节点的服务。PPP协议通信完毕时，NCP释放网络层链接，收回原来分配出去的IP地址

**向上层提供的服务有两种**：面向连接的（TCP）、无连接的（UDP）

**面向链接服务：**TCP服务

**TCP服务**：可靠性、流量控制、拥塞控制

- 可靠性：确认和重传
- 流量控制：发送方不会淹没接收方
- 拥塞控制：当网络拥塞时，发送方降低速率

**无连接的服务**：UDP服务

## 网络核心

由分组交换构成的网络

**数据怎样通过网络进行传输？**

- 电路交换（circuit switch）：为每一个呼叫预留一个专有电路，如电话网
- 分组交换（packet switch）

### 电路交换：FDM和TDM

Q：两个交换节点连在一起采用什么方法来划分piece？

A：将带宽分成片：频分（Frequency-division multiplexing）、时分（Time-division multiplexing）、波分（Wave-division multiplexing）

TDM（时分）：如果把整个带宽分为24个时间段，24个时间段为一个周期，一个用户分配一个时间端，如果带宽为1.536Mbps，则每个用户会分配（1.536 * 1000）/ 24=64Kbps，因此使用TDM影响单个带宽的速率有几点原因：带宽、单个周期内的时间段

使用TDM计算文件传输的速度需要几点前提：传播时间 = 文件大小Kb / （总带宽M / 1000）/ 周期片段 +  端到端连接建立时间 + 传播延迟，传播延迟=两个主机距离 / 光速（其实是使用的传播介质在大气中的传播速度）

（640/64 + 0.5）= 10.5s

### **分组交换**：虚电路网络（有连接）和数据报网络（无连接）

传输总时间 = 排队时延+传播时延+传输时间+单个存储时间（感觉有几个节点就需要翻倍）

**排队：**分组将会排队，等待传输

**丢失：**如果路由器的缓存用完了，分组将会丢失

因为分组的排队等待会占用缓存，如果带宽不够高则就会造成堵塞，排队多了就回对后来者丢弃（自我理解）

**虚电路网络**

- 虚电路的链接不仅仅体现在发送主机和目标主机上，同时体现在中间所经过的所有节点之上
- 每一个分组都带有VCID代表目标的下一跳
- 在呼叫建立时决定路径，并在传输中保持不变
- 路由器维持每个呼叫的状态信息

**数据报网络**

- 分组的目标地址决定下一条
- 在不同的阶段路由可以改变
- 类似：问路

**面向连接和有链接的区别**

- TCP是面向连接，TCP向应用进程提供服务的时候，仅仅体现在端系统和应用实体上，中间的节点不维护他们的状态
- 有链接网络。体现在虚电路网络，链接不仅仅体现在发送主机和目标主机上，同时体现在中间所经过的所有节点之上

## 接入网和物理媒体

端系统--网络边缘--网络核心

作用：网络边缘接入网络核心

**如何接入？**

1. 住宅网接入
2. 单位网络接入
3. 无线网络接入

接入网络的带宽分为两种：共享和独享，共享则每个个体户分配总的上网带宽，独享则独自享受运营商的带宽。

### modem：调制解调器

俗称的猫接入，将上网数据调制加载到音频信号上，在电话线上传输，在局端其中的数据解调出来：反之亦然。

传输的几种方式：调频、条幅、调相位、总和调制

在音频的载波数据上修改，变成所需要的上网数据

缺点：56Kbps的速率直接接入路由器（通常更低），不能同时上网和通话，不能总是在线

### digital subscriber line（DSL）

分离电话线：一部分用于电话通讯，一部分用于上网

用于上网的分为上行数据和下行数据，两个数据如果是不对称的话叫ADSL

### 电缆网络

有限电视原本用于单项传输，只能传向下行

把有限电视的线路传输进行数字化和双向改造，使用的是FDM

HFC：hvbrid fiber coax（混合光纤同轴电缆），非对称上行30Mbps，下行2Mbps

线缆和光纤网络将个家庭用户接入到ISP（互联网提供服务商）路由器

### 无线接入

无线LANs（建筑物内部：例如无线路由器提供的）和广域无线接入（由运营商提供的：例如3G、4G网络）

### 物理媒介

连接网络的介质

- 导引性媒体：光纤、以太网网线、同轴电缆、双绞线
- 非导引性媒体：无线电                               

光纤传输：速率快、带宽高

## Internet结构和ISP

历史发展：如果所有的网络需要实现互联的话，每个交换机需要与其他交换机互联，复杂度O(n²)，到达一定规模之后会导致可扩展性非常差，因此出现ISP

ISP（Internet Service Provider：互联网服务提供商）：ISP是经国家主管部门批准的正式运营企业，享受国家法律保护，一般是服务器与虚拟主机提供商必须具备的，相互连接通过IXP（Internet exchange point：互联网交换点）

ICP（Internet Content Provider：网络内容服务商）：提供业务，不与ISP同级，仅仅是对用户提供服务，但是大型公司可以自己部署，例如：谷歌

center provider network（中心服务商网络）：大公司由于需要向世界或者较远地区提供优质化服务，则自身拉光纤配置DC（data center：数据中心），配置的DC位置一般是离ISP比较近，一般这种会绕过access ISP和Regional ISP（区域ISP）直接接入ISP

IXP：（Internet exchange point：互联网交换点）

ISP==》IXP==》Regional ISP（区域ISP）==》access ISP

**ISP之间的连接**

- POP：搞成ISP向客户网络的接入点，设计费用结算
- 对等接入：2个ISP对等互联，不涉及费用结算
- IXP：多个对等ISP互联互通之处
- ICP：自己部署专用网络，同时和各级ISP相连接

## 分组延时、丢失和吞吐量

>分组延时分为几种：节点处理延时、排队延时、传播延时

**节点处理延时（固定的）**

- 检查bit级差错
- 检查分组首部和决定将分组导向何处

<span id='jump1'>**排队延时（随机的）**</span>

- 分组到达链路的速率超过了链路的输出速率就会造成排队延时
- 某一分组在队尾，从队头到它之间的传输时间也是有延时

>**流量强度**
>
>设计的流量强度会影响到分组传输的排队延时
>
>链路带宽（R）、分组长度（L）、分组到达队列的平均速率（a） 
>
>La / R  = 流量强度
>
>流量强度趋近于0的时候，排队延时无穷大
>
>**分组丢失**
>
>解释：因为链路队列的缓冲区存储有限，当链路分组队列达到上限后新加入的队列会被自动遗弃

**传输延时（根据单位分组长度而定）**

- 因为传输时需要对分组数据进行存储转发
- 分组长度 / 网络带宽

**传播延时（根据传输距离而定）**

- 物理媒介传输一段分组数据到目的地其中的传输时间就是传播延时
- 传播长度 / 在该媒介的传播速度



| 传播延时 | 节点处理延时                     | 排队延时                         | 传输延时                             | 传播延时                                                   |
| -------- | :------------------------------- | -------------------------------- | ------------------------------------ | ---------------------------------------------------------- |
| 时间     | 固定的，通常是微秒               | 取决于堵塞程度                   | 根据单位分组长度而定                 | 根据传输距离而定                                           |
| 计算方式 | 节点处理数据的时间               | /                                | 分组长度(L) / 网络带宽(R)            | 传播长度(D) / 在该媒介的传播速度(S)                        |
| 描述     | 检查分组首部和决定将分组导向何处 | 检查分组首部和决定将分组导向何处 | 因为传输时需要对分组数据进行存储转发 | 物理媒介传输一段分组数据到目的地其中的传输时间就是传播延时 |
| 符号     | d(proc)                          | d(queue)                         | d(trans)                             | d(pron)                                                    |

所以分组数据从主机到达目标主机有可能经历：排队延时、节点处理延时、传输延时、传播延时

**吞吐量**

- 解释：在源端和目标端之间的传输速率（数据量 / 单位时间）
- 瞬间吞吐量：在一个时间点的速率
- 平均吞吐量：在一个长时间内平均值
- 短板效应：如果传输路径上有多个传输速率不同的链路组成，平均吞吐量取传输速率最少的

LAN（局域网：Local Area Network）、WLAN（无线局域网：Wireless Local Area Network）、WAN（广域网：Wide Area Network）

## 协议层和服务模型

### 协议基本概述

协议的实现借助于下层的服务才能实现，协议实现的目的是为了向上层提供更好的服务

实现本层协议的时候需要借助下层服务提供的接口interface实现

应用的最高层是网络存在的理由

计算机网络分成一个个功能明确的层次，具体实现是使用协议实体的相互动作，协议实体如何实现交互的动作？借助于层接的接口用下层的服务来交换PDU，目的是为了向上层提更更好的服务，向上层提供的服务包括当前层的下层的服务的总和与对等层的交互实现的新特性

**服务**：底层实体向上层实体提供他们之间的通信能力

**服务点（SAP：Services Access Point）**：上层使用下层提供的服务通过层间的接口--地点

**原语（primitive）：**上层使用下层的形式，高层使用底层的服务，以及底层向高层提供服务都是服务器访问原语来进行交互--形式

同一个服务提供者需要同时向多个上层用户提供服务，

### 服务的类型

**面向连接（TCP）：**

- 两个用户在使用下层提供的服务之前需要有一个握手的过程，这种服务就是面向连接的服务

**无连接（UDP）：**

- 两个对等层实体在通信前不需要建立连接，不预留资源，不需要双方都是活跃的

**服务和协议的区别**

- 服务是层级之间的关系，协议是对等层的实体在通讯过程当中应该遵守的规则的集合，服务是在相邻两层之间利用层间的关系在SAP通过原语的方式由下层向上层提供服务

**服务和协议的联系**：实现本层协议的时候需要使用下层提供的服务，本层实现的协议目的是为了向上层提供更好的服务

### 数据单元

**SDU**（服务数据单元：service data unit）

**PDU**（协议数据单元：ptotocol data unit）

**IDU**（接口数据单元：interface data unit）

**ICI**（接口控制信息：interface control infomation）

上层传输的SDU通过SAP传输到下一层，由下一层处理上层的SDU增加header形成本层的PDU，同时又三种情况

- 一对多，上层SDU数据单元较大，下层需要分块处理对每一块增加一个header形成多个本层的PDU
- 多对一，上层的SDU数据单元很小，下层可以合并上层多个较小的SDU然后增加一个header姓曾一个本层的PDU
- 一对一，直接增加header新城本层PDU

**分层处理和实现复杂系统的好处？**

概念化：结构清晰，便于标识网络组件，以及描述其相互关系

结构化：模块化更利于系统的维护和升级

### internet协议栈

物理层-》链路层-》网络层-》传输层-》应用层

物理层：线路之间bit和bit的传输

链路层：提供的是相邻两点之间由物理层传输的bit和bit的传输包装成一个帧，也就是相邻两点以帧为单位的传输

网络层：提供的是以相邻两点之间的帧传输的基础之上向传输层提供端到端之间的传输，两个重要的功能：转发与路由

传输层：解决的是服务进程到服务进程的数据传输，是由端口进行区分 同时把不可靠的报文由TCP包装成可靠的报文

应用层：在传输层提供的进程到进程之间可靠传输的基础之上实现各种各样的网络应用

### 各个层次的协议数据单元

应用层：报文（message）

传输层：报文段（segment）：TCP段、UDP数据报

网络层：分组packet（如果无连接方式：数据报文段datagram）

数据链路层：帧（frame）

物理层：位（bit）

## 总结与习题

是什么？作用？目的？

协议

- 概念：对等实体有一组规则集合作为通讯协议
- 作用：网络之间信息通信的桥梁
- 目的：多端相互通讯
- 组成内容：语法、语义、时序
- 语法：确定协议元素的格式，数据与控制信息的结构与格式
- 语义：确定协议元素的类型，规定通信双方要发何种信息，完成何种动作和做出何种应答
- 时序：规定事件实现顺序的详细说明

按照网络结构类型划分：网络边缘、网络核心、接入网

网络边缘

- 概念内容：主机、支持分布式应用通讯的基础设施
- 作用：应用数据存储

网络核心

- 内容：路由器、交换机
- 作用：信息的存储与转发
- 目的：实现从源主机到目标主机的信息交换
- 交换的类型：电路交换和分组交换
- 电路交换：TDM（时分）、频分（FDM）、波分（WDM）
- 时分的电路交换的计算方式：传播时间 = 文件大小Kb / （（总带宽M / 1000）/ 周期片段） +  端到端连接建立时间 + 传播延迟
- 传播延迟 = 两个主机距离 / 光速（其实是使用的传播介质在大气中的传播速度）
- 分组交换：虚电路网络（如今很少使用）和数据报网络
- 两种分组交换的区别：虚电路网络是有连接的数据报网络是无连接的
- 分组交换和电路交换的区别：分组交换每一个用户都可以享受全部的带宽，而电路交换需要大家共享带宽
- 分组交换的传播时间计算：传播时间 = 文件大小 / 总带宽 + 传播延时 + 排队延时

接入网络

- 概念：物理层的传输介质、无线接入（WLAN）、物理媒体：光纤、双绞线、同轴电缆
- 作用：传输通信信息
- 目的：接入网络核心

### “主机”和“端系统”有什么不同？

没有什么不同，主机就是端系统

### 列举几种不同类型的端系统……



### Web服务器是一种端系统么？

web服务器是一种端系统

# 第二章：应用层

## 应用层协议原理

网络应用的体系架构

### 客户-服务器（ C(client)  / S(serve) ）

缺点：在到达一个阈值的时候会发生断崖式的下降

原因：因为所有的客户都会请求一个服务器所以导致服务器压力提升

### P-P（对等服务）

### C/S和P2P混合服务

中心服务器、用户

服务逻辑：用户上线向中心服务器发送IP地址，下载资源时向中心服务器发送查询信息，中心服务器向已上线的用户中查询资源建立下载连接

用户越多下载越快，同时有中心服务器做集中和分发

### 进程通信

>分布式应用进程通讯需要解决的问题

### 进程标识和寻址问题

标识一个应用进程和寻址一个应用进程需要包括三个要素：主机IP、TCP还是UDP、端口号

### 传输层提供的服务-需要穿过层间的信息

位置：层间界面的SAP（TCP/IP : soket ）

形式：应用程序接口API（TCP/IP : socket API）

**层间接口必须要要携带的信息**：

- 要传输的报文（对本层来说时SDU）
- 谁传的：应用进程的标示：IP+TCP（UDP）端口
- 传给谁：对方的应用进程的标示：对方的IP+TCP（UDP）端口号

**传输层实体**（TCP或者UDP实体）根据这些信息进行TCP报文（UDP数据报）的封装

- 源端口号、目标端口号、数据等
- 将IP地址往下交IP实体，用于IP数据报：源IP，目标IP

### 传输层提供的服务-层接信息的代表

目的：减少层间传输的信息量

TCP socket：

- TCP服务，两个进程之间的通讯之前需要建立连接，两个进程通讯会**持续**一段时间，通讯关系稳定
- 可以用一个证书标识两个应用实体之间的通讯关系，**本地**标示
- 穿过层间接口的信息量**最小**
- TCP socket ：源IP、源端口、目标IP、目标IP、目标端口

**TCP之上的嵌套字（socket）**：对于TCP而言嵌套字是4元组的一个具有本地意义上的一个标示

- 4元组：源IP、源端口、本地IP、本地端口
- 唯一的指定了一个会话（2个进程之间的会话）
- 应用使用这个本地标示，与远程建立通信关系
- 不必再每一次发送都要制定这个4元组
- 简单、便于管理
- 物理上来看就是一个整数

TCP的socket就是一个整数返回的是主机之间的会话关系的本地标示

### 传输层的服务-层间信息的代码

UDP socket

- UDP服务，两个进程之间的通信之前，无需建立连接：每个报文都是独立传输的、前后报文可能给不同的非部署应用进程
- UDPsocket：本IP、本端口
- 发送报文时：必须提供本地IP、port
- 接收报文时：传输层需要上传对方的IP、port

传输时需要传输三个东西：数据报文、UDP socket、对方IP和端口

### 如何使用传输层提供的服务实现应用

定义应用实现协议：报文格式、解释、时序等

编制程序：通过API调用网络基础设施提供通信服务穿报文，解析报文，实现应用时序等

### 应用层协议

定义：

应用协议只是应用进程的一个组成部分

公开协议：HTTP、SMTP等

**应用层需要传输层提供什么样的服务？**

数据丢失率、延迟、吞吐、安全性

### 安全TCP

TCP&UDP

- 都没有加密
- 明文通过互联网传输，设置密码

SSL

- 在TCP上面实现，提供加密的TCP连接
- 私密性
- 数据完整性
- 端到端的鉴别
- 在应用层：应用采用SSL库，SSL库使用TCP通信

SSL socket API

- 应用通过API将明文交给socket，SSL将其加密在互联网上传输

## WEB与HTTP

什么时web、web是由什么组成的、

**web**

- 由一些对象组成
- 对象可以是HTML文件、JPEG图片、Java程序、声音剪辑文件等
- web有一个基本的HTML文件，该基本的HTML文件又包含多干个对象的引用
- 通过URL对每个对象进行引用：用户名、口令字、端口

>![image-20220321202656922](.\assets\image-20220321202656922.png)

web上传和请求不维护文件的边界



### 用户-服务器状态

**cookies：**

4个组成部分

- 在HTTP响应、请求报文中有一个cookie的首部行
- 在用户端系统中保留一个cookie文件，由用户的浏览器管理
- 在Web站点有一个后端数据库

### web缓存（代理服务器）

**优点**

- 降低服务器的载荷
- 降低客户端的相应时间
- 可以使较弱的ICP也能够有效的提供内容

排队延时：

- queue = I / 1-I * (L / R)
- I是流量强度

通过本地缓存进行一部分的流量控制，从而降低流量强度，降低陡增的排队延时，从而达到由2min的响应时间降低到1.2s的响应时间

## FTP（File Transfer Protocol：文件传输协议）

**FTP端口号**：21

向远程主机上传或者下载文件，客户 / 客户端 服务模式

**FTP控制连接与数据连接分开**

- FTP客户端和FTP服务器通过端口21联系，并使用TCP为传输协议
- 客户端通过控制连接获得身份确认
- 客户端通过控制连接发送命令浏览远程目录
- 收到一个传输文件命令时，服务器打开另一个客户端的数据连接
- 一个控制连接和一个数据连接
- 特点：数据命令的发出和数据信息的传输在两个不同的TCP连接上传输
- 有状态的

http在初始设计的时候是无状态的，后续通过cookie形成有状态的

## Email（电子邮件）

三个组成部分：

- 用户代理
- 邮件服务器
- 简单有见传输协议：SMTP

发邮件使用的是SMTP协议，但是拉取邮箱的协议可以是：http、POP3、TMAP

用户代理软件：指可阅读的邮件应用例如：outlook，等

![image-20220327150815263](.\assets\image-20220327150815263.png)

![image-20220327153043528](.\assets\image-20220327153043528.png)

SMTP的发送都是以明文发送，安全性较差

**总结**

- SMTP是持久性连接，发完一个邮件后可以继续发送
- SMTP要求报文（首部和主体）为7为ASCII编码
- SMTP服务器使用CRLF，CRLF决定报文的尾部

**SMTP和HTTP的区别**

- HTTP：拉取（pull），SMTP（推）：push
- 二者都是以ASCII形式的命令/响应交互、状态码
- HTTP：每个对象封装在各自的响应报文中
- SMTP：多个对象包含在一个报文中

### 报文格式：多媒体扩展

由于邮件传输只能传输ASCII报文，因此想要传输附件或者其他形式的信息需要进行多媒体扩展

**MIME：多媒体邮件扩展（multimedia mail extension）**

base64：把不在ASCII编码范围内的字节转化为更长但在ASCII范围内的字节

### POP3协议

用户确认阶段

- 客户端命令：user（用户名）、pass（口令）
- 服务器响应：+OK、-ERR

事物处理阶段、客户端

- list：报文列表
- retr：根据报文号检索报文
- del：删除
- quit：退出

## DNS

DNS：Domain Name System（域名解析系统），是互联网的一项服务，它将作为IP与域名互相映射的一个分布式数据库，能够使人更方便的访问互联网 

因此DNS是给其他应用的应用，完场的由域名到ip的解析

DNS的必要性：

- 需要使用有意义的字符来标识Internet上的设备，因此需要有一种字符串-IP地址的转换方式

### **DNS系统需要解决的问题**

- 如何命名设备？使用具有意义的字符串、解决一个平面命名的重名问题：层次化命名
- 如何完成名字到IP地址的转换？分布式数据库维护和响应式名字查询
- 如何维护增加、删除一个域，需要在域中做哪些工作？

### DNS历史

**ARPANET解决方案**

- 主机名：没有层次的一个字符串（一个平面）：自我理解：没有进行结构划分，所有域名统一管理
- 集中维护一个主机名-IP地址的文件：Hosts.txt
- 每台主机定时从维护站读取文件

**ARPANET解决方案的问题**

- 当网络中主机数量很大时
  1. 没有层次的主机很难分配
  2. 文件的管理、发布、查找都很麻烦

### DNS总体思路和目标

DNS是在网络边缘的应用进程上实现的

**DNS的主要思路**

- 分层的、基于域的命名机制
- 若干个分布式的数据库完场名字到IP姬直的转换
- 运行在UDP之上端口号为53的应用服务
- 核心的Internet，但在应用层协议实现

**DNS的主要目的**

- 实现主机名-IP地址的转换
- 主机别名到规范地址的转换：Host aliasing
- 邮件服务器别名到邮件服务器的正规名字的转换：Mail server aliasing
- 负载均衡：在从域名解析IP地址的时候可以根据服务器的负载情况分配到不同的主机进行提供服务因此达到负载均衡

### DNS的明明结构

NDS采用树状结构的命名方法

Internet根被划分为几百个顶级域

- 通用的（generic）：.con .edu .gov .int .mil .net .org .firm .hsop .web .arts .rec 
- 国家的（countries）：.cn .us .nl .jp

每个域下分为若干个子域

树叶是主机

### 区域名字服务器资源维护记录

每一个区域用一台名字服务器来维护，是关于这个区域的权威，上层的区域知道下层区域如何走

**资源记录（resource records）**

- 作用：维护域名-IP之间的映射关系
- 位置：Name Server的分布式数据库中

**RR格式**

- Domain_name：域名
- TTL：time to live ：生存时间（权威、缓冲记录）
- Class：类别：对于Internet值为in
- Type类别：资源记录的类型

### DNS记录

RR格式：name、value、type、ttl

**Type值**

- A：Name主机、value为主机地址
- CNAME：Name为规范名字的别名、value为规范名字
- NS：Name域名、Value为该服务器的权威服务器的域名
- MX：Value为name对应的邮件服务器的名字

TTL：生存时间，决定了资源记录应当从缓存中删除的时间

**一台设备上网需要具备4个信息**

- 主机的IP地址
- 子网掩码
- Default getway：默认路径
- local name server

### 名字服务器

**名字解析过程**

- 目标名字服务器在Local Name Server中
  1. 查询的名字在服务器内部
  2. 缓存

当本地名字不能解析时使用递归（深度优先遍历）查询根服务器

- 问题：根服务器负担太重
- 解决：使用迭代查询

迭代查询：广度优先遍历

缓存是为了性能，缓存删除是为了一致性

### DNS解析流程

权威DNS、递归DNS、转发DNS

TLD（Top-level domains）-first-level domains：顶级域名服务器，也翻译为国际顶级域名，也称一级域名

![image-20220410203425069](assets/image-20220410203425069.png)

### 攻击NDS

![image-20220327184123027](.\assets\image-20220327184123027.png)

### 总结

NDS：名字命名、名字查询、子域名查询、域名记录方式、NDS缓存的作用、域名维护（增删改查）

一个域名解析的查询步骤：



## P2P应用

### 纯P2P架构

**特点**

- 没有一直运行的服务器
- 任意端系统都可以直接通信
- 利用peer的服务能力
- Peer节点间歇上网，每次IP都有新变化

例子：文件分发（BitTorrent）、流媒体（KanKan）、VoIP（Skype）

### 文件分发时间：C/S模式

 **服务文件传输**：都是由服务器发送给Peer，服务器必须顺序传输（上载）N个文件拷贝：

- 发送一个copy：FUs
- 发送N个：NFUs

**客户端**：每一个客户端需要下载一个文件的拷贝

- Min(d)：客户端最小的下载速率
- 最小下载速率所用到的时间：F/Min(d)

因此将一个文件使用C/S的方式传输F所需要的时间：**D(c/s) >= Max( NF/Us , F/Min(d) )**

用户量较小的时候所需要的时间基本就是用户的最小下载速率，因为服务器的上载很充裕，单数如果用户基数很大，也就是N很大的时候服务器压力会持续增加同时传输速率会线性增长。

### 文件分发时间：P2P模式

**服务器传输**：最少需要上载一份拷贝

**客户端**：每个客户端必须下载一个拷贝

**客户端**：所有客户端总下载量NF

- 最大上载带宽是：Us（客户端上载带宽） + NUi（N分片节点上载带宽）
- 除了服务器可以上载，其他所有的peer节点都可以上载

所需要的最大耗时分为几个主要因素：1、服务器的上传，因为关系到第一份上载的拷贝，2、客户端下载的最小带宽，3、所有peer节点的总上传和下载量

所需要的最大耗时：Min（Us，F/d(min)，NF / NUi（N分片节点上载带宽））

![image-20220404164525872](assets/image-20220404164525872.png)

### 非结构化P2P

两个问题：

- 如果确定所需资源
- 如何处理对等放的加入离开

可能的方案

- 集中、分散、半分散

**集中式目录**

最初的“Napster”设计

1. 对等放连接时告知中心服务器：有什么资源、IP地址
2. Alice查询"双截棍.mp3"
3. Alice从Bob处请求文件

集中式目录存在的问题：单点故障（中心服务挂掉后无法使用）、性能瓶颈（因为查询资源也是走的中心服务器虽然压力小但是还是有瓶颈）、侵犯版权

### **完全结构化分布式**

查询洪范：Gnutella

完全分布式没有中心服务、代码是开源的、

许多Gnutella客户端实现了Gnutella协议

**Gnutella：协议**

泛红查询：发出一个查询，首先向邻居节点发送查询，然后邻居再广度查询

**Guntella：对等放加入**

当加入覆盖网络时需要向邻居网络发送ping，然后获得ping报文的节点进行回传pong报文，标示建立连接同时标示加入覆盖网络

### 混合体

>利用不匀称性：KaZaA

每个节点要么是一个组长要么隶属于一个组

![image-20220404192318090](assets/image-20220404192318090.png)

### P2P文件分发：BitTorrent

加入：peer加入torrent，刚进入没有资源块，通过其他节点累计资源块，向跟踪服务器注册获取peer节点列表建立连接

下载：当peer下载同时也会向其他节点提供上载服务

扰动churn：peer节点可能会随时下线或者上线

一旦一个peer拥有整个文件，他会离开（自私的）或者保留（利他主义）在torrent中

当进入洪流中首先随机请求数据块让自己加入洪流拥有上传和下载的能力，然后会请求洪流中稀缺的块进行对稀缺资源补充peer节点同时自己拥有稀缺资源后会增加别人的访问和请求，因此也变相增加了自己的上传和下载。 个人利益转换成团队利益

### DHT结构化P2P（*自行了解下）

## CDN

### 视频流量服务和CDN：上下文

为什么会有CDN？

现在又很多杀手级应用，大多数都是以提供视频为基础服务的应用，因此占用大量带宽

CDN的基本实现是什么？

分布式的，应用层面的基础设施

### 多媒体

CBR（constant bit rate）：以固定速率编码

VBR（variable bit rate）：视频编码速率随着视频速率变化而变化

> **多媒体流话服务：DASH**（Dynamic Adaptive Streaming over Http）

**服务器**

- 将视频文件分割成多块
- 每个块独立存储
- 告示文件（manifest file）：告知视频的各个版本解析度的url

**客户端**

- 先获取告示文件
- 周期性的测量服务器到客户端的带宽
- 查询告示文件，结合用户的实际情况或者用户手动切换动态改变视频码率，意思就是改变块的访问url

### CND部署策略

>**enter deep**：将CND服务器深入到许多接入网

更接近用户，可以为用户提供较好的服务，缺点是不易管理

例如：Akamai，1700个位置

>**bring home**：部署在关键位置。

因为网络的结构是松散的，因此在某些关键的节点是用户访问的大流量区域，在其中部署CDN节点也可以获取不错的服务，缺点是离用户太远

例如：Limelight

## TCP嵌套字编程

### Socket编程

>应用进程使用传输层协议提供的服务才能够交换报文，实现应用协议，实现应用

TCP/IP：应用进程使用Socket API访问传输服务

地点：界面上的SAP（Socket），方式：Socket API

目标：如何能够借助socket进行通讯C/S应用服务

socket：分布式应用进程之间的门，传输层协议提供的端到端之间的接口

**两种传输服务的socket类型：**TCP（可靠的、字节流服务）和UDP（不可靠、数据UDP报文）



### C/S socket交互：TCP（*）

### socket和websocket的区别

**sokect**：应用层和传输层之间的抽象层，是为了方便TCP和UDP使用出来的抽象层，它提供了一套API接口用于进程和进程之间的数据通信，本身不是协议

**websocket**：是HTML5出来的新协议，用于提供客户端和服务端的持久连接，它是建立在TCP之上的应用层协议。使用的标准的80和443接口，HTTP与HTTPS端（80和443），其中每一个websocket的连接建立都是基于HTTP请求，通过HTTP协议在传送Websocket支持的版本号，协议的版本号、原始地址、主机地址等等一些字段给服务器。Upgrade字段是用于把当前的http协议升级成websocket协议，所以一个websocket的连接是客户端在服务端之间http协议的初始握手阶段将其升级成websocket协议来建立的，其底层仍然是TCP/IP连接。

![image-20220405002805965](assets/image-20220405002805965.png)

**客户端与服务端连接步骤**

>**客户端终止状态类型**：FIN-WAIT-1、FIN-WAIT-2、TIME-WAIT、CLOSED
>
>**服务端终止状态类型**：CLOSED-WAIT、LAST-ACK、CLOSED

1. 服务端：创建socket，
2. 服务端：绑定socket，ip和端口
3. 服务端：监听端口信息
4. 客户端：创建socket，嵌套字
5. 客户端：绑定socket
6. 客户端：发送soket连接请求
7. 服务端：listen监听到连接请求，然后确认身份，同时判断客户端的数据接收能力（第一次握手：请问你是？）
8. 客户端：响应身份确认，确认服务端的发送能力正常，同时要响应自己的发送能力在发送数据，同时也证明了自己已经收到了服务端的数据，确认了自己的数据接收能力正常（第二次握手，我是某，你是？）
9. 服务端：监听身份取人信息并回应，服务器收到客户端的接收和发送能力正常（第三次握手：某某你好，我是某）
10. 服务端：进行连接建立（accept连接请求）
11. 客户端与服务端数据交互
12. 客户端：请求结束，目的是告知服务端自己要关闭连接了（状态改变为FIN-WAIT-1、第一次挥手）
13. 服务端：响应结束，得知客户端的关闭消息，发送消息告知自己已经收到结束消息，自己进入CLOSED-WAIT（第二次挥手）
14. 客户端：收到服务端明白了自己的结束消息，自己进入FIN-WAIT-2
15. 服务端：发送之前未发送完的报文，发送结束后向客户端发送已经全部结束的消息自己进入LAST-ACK（第三次挥手）
16. 客户端：收到服务端发送的完全结束消息，做出一个回应ACK，自己进入TIME-WAIT状态（第四次挥手）
17. 服务端：收到ACK，直接关闭连接
18. 客户端：超长等待后关闭连接

![image-20220405131553768](assets/image-20220405131553768.png)

![image-20220405131614491](assets/image-20220405131614491.png)

## UDP嵌套字编程

**特点**

- 没有握手
- 发送端在每一个报文中都要明确标记目标端口和IP地址
- 服务器必须要从报文中提取端口和IP地址

Client/server socket 交互：UDP

>server 1.1.1.1:80  ------------->  client 2.2.2.2:777
>
>1. server：建立socket，返回一个整数
>2. server：绑定socket，bind
>3. server：readfrom 等待接收报文
>4. client：建立socket
>5. client：绑定socket
>6. client：send，发送报文
>7. server：接收报文，处理完后发送到客户端
>8. client：读取服务器返回的报文

# 传输层

TCP：进程到进程之间以Message（数据报）为单位的逻辑传输，增强下层的服务提供给上层：多路复用、解复用；拥塞控制；流量控制；建立连接

UDP发送发是字节流：无连接（丢失、乱序）

## 传输服务和协议

用户不同主机上面的应用提供逻辑通讯

传输协议运行在端系统

- 发送方：将应用报文分割成报文段，然后传给网络层
- 接收方：将报文重组成报文，然后传递给应用层

TCP可以加强通讯：多路复用、解复用；拥塞控制；流量控制；建立连接

**传输层提供的服务**是由进程道进程之间的服务

**网络层提供的服务**是主机道主机之间的服务

## 多路复用/解复用

A主机道B主机**复用/解复用**流程

>**A主机：**
>
>A某进程应用发送message信息传给TCP层
>
>传输层（TCP协议）：增加head（源IP、端口和目标IP、端口）和message封装成数据包（data）传给网络层
>
>网络层（IP协议）：增加head（目标IP、端口）加上Data，由网卡发送
>
>**B主机**：
>
>网络层（IP协议）：拿到Data数据发送给传输层（TCP协议）
>
>传输层（TCP协议）：拿到由A主机的传输层封装的head（源IP、端口和目标IP、端口），查询socket找到pid然后发送道指定进程

### 无连接传输UDP

**验证校验和**(Don't understand)：用于判断发送的数据是否由丢失，检测在被传输报文段中的差错

Internet校验和的例子：

1、两位16位比特相加，最高位的进位要回卷（最高位舍弃，加到最低位）

2、取反码

目标端：校验范围+校验和 = 1111111111111111 通过校验

## 可靠数据传输的原理

RDT（reliable data transfer）：可靠数据传输

双向流动，但只需要考虑单向数据传输，因为双向的数据传输一般是2个单项数据传输的综合。

**使用有限状态机（FSM：finite-state machine）**来描述发送方和接收方

**状态机可归纳为4个要素，即现态、条件、动作、次态。**“现态”和“条件”是因，“动作”和“次态”是果。

- 现态：是指当前所处的状态。
- 条件：又称为“事件”。当一个条件被满足，将会触发一个动作，或者执行一次状态的迁移。
- 动作：条件满足后执行的动作。动作执行完毕后，可以迁移到新的状态，也可以仍旧保持原状态。动作不是必需的，当条件满足后，也可以不执行任何动作，直接迁移到新状态。
- 次态：条件满足后要迁往的新状态。“次态”是相对于“现态”而言的，“次态”一旦被激活，就转变成新的“现态”了。

![image-20220510155229001](assets/image-20220510155229001.png)

### RDT协议

[RDT协议](https://blog.csdn.net/springtostring/article/details/80379841)

### RDT：在可靠信道上的可靠数据传输

#### **RDT1.0**

上层和下层提供的数据是可靠的，RDT只做接收、发送和封装、解封装

#### **RDT2.0：具有比特差错的信道**

rdt2.0增加了3种新机制：**1.错误检验 2.接收者反馈接受信息（ACK,NAK）3.重传机制**。

在运输层对应用层的数据进行打包处理时，新增checksum（校验和），从而接收端可以对其数据包进行检验，如果正确，返回ACK，发送者继续发送下一个数据包；如果不正确，返回NAK，发送者重传数据。

![image-20220510161751450](assets/image-20220510161751450.png)

![image-20220510161814285](assets/image-20220510161814285.png)

问题：如果NAK和ACK出错无发进行矫正。

#### RDT2.1

**NAK和ACK出错矫正**

在rdt2.0的基础之上，发送方在打包数据包时添加了0或者1编号，同样ACK,NAK字段上也添加了0，1字段，表示0.1号字段的确认或者否定。发送方就有了2种状态发送0号数据包，1号数据包，接收方也有了2种状态等待0号数据包和等待1号数据包。现在假设情景发送方向接收方发送0号数据包，如果接收方接收到0号数据包，返回ACK，但是ACK出现翻转，接收方处于等待1号数据状态，发送方重复发送0号数据，接收方会拒绝0号数据，避免重复。如果接收方接收到0号数据包出现错误，返回NAK，但是NAK出现翻转，接收方处于等待0号数据状态，发送方继续发送1号数据，接收方会拒绝1号数据，避免错序。

图示中：条件 / 动作

发送方图示

![image-20220510164028241](assets/image-20220510164028241.png)

接收方图示

![image-20220510164048340](assets/image-20220510164048340.png)

#### RDT2.2

是在rdt2.1上的基础之上做了小小的改善，**摒弃了NAK，只需采用ACK。**

ACK的反向确认使用ACK的上一个的正向确认。

在ACK的信息上加上了期望的顺序号，现在假设情景发送方向接收方发送0号数据包

1. 如果接收方接收到0号数据包，返回（ACK，1），发送方接着发送1号数据包。
2. 如果接收方接收到0号数据包出现错误，返回（ACK，0），发送方重传0号数据包。

![image-20220510165951378](assets/image-20220510165951378.png)

#### RDT3.0

增加**超时重传**

在rdt2.2的基础之上处理了数据包丢失的情况，增加了计时器的机制，如果在RTT时间段内，发送方没有接收到反馈信息，那么发送方默认数据包已经丢失了，会自动重传。

![image-20220510170335787](assets/image-20220510170335787.png)

![image-20220510170349685](assets/image-20220510170349685.png)

#### 流水线协议

rdt3.0 可以工作, 但是性能很差

主要原因是在RTT时间段内，网络处于空闲状态，而RTT时间段比较长，使得利用率十分的低。

![image-20220510172611737](assets/image-20220510172611737.png)

流水线

- 允许发送方在未得到确认的情况下一次发送多个分组
- 发送方/ 接收方 要有缓冲区，发送方要重传，接收方上层用户的数据使用速率≠接收到的速率

**主要有两类流水线协议: go-Back-N（退步）, selective repeat（选择重传）。**

**滑动窗口协议（slide window）协议**

- 发送窗口：发送缓冲区内容的一个范围（已发送但是未确认分组所构成的空间）
- 发送窗口的最大值<=发送缓冲区的值
- 每发送一个分组移动一个单位

接收窗口（receiving window）= 接收缓存区

- 接收窗口用于控制哪些分组可以接收；
- rw = 1 只能顺序接收 （go-Back-N协议），ACK包含了累计确认（接收到某个数据意味着之前的已经接收成功），一次只能确认一个，按顺序确认，如果错序则触发发送的重发定时器，发送需要重新发送之前已发送但是未确认的分组数据，因为接收方只能接收一个，如果失败他会丢弃所有，因此需要重新发送所有未确认的
- rw > 1 可以乱序接收 （selective repeat协议），ACK做的是单独确认（接收到一个只能确认当前接收成功），如果某个数据没有返回ACK，则发送方触发超时定时器，重新发送该数据

**go-Back-N**：接收时如果遇到地位未接受则直接返回错误，等待地位接收才接收后续，ACK包含了累计确认

**selective repeat**：接收缓存区内所有数据，但是如果有低位没有接收则窗口不向后滑动直至接收完成所有缓存区内数据，ACK做的时单独确认

![image-20220510193422165](assets/image-20220510193422165.png)

![image-20220511101334883](assets/image-20220511101334883.png)

![image-20220511103253644](assets/image-20220511103253644.png)

## 面向连接的传输协议：TCP

点对点；可靠的、按顺序的字节流；管道化；流量控制；面向连接；全双工数据

MSS（Maximum Segment Size）最大报文长度

**报文结构**

![image-20220511110448537](assets/image-20220511110448537.png)

### TCP往返延时（RTT）和超时

RTT的计算，因为当往返长度较长时，往返延时的时间不是很确定，较为分散。

- RTT太长，导致报文段丢失，消极
- RTT太短，导致不必要的重传

SampleRTT延迟计算：对最近的测量值（最近的数据报的往返时间）求平均值

EstimatedRTT（当前加权平均值） = (1 - α)\*EstimatedRtt（之前加权平均值） + α\*SampleRTT

- 指数加权平均值
- 过去样本的影响指数衰减
- 推荐之α=0.125

DevRTT（标准差）=（1-β）\*DevRTT+β\*| SampleRTT - EstimatedRtt |

β推荐值=0.25

超时时间间隔设置为：TimeoutInterval = EstimatedRtt + 4\*DevRTT

### TCP：可靠数据传输

管道化、

TCP在ip不可信的信道上增加了rdt

- 只设置一个定时器、与最老的那一个相关联，类似go-back-n，但是如果超时并不是把这一段全部重新发送，而是重新发送最老的那一段，类似selective repeat，因此，TCP上是一个混合体

超时重发、<span id='jump2'>冗余确认（收到三个ACK50，之后又收到三个ACK50）</span>

简化TCP发送方：忽略流量控制、忽略重复确认

### 产生TCP ACK的建议

| 接收方的事件                                                 | TCP接收方动作                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 所期望的序号报文段按序到达，所有在期望序号之前的数据都已经被确认 | 延迟发送ACK，对另一个报文段的到达最多等待500ms，如果下一个报文段在这个时间段没有到达，则发送一个ACK |
| 有期望序号的报文段到达。另一个按序报文段等待发送ACK          | 立即发送单个累计ACK，以确认两个按序报文段。                  |
| 比期望号大的报文段乱序到达，检测出数据流中的间隔             | 立即发送重复的ACK，指明下一个期望的字节序号                  |
| 能部分或者完全填充接收数据间隔的报文段到达                   | 若改报文段起始间隔（gap）的低端，则立即发送ACK               |

### 快速重传

如果发送方收到同一数据的三个ACK，此时还没有触发超时定时器，直接重新传送期望序号，这种情况叫快速重传。

![image-20220520223118413](assets/image-20220520223118413.png)

### 流量控制

接收方在向其发送方的TCP段部的头部rwnd字段“通告”其中空闲buffer大小，发送方获取到接收方的空闲大小，因此可以保证下次发送数据不会超过此临界值，由此达到流量控制，

### TCP连接管理

两个应用之间的TCP连接，本质是双方知道和对方通讯，为这次通讯做好缓冲区，控制变量置位，告诉对方连接的初始序号

三次握手，

**两次连接可以么？**

失败情况

1. 当服务端收到重复的连接请求后，由于只需要两次连接，就会导致服务端出现一个半连接的状态，没有一个重复的请求连接就会出现一个半连接。
2. 旧数据当成新的数据

![image-20220520225312015](assets/image-20220520225312015.png)

**三次连接解决二次连接的问题**

![image-20220520230225806](assets/image-20220520230225806.png)

### 关闭连接

![image-20220520230948375](assets/image-20220520230948375.png)

大概齐的解决方案，并不是一个完美的解决方案，对称释放，并不完美

## 拥塞控制原理

λin：传送流量大小

λout：接收流量大小

解释：太多数的数据传输超过了网络的处理能力

**场景1：2个发送端、2个接收端，带宽：R**

--拥塞

- 原因：每个接入带宽使用最大吞吐量
- 代价：排队延时增加，当达到R/2的时候排队延时陡增

详细查看：[排队延时](#jump1)

**场景2：理想化传输信息**

>理想化1：发送端有完美的信息，发送端知道什么时候路由的缓冲是可以使用的

--代价

- 每个路由器需要知道传输给对方的缓存大小所需要的数据传输时巨大的，因为每一次传输都需要通知各个路由器的缓存大小
- 即使知道路由什么时候缓冲可以使用，但是λin和λout还是会成线性增长，一旦λin/λout = R/2 时还是会出现巨大延时

>理想化2：掌握丢失信息，知道自己所发的信息丢失了

--代价

- 知道什么时候丢失了，就会触发λin的重发机制，流量强度越接近1，就会导致有效信息λout越少，

**场景3：4个发送端、多重路径、超时/重传**

代价：多个路由器协作使用，没有足够的缓存区，导致数据丢失

原因：没有流量控制，路由器的缓冲区只有0和1，多个发送端同时发送，流量大的会抢走流量小的，导致流量小的丢失，同时有经过多跳以后会导致所有数据都无法完美传送到接收端

### 拥塞控制方法

端到端拥塞控制

- 没有来自网络的显示反馈
- 端系统的延时和丢失推断拥塞
- TCP采用的方法

网络复制的拥塞控制：路由器提供给端系统以反馈信息

- 单个bit置位，SNA、DECbit、TCP/IP、ECN、ATM
- 显示发送端可以采用的速率

#### 网络辅助信息的控制：ATM、ABR

ATM中使用RM（资源管理）信元来向发送方通知信息发送端发送插入在数据间隔中，数据信元、资源管理信元

- NI bit：no increase in rate（轻微拥塞），速率不要增加了
- CI bit：congestion indication，拥塞指示

ABR：available bit rate

- 轻度拥塞：发送使用可使用带宽
- 明确拥塞：发送方限制发送速到到可用带宽

## TCP拥塞控制

端到端的拥塞控制

**如何检测拥塞：轻微拥塞、拥塞**

超时时、[三个冗余ACK](#jump2)

用于控制策略的几个变量：

- congWin：以字节为单位在对方未确认的情况下可以向网络中注入多少个字节
- RTT：往返延时
- MSS：Maximum Segment Size（最大报文长度）

rate（传输速率） = congWin / RTT

**控制策略：轻微拥塞、拥塞如何降低速率；拥塞解除后如何增加速率**

congWin初始值等1MMS

SS阶段：congWin每一次接收加倍增加（每个RTT），慢启动阶段

CA阶段：线性增加，congWin每次增加一个MSS（每个RTT），快速启动阶段

降低速率

- 超时时：CongWin降为1MSS，进入到SS阶段让后再每次往返翻倍增加到CongWin/2（每个RTT，每个周期），从而进入CA阶段
- 3个重复ack：CongWin降为CongWin/2，进入CA阶段

拥塞控制和流量控制时一体的



![image-20220522214105786](assets/image-20220522214105786.png)

![image-20220522214130124](assets/image-20220522214130124.png)

TCP的公平时大致的公平，如果两个主机连接的TCP数量不均等，所获得的带宽也会不均等，TCP和UDP同时存在，那么UDP会抢走过多的带宽，因为UDP没有TCP的流量控制
