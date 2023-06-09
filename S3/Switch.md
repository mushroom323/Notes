以下范围来自bjl的《2023期末复习要点》word版本和yq的《期末复习2023》ppt，内容求并集，非交集部分会打*。

部分内容直接照搬了前人笔记。

# 概论

## 通信网（三要素）

![image-20230603141037289](https://s2.loli.net/2023/06/03/uUbLgJMV726x5YE.png)

## 交换方式的特点

### 电路交换

 电话通信中信息的传送方式：**公共交换电话网（Public Switched Telephone Network，PSTN）**，每一路能提供 64k 速率。

电路交换的特点

- 信息传送的最小单位是时隙：每个时隙采样 8bit，采样率 8kHz，每路通信速率 64kbps。

- 面向连接的工作方式（物理连接）。
- 同步时分复用（固定带宽分配）。
- 无差错控制机制（实时性强）。
- 对通信信息不作处理（透明传输）。
- 流量控制基于呼叫损失制。

**适合实时性、恒定速率的业务。**

![image-20230603141202391](https://s2.loli.net/2023/06/03/zRvDPU5ZwxVkumo.png)

### 分组交换

机制——存储+转发。

分组交换的特点：

- **信息传送的最小单位是分组**：由分组头、用户信息构成，分组头含有选路和控制信息。
- 面向连接（虚电路）方式和无连接（数据报）方式。
- 统计时分复用，动态分配带宽。
- 有差错控制机制：CRC 校验、重发等（设于第二层和第三层协议中）。
- 信息传送不具有透明性：对通信信息作处理，如拆分、重组等。
- 流量控制基于呼叫延迟制。

**适用于突发、对差错敏感的数据业务。**

|            | 虚电路             | 数据报                 |
| ---------- | ------------------ | ---------------------- |
| 分组头     | 简单（逻辑信道号） | 复杂（详细的选路信息） |
| 选路       | 虚连接表           | 每个分组独立选路       |
| 分组顺序   | 有序               | 可能失序               |
| 故障敏感性 | 敏感               | 可靠性高               |
| 应用       | 连续数据流         | 询问/响应              |

### 各类交换方式的基本信息交换单元

| 交换类型 | 基本信息交换单元 |
| -------- | ---------------- |
| 电路交换 | 时隙             |
| 报文交换 | 报文             |
| 分组交换 | 分组             |
| 帧中继   | 帧               |
| ATM 交换 | 信元             |

## 复用技术

### 同步时分复用

- 用于电路交换。
- 采用位置化信道：
  - 根据数字信号在**时间轴**上的位置区别各路。无信息传送时，也会占用信道。
  - 每帧定长。
  - 信号经过复用器和分路器的时延低（1~2 帧）。

### 统计时分复用

分为分组化时分复用、异步时分复用。

- 用于分组交换、ATM 交换。

- 采用标志化信道：使用分组头的标志区分各路通信。

#### 分组化时分复用

- 每个分组前附加标志码，标识分组的输出端或传送路径，与时间无关。
- 分组长度可变、分组头定界。
- 统计复用提高信道利用率。具有一定容量的排队存贮器，解决瞬间的出线冲突。
- 传输时延较小且稳定、处理时延与分组大小有关、排队时延与突发流量有关。

#### 异步时分复用

- 位置固定的标志化信道。
- 信元长度固定、插入空信元保持同步。
- 时延较为稳定。

## 连接类型

### 面向连接/无连接

面向连接：

- 无论物理或逻辑连接，通信分为三阶段：连接建立、传送信息、连接拆除。
- 连接建立后，传送的所有信息均沿此路径传送，保证信息有序性。
- 信息传送的时延（比无连接）小。
- 对网络故障敏感。

无连接：

- 没有连接建立过程，边选路边传送。
- 同一通信的信息到达目的地的路径无法预知，不保证信息有序性。
- 信息传送的时延（比面向连接）大。
- 对网络故障不敏感。

### 物理连接/逻辑连接（虚电路）

同：都具有连接建立、传送信息、连接拆除三阶段。

异：物理连接建立一条通信源和目的之间的物理连接通路；逻辑连接没有物理连接，通过在通信连接上的所有交换节点保存选路结果和路由连接关系实现逻辑上的连接。

## 带宽分配

### 固定带宽分配

### 动态带宽分配

见“复用技术”。

## 目前交换技术的种类和特点

![image-20230603144940947](https://s2.loli.net/2023/06/03/u1SznymXc6AqRBt.png)

## *各种常用网络的交换方式

| 网络       | 交换方式   |
| ---------- | ---------- |
| PSTN电话网 | 电路       |
| B_ISDN     | 分组       |
| Internet   | 分组       |
| No7信令网  | 电路       |
| GSM网络    | 电路       |
| GPRS网络   | 电路&分组  |
| 4G网络     | 分组       |
| 5G网络     | 分组       |
| IMS系统    | 分组       |
| MPLS网络   | 带标记分组 |

## *各种常用网络的重要信令/协议

| 网络     | 信令/协议 |
| -------- | --------- |
| PSTN     | No.7      |
| IMS      | SIP  |
| MPLS     | LDP  |
| SDN      | Openflow  |
| Internet | IP        |

![image-20230605211031159](https://s2.loli.net/2023/06/05/nB34oyRq9rwYUa2.png)

## *电信交换系统的基本结构

由信息传送子系统和控制子系统组成。

- 信息传送子系统：
  - 交换网络：完成交换，实现任意出线与入线的互联。
  - 各种接口：分为用户接口和中继接口，用途是进行信号转换。
- 控制子系统：由处理机系统构成，是交换系统的“指挥中心”。

![image-20230603170345837](https://s2.loli.net/2023/06/03/a3SAxB7NKfn9Wl2.png)

### 程控电话交换机

![image-20230603170405590](https://s2.loli.net/2023/06/03/a4bxt1qgQL9STvG.png)

![image-20230603170948125](https://s2.loli.net/2023/06/03/DRXO4M728dof3yJ.png)

### IP路由器

什么东西...

随便在mooc上找的一张图，反正我觉得这个不考。

![image-20230603171433061](https://s2.loli.net/2023/06/03/TqaDIyZVhfeP5kU.png)

### MPLS路由器

![image-20230603171625815](https://s2.loli.net/2023/06/03/EL7TM5WOQuvtN1w.png)

![image-20230603171732426](https://s2.loli.net/2023/06/03/I7HT6GleYWKPBfi.png)

# 交换网络

## 连接概念

连接

- 集合描述法：所有入线序号为集合$T$，出线序号为集合$R$。连接$c = \{t,R_t\}, t \in T , R_t \subset R$
- 函数描述法：$f(t)=R_t,\space R_t \subset R$
- 排列表达式：$\begin{pmatrix}
  t_1 && t_2 && \cdots && t_n \\
  r_1 && r_2 && \cdots && r_n \\
  \end{pmatrix}$，入线排列表达式$(0,1,2...,N-2,N-1)$
- 图形表示法：略
- 二进制函数表示：$E(x_{n-1}x_{n-2}...x_1x_0)=x_{n-1}x_{n-2}...x_1\bar{x_0}$，表示点到点二进制编号。

一个$N \times N$的交换单元最多可以有$N!$种不同的点到点连接方式。

连接方式

- 直线连接：略

<img src="https://s2.loli.net/2023/06/03/RIuZqW1F7CgMsVc.png" alt="image-20210617195519390" style="zoom: 33%;" />

- 交叉连接（交换置换）：$(1,0,3,2,...,N-1,N-2)$，$E(x_{n-1}x_{n-2}...x_1x_0)=x_{n-1}x_{n-2}...x_1\bar{x_0}$

<img src="https://s2.loli.net/2023/06/03/b6OyAWz3SVgoF5B.png" alt="image-20210617195606140" style="zoom:33%;" />

- 蝶式连接：$\beta (x_{n-1}x_{n-2}...x_1x_0)=x_0x_{n-2}...x_1x_{n-1}$，将输入端二进制最高位$x_{n-1}$与最低位$x_0$互换位置得到。

<img src="https://s2.loli.net/2023/06/03/oaWSqvItLx7bZsQ.png" alt="image-20210617195640668" style="zoom:33%;" />

- 均匀洗牌置换：将入线均分，前一部分和后一部分按顺序一个接一个交叉连接。$\delta(x_{n-1}x_{n-2}...x_1x_0)=x_{n-2}x_{n-3}...x_1x_0x_{n-1}$，将入线二进制地址循环左移一位得到。
- 间隔交叉连接（方体置换）：实现二进制地址编号中第 k 位位置不同的输入端和输出端之间的连接。

<img src="https://s2.loli.net/2023/06/03/aNP435m2LH6B87y.png" alt="image-20210617200821165" style="zoom:33%;" />

~~一点系统结构震撼~~

### 点对点、同发、广播

对于连接$c = \{t,R_t\}, (t \in T , R_t \subset R)$

- 如果$R_t$只有唯一元素，为点到点连接。

- 如果$R_t$包含多个元素，为点到多点连接。

  - 如果$R_t \ne R$，为同发。
  - 如果$R_t = R$，为广播。

  ![image-20230530201514331](https://s2.loli.net/2023/06/03/8DnfC2sM9wWR7h5.png)

## 交换单元的结构、特性、工作原理

基本交换单元的结构、特性（需要的单元个数、是否内部阻塞、同发和广播能力）

### 基本交换单元与开关阵列

- M\*N 有向

![image-20210617201425659](https://s2.loli.net/2023/06/03/JgyatrRL28nCw1N.png)

采用矩阵表示开关通断：

$$
\begin{pmatrix}
1 && 0 && \cdots && 0 \\
0 && 0 && \cdots && 1 \\
\vdots && \vdots && \ddots && \vdots \\
0 && 1 && \cdots && 0
\end{pmatrix}
$$

**不允许出线冲突时，同 column 只允许一个 1 出现；不允许同发广播时，同 row 只允许一个 1 出现。**

- N 无向

特点是主对角线不连通。需要$N(N-1)/2$个双向开关，或者$N(N-1)$个单向开关。

![image-20210617203003483](https://s2.loli.net/2023/06/03/NRVrWJix13HUvT4.png)

- M\*N 无向

需要$M \times N$个双向开关，或者$2 \times M \times N$个单向开关。

![image-20210617203412693](https://s2.loli.net/2023/06/03/ZRw2tAzyU9XWNCD.png)

#### 开关阵列性质

- 空分交换。
- 容易实现同发和广播。
- 交换动作控制简单，信息从入线到出线具有均匀的单位延迟时间：信息从任一入线到任一出线经过的开关数是相等的，不存在时延抖动。
- 开关阵列的控制简单。
- **适用于构成较小规模的交换单元。**

- 开关阵列的性能取决于所用的开关性能。（继电器、模拟电子开关、数字电子开关）

- 无内部阻塞。

实际实现：

- 可用多路选择器。

- 可用 2\*2 交叉连接单元（crossbar）：可以避免出线冲突，但不支持同发。

### S 接线器

- 构成：
  - 交叉点矩阵（开关阵列）。
  - 一组控制存储器（CM，Control Memory）。
- 功能：**实现一个时隙内任意母线间的交换。**

- 规格：
  - 一个 S 接线器所含控制存储器 CM 的数量=入（出）线数。（输入控制 CM 数=入线数，反之）
  - 每个控制存储器 CM 含有的存储单元个数=时隙数。
  - 每个存储单元中存储索引存储单元的地址，为 m 位 bit，且满足$N \le 2^m$，其中 N 为接线器的入（出）线数。
- CM 具有输入控制方式与输出控制方式：
  - **输入控制：控制一条输入线与每一条输出线的交叉点的开启与闭合，存储单元的内容表示对应输入复用线与哪一个输出复用线的交叉点开关在该存储单元所对应的时隙内接通**（对于入线$a$，在当前时隙$TS_i$，从$CM_a$的$i$号存储单元读出需要交换到的出线$b$，打开输入线$a$与$b$相交叉的开关，完成空间交换）
  - **输出控制：控制一条输出线与每一条输入线的交叉点的开启与闭合，存储单元的内容表示对应输出复用线上哪个交叉点在该存储单元所对应的时隙内接通**（对于出线$b$，在当前时隙$TS_i$，从$CM_a$的$i$号存储单元读出接受输入的入线$a$，打开输入线$a$与$b$相交叉的开关，完成空间交换）

<img src="https://s2.loli.net/2023/06/03/FWH5lTOgXJiofEk.png" alt="image-20210617233335178" style="zoom:50%;" />

<img src="https://s2.loli.net/2023/06/03/6NjPZmWu8c7LTKE.png" alt="image-20210617233440479" style="zoom:50%;" />

特性：

- 只完成空间交换，不进行时隙交换。
- 空间接线器按时分方式工作。
- **输<u>出</u>控制方式易于实现多播（将多个 CM 的$TS_i$的存储单元置为同一条输入线即可）。**
- **输出控制方式可自动避免出线冲突。**

![image-20230530201722392](https://s2.loli.net/2023/06/03/B4Rp2yXNJ5dWrOK.png)

### T 接线器

时分交换单元一般分为：共享存储器型交换单元、共享总线型交换单元。

- 共享存储器型：共 2N 个出入线缓存。入线缓存控制读出、出线缓存控制写入。
- 共享总线型：总线按照时隙轮流分配给入线控制部件和出线控制部件使用。
  - $kNV=B/T$（N 为入线数、V 为入线速率、B 为每时隙传送比特数、T 为时隙长度，k 为时隙分配因子）

**异同：**

- 相同点：
  - 两种时分交换单元内部都只有一条唯一的通路，由各子信道分时共享；
- 不同点：
  - 共享存储器型内部唯一的公共通路是存储器，共享总线型内部唯一的公共通路是总线；
  - 共享存储器型的存储器被划分成 N 个区域，N 路输入信号被放在存储器的 N 个区域中， 不同区域的 N 路信号被读出形成 N 路输出信号；共享总线型则按照总线控制权的分配方法，把总线的工作时间划分为多个时段（最简单的是划分为 N 个时隙），在每个时段内把总线分给某条入线；当输入部件获得总线上的输入时隙后把入线的信号送到总线上，同时，对应的输出部件将总线上的信息读入并从出线上输出信息；
  - 共享存储器型交换速度与控制器有关，共享总线型交换速度与总线宽度有关。

**时间接线器的构成：**

- T 接线器
  - 话音存储器（SM，Speech Memory）：暂存话音的数字编码信息。
    - 存储单元个数等于 PCM 线路每帧时隙数；每单元至少 8bit（一路话音）。
  - 控制存储器（CM，Control Memory）：
    - 存储单元个数等于 SM；每单元至少$log_2n（n 为时隙数）$比特。

时间接线器输出控制方式：顺序写入、控制读出。

- SM：前半周期顺序写入话音、后半周期从地址读出话音

- CM：前半周期顺序写入控制地址、后半周期控制读出话音。

  缺点：复用级别越高，对控制电路要求越高，无法达成很大规模；时隙转换延迟不定。

![image-20210618002435156](https://s2.loli.net/2023/06/03/XCspm8HQat5jc6K.png)

时间接线器输入控制方式：控制写入、顺序读出。

![image-20210618002449171](https://s2.loli.net/2023/06/03/XIATOhVdSjNuJmv.png)

特性：

- **时分交换，适用于同步时分复用和统计时分复用信号。**
- SM 划分为 N 个区域，每个区域一个字节，存放一个话音数据。各个区域间不共享，无排队缓冲。
- 存储容量足够大时，无内部阻塞。
- 容量受到信号存储器工作速度和控制器工作速度的控制。
- 交换的控制过程由 CM 硬件实现，速度快。
- 交换时延小且稳定，延迟时间不均匀。
- 严格无阻塞，并且可避免出线冲突。
- **可以实现同发和广播。**
- 速率固定。

![image-20230603173656930](https://s2.loli.net/2023/06/03/EJSBN9fIVglzWQ6.png)

![image-20230530215913179](https://s2.loli.net/2023/06/03/hB2WoIbYctapC17.png)

## 无阻塞网络概念

严格无阻：只要需要交换的入线与出线空闲，就可以通过交换网络建立一个连接。

可重排无阻：只要需要交换的入线与出线空闲，就可以通过交换网络直接地或对已有连接进行重排之后建立一个连接。

广义无阻：给定的网络存在着固有的阻塞可能，但又**可能**存在一种精巧的选路方法，使得只要需要交换的入线与出线空闲，**不必重排**，就可以通过交换网络建立连接。

### CLOS 网络：严格无阻、可重排无阻公式和构造

3 级 CLOS 严格无阻：$m \ge 2n-1$

3 级 CLOS 可重排无阻：$m \ge n$

构造法：根据要求确定中间级个数$m$，一三级分别采用$n \times m$和$m \times n$交换单元，$r=N \div n$（一三级单元个数），中间级采用$r \times r$交换单元。

![image-20210618005822162](https://s2.loli.net/2023/06/03/utmvkYnCoVKxENM.png)

### TST：结构、SM 和 CM 容量和内容、反向半帧、同发特性

详见三电话交换系统.数字交换网络。

![image-20210618012220878](https://s2.loli.net/2023/06/03/kxKjYse3LgXvJVb.png)

内部阻塞：存在，但概率很小，约为$10^{-6}$。

同发特性：

* 初T 顺入控出， S 输出控制/输入控制， 次T 控入顺出。
* 初T 控入顺出， S 输出控制/输入控制， 次T 顺入控出。

特性：

- 反向路由的半帧选择；
- 控制存储器的合用；
- 无内部阻塞条件。

### BANYAN 网络

特性：唯一路径、有阻塞（内部竞争）、单通路、基于树形结构所以能自选路。

**构造法：**构造$N \times N$的 BANYAN 网络，需要$log_2N$级，每级$N/2$个交换单元。拿两个$n \times n$网络，**将$n$个$2\times 2$交换单元作为一级通过混洗连接到前部、或者通过反转混洗连接到尾部。**

![image-20210618010232494](https://s2.loli.net/2023/06/03/4mGtY6TVle3kw9p.png)

降低阻塞方法：

- 增加网络级数（如 BENES 网络），每增加一级，通路数翻倍。但同时失去唯一路径和自选路特性。
- 使用扩展型或膨胀型 banyan 网络。
- batcher-banyan（排序-banyan）网络：严格无阻塞、结构规整、自动选路。
- 减少入线的信息量，加大入线缓存。
- 增加平面数，构造多通道交换网络。（几平面就是几倍的交换单元）

### BENES 网络

两个 banyan 网络背靠背连接，并将中间两级合并为一级。**是可重排无阻塞网络，多通路。**

$N \times N$的BENES网络需要$(N/2) \times (2 \times log_2N-1)$个$2 \times 2$交叉单元。

![image-20210618005420985](https://s2.loli.net/2023/06/03/iYXp39EmM1ZJx8s.png)

![image-20230530232952411](https://s2.loli.net/2023/06/03/NuiOZeLbyXhl81I.png)

# 电路交换（话音交换）

## 程控数字交换机的硬件

### 程控数字交换机的系统结构

![image-20210618143045260](https://s2.loli.net/2023/06/03/diYnKxStvL75Qsw.png)
![image-20230531224131711](https://s2.loli.net/2023/06/03/1K2ekgOfhSr7AvP.png)

![image-20230531190750480](https://s2.loli.net/2023/06/03/RpHtLKcumZDJMb2.png)

### 模拟用户电路的基本功能（不要求电路）

用户电路功能：BORSCHT

- 馈电（Battery feeding）：向用户提供直流馈电电流，电压-48V。
- 过压保护（Overvoltage protection）：二极管用于钳制电压，无论外线电压高于或低于内线，都会由二极管钳制内线为-48V，R 为热敏电阻，可自行烧毁。
- 振铃控制（Ring control）：控制是否向用户线发送 25Hz 铃流信号。
- 监视（Supervision）：监视用户环路的通断状态，通过电阻的直流压降得知用户是否摘机。
- 编译码和滤波（CODEC&filters）：模拟话音信号与 64Kbps 数字话音信号转换。对模拟信号进行编码、对数字信号进行解码；为避免混叠失真、50Hz 干扰、3400Hz 以上频率分量，进行滤波。
- 混合电路（Hybrid circuit）：在用户话机的 2 线双向信号和 PCM 的 4 线单向信号之间进行 2/4 转换。（发生在编码之前和译码之后）
- 测试（Test）：控制是否进行内外线的故障检测。

![image-20230603175012524](https://s2.loli.net/2023/06/03/UNOtofXdmDyuMvW.png)

### 数字中继器的基本功能（不要求电路）

数字中继电路（用于与数字交换局或远端模块的连接）：

- 内部 NRZ 码与外部 HDB3 码之间的转换
- 帧同步
- 复帧同步
- 时钟提取：从输入的数据流中提取时钟信号，作为输入数据流的基准时钟；从接收的数据流中搜索并识别到同步码，以确定一帧的开始，以便接收端的帧结构排列和发送端的完全一致。

- 提取和插入随路信号

![image-20230603180739075](https://s2.loli.net/2023/06/03/THoxmKElDOaXh72.png)

### *数字交换网络

- TST 大题，全程话路连接

T 接线器，串并复用与分路并串的时隙换算：

<img src="https://s2.loli.net/2023/06/03/8cik2jFsNg9nlR3.png" alt="image-20210618144856786" style="zoom:33%;" />

- 总共有$m$条 HW，第$i$条 HW 上 $TS_j$的 ITS 号 =$j \times m + i$。

![image-20210618144454756](https://s2.loli.net/2023/06/03/9sCzU1SnPNAja5c.png)

话路建立：

- 用户 A 呼叫用户 B：用户级出线$HW_0TS_{8}$经过复用器$M_0$交换为$ITS_{16=2*8+0}$，选择交换时隙$ITS_{20}$；
- 用户 B 建立到用户 A 的连接：采用反向法（半帧法）计算，由$ITS_{20}$，T 接线器输入信号每帧为 64 时隙（由两条 PCM32 线路复用而来），半帧为 32，故 20+32=52，所以 B 到 A 的连接选择$ITS_{52}$。

完整版：

- 每个用户模块连接**256**个用户，内部提供**8**条**HW**，**32TS/HW**

  (即**256\*256**)的交换

- 所有模块(包括用户模块**/**中继模块**/**信号音源)连接到**TST**的中央交换网络，支持**16K\*16K**的交换(每个**T**支持**512\*512** 交换)。用户模块采用复接方式接入**TST(A**为复接点**)**，实现话务集中

- 用户**A**接至模块**0**的**HW0TS1**，用户**B**接至模块**n**的**HW7TS31** (双向都使用该时隙)

- 系统为用户**A**选择模块**0**的空闲时隙**HW0TS3**(双向)，模块**0**的**HW0**固定连接到**M0**的**HW0**;为用户**B**选择模块**n** 的空闲时隙**HW3TS8**(双向)，模块**n**的**HW3**固定连接到**M31**的 **HW8**

- **A**→**B**连接时，**TST**网络选择使用内部时隙**ITS4**；**B**→**A**连接时， 使用反相法选择内部时隙

![image-20210618145637383](https://s2.loli.net/2023/06/03/Q6VgDXWk7E4sZnd.png)

![image-20230531220507294](https://s2.loli.net/2023/06/03/6xyrpTR7dLVZgO1.png)

### 控制部分

控制方式：

- 集中控制：处理机对交换系统内所有功能及资源统一控制。
  - 处理机直接控制所有功能的完成和资源的使用，因此控制关系简单，处理机间通信接口简单。
  - 单个处理机上的应用软件复杂、庞大。
  - 一旦处理机系统故障，整个控制系统失效。可靠性较低。
- 分级分散控制：控制系统由多个处理机构成，分别完成不同功能并对不同资源实施控制。
  - 处理机之间分等级，高级别处理机控制低级别处理机。
  - 处理机之间通信接口较为集中，控制方式复杂，但比全分散简单。
  - 各处理机上应用软件复杂程度适中。
  - 控制系统的可靠性适中。
- 全分散控制：各个处理机之间独立工作，分别完成不同功能并对不同资源实施控制。
  - 处理机之间不分等级，不存在控制与被控制关系。
  - 每台处理机只完成部分功能，要求各处理机协调配合完成整个系统功能，通信接口复杂。
  - 每台处理机应用软件只完成该处理机承担的功能，较为简单。
  - 可靠性较高。
  - 系统具有良好的扩充能力。

多处理机之间的工作分担方式：

- 功能分担：多个处理机分别完成同一话务的不同功能。

- 负荷（话务）分担：多个处理机各自完成一部分话务功能。

- 冗余。

  - 双机冗余配置：两套处理机系统，一个主用、一个备用。

    - 同步方式：主备用机同步工作，同时执行指令并比较结果。
    - 互助方式：主备用机负荷均分，分别承担一半话务负荷。一台机器故障，负荷全部转移到另一台机器上。
    - 主备用方式：主机在线运行，备用机处于待机状态。（冷备用：不保存动态呼叫数据，故障切换时直接呼损。热备用：保存动态呼叫数据，故障切换时不会呼损。一般采用热备用。）


  - N+m 备份：N 个处理机在线运行，m 个处理机处于备用状态。

> yq的在这里还有处理机间的通信方式、交换软件系统的组成、数据库系统——局数据之类的，全跳了，我不觉得会考。

## 程控数字交换机的软件

### 呼叫处理软件设计方法

SDL 图：

<img src="https://s2.loli.net/2023/06/03/8afQVlym4wcN91C.png" alt="image-20210618152614630" style="zoom: 67%;" />

代码实现方法：

![image-20230603182736775](https://s2.loli.net/2023/06/03/tW9q4DwYc6pOgyx.png)

### 呼叫处理

呼叫处理：

- **输入处理、摘挂机检测（重点）：**在呼叫处理的过程中，输入信号主要有摘机信号、挂机信号、所拨号码和超时信号，这些输入信号也叫做事件，输入处理就是指识别和接收这些输入信号的过程，在交换机中，它是由相关输入处理程序完成的。
- 分析处理：分析处理就是对输入处理的结果（接收到的输入信号）、当前状态以及各种数据进行分析，决定下一步执行什么任务的过程，如号码分析、状态分析等。分析处理的功能是由分析处理程序完成的。
- 输出处理：任务执行是指在迁移到下一个稳定状态之前，根据分析处理的结果，完成相关任务的过程。它是由任务执行程序完成的。在任务执行的过程中，要输出一些信令、消息或动作命令，如 No.7 信令、处理机间通信消息以及送拨号音、停振铃和接通话路命令等，将完成这些消息的发送和相关动作的过程叫做输出处理，输出处理由输出处理程序完成。

本局呼叫处理：

<img src="https://s2.loli.net/2023/06/03/j23brGzshTy8pek.png" alt="image-20210618152634475" style="zoom: 67%;" />

![image-20230531222708312](https://s2.loli.net/2023/06/03/9qWG2OyhDBsEmYz.png)

**摘挂机检测（重点）**

<img src="https://s2.loli.net/2023/06/03/p7KbJqYFW5tclfM.png" alt="image-20210618152926366" style="zoom:50%;" />

<img src="https://s2.loli.net/2023/06/03/2YWtwC5yf1i9RNZ.png" alt="image-20210618152949117" style="zoom:50%;" />

### 任务分级和调度

任务分级：

- 级间转移：级别高的程序优先处理。

| 程序级别 | 程序功能                       | 启动方式 | 响应速度         |
| -------- | ------------------------------ | -------- | ---------------- |
| 故障级   | 故障识别和紧急处理             | 硬件中断 | 立即响应         |
| 周期级   | 按一定周期进行的各种扫描和驱动 | 时钟中断 | 在严格时限内相应 |
| 基本级   | 分析处理和各种无时限任务       | 事件队列 | 在一定时限内相应 |

![image-20230531223339050](https://s2.loli.net/2023/06/03/2s1dFRaVYcXnCo5.png)

**时间表调度算法：**

- 每次时间中断到来时，对时间计数器加一，根据时间计数器的值形成时间表行地址。屏蔽表用于控制在该时刻程序是否被调用执行。

![image-20210618165844950](https://s2.loli.net/2023/06/03/IRA8pMFu5w9Cf4j.png)

时间表的每一行代表时间，每一列为一个比特，代表一个程序。若在第 i 行第 j 列的比特位的值为“1”, 则表示在这个时刻该程序被调用；若为“0”则不被调用。每次时间中断到来时，都要对时间计数器做加“1”操作，时间计数器的值形成了时间表的行地址。程序地址表保存被调用程序的入口地址。屏蔽表用于控制在该时刻该程序是否被调用执行，屏蔽表的每一位对应一个程序，如果某一位为“1”则表示该程序可执行，否则不执行。屏蔽表提供了一种灵活控制程序调用的机制，不用频繁更改时间表了。若时间中断周期为 10ms，则由上述表格结构的设计可知：

![image-20230531223747066](https://s2.loli.net/2023/06/03/HirIBwTkMDqlthd.png)

### BHCA 计算

BHCA（maximum number of Busy Hour Call Attempts，最大忙时试呼次数）

- 处理机的系统开销=固有开销（与呼叫处理次数无关）+非固有开销（与呼叫处理次数有关）
- BHCA 计算：$t=a+bN$，t 为总开销时间，a 为固有开销，b 为处理一次呼叫的平均非固有开销，N 为单位时间内处理呼叫总次数。注意单位是小时。

### 过负荷控制的概念

![image-20230603183323986](https://s2.loli.net/2023/06/03/YTShHw8yROp4ruN.png)

# 分组交换

## *路由器的交换结构

高端路由器的CLOS结构

不知道是个什么东西，没见过，也许是指M40交换机？

## *ATM网络

![image-20230603185609171](https://s2.loli.net/2023/06/03/CF6Jscdm3ZaygrD.png)

![image-20230603185618955](https://s2.loli.net/2023/06/03/LAlwyBU9VdFzjmO.png)

## MPLS的基本组成和原理

- 特点：面向连接（VPC/VCC）、多协议、标签交换

- MPLS 在多种第二层协议上进行标记交换，将第二层和第三层有机结合。

- 核心思想：**边缘路由，核心交换**：边缘路由保持与现有协议兼容，增强核心网络交换速度。

概念：

- **LSP**：Label Switched Path 标记交换路径，类似虚电路。
- **FEC**：Forward Equivalence Class 前转等价类，灵活按照多种方式划分，相同 FEC 的包具有相同 Label，走相同 LSP。
- LIB：Label Information Base 标记信息库，保存转发 Labeled 分组所需要的信息。
- Ingress LER：Ingress Label Edge Router 入口边缘路由器，为每个 FEC 生成 Label，映射到 LSP 下一跳的标记。对入口 IP 分组进行分类，确定 FEC。
- **LER**：根据 FEC 查询 LIB 得到下一跳 Label，将 Label 插入 IP 包头，从相应端口发送。
- **LSR**：Label Switch Router，维护 LIB、完成标记置换。
- Egress LER：去掉 Label 还原成普通 IP 包继续转发。

主要特点：

- 标记置换：将 2 层的交换速度带到 3 层
- 控制平面与转发平面分离：便于采用新的路由协议和交换技术
- 通过标记堆栈实现多层次的转发：提高可扩展性

对比：

![image-20230603195831182](https://s2.loli.net/2023/06/03/8H61oVNDE3b5tnY.png)

## MPLS交换原理

标签操作：

- Push：标签入栈，进入子路由域内传输。
- Pop：标签出栈，回到父路由域传输。
- Replace：置换标签，在同一路由域内传输。

LDP 标签分配过程：

- 发现相邻的 LDP 对等体：使用 UDP 广播，发现相邻 LSR
- 建立 LDP 会话：相邻 LSR 建立 TCP 连接，建立 LDP 会话
- 建立 LSP：下游 LSR 分配标记并沿着 LDP 会话通知上游 LSR

![image-20230601183414365](https://s2.loli.net/2023/06/03/MA9Eto57mpJxVRP.png)

![image-20230601183422144](https://s2.loli.net/2023/06/03/jCSGaxz5fc8ODMh.png)

![image-20230601195040050](https://s2.loli.net/2023/06/03/Dmk5w7rlneEbicJ.png)

# 信令系统

## *信令分类

![image-20230603212316835](https://s2.loli.net/2023/06/03/PpJVIUKkq7Hhx4t.png)

## NO.7信令系统

### 七号信令协议栈

- MTP：公共的消息传递部分（重点）
  - MTP1——物理层
  - MTP2——数据链路层
  - MTP3——网络层一部分
- SCCP：信令连接控制部分——网络层一部分
- UP：用户部分——传输层、会话层、表示层、应用层
  - ISUP：综合业务数字网部分
  - TUP：电话用户部分（重点）
  - DUP：数据用户部分
  - TCAP：事务处理能力部分
    - INAP：智能网应用部分
    - OMAP：操作维护应用部分
    - MAP：移动通信应用部分

MTP 各级功能：

| OSI 对应     | MTP 部分             | 功能                                                         |
| ------------ | -------------------- | ------------------------------------------------------------ |
| 物理层       | MTP1：信令数据链路级 | 规定信令链路电气特性和接入方法。速率 64Kbps。                |
| 数据链路层   | MTP2：信令链路功能级 | 将第一级中透明传输的比特流划分为不同长度的信令单元，有差错检测和重发校正。 |
| 网络层的部分 | MTP3：信令网功能级   | 保证信令单元在网络中的可靠传输。                             |

![image-20230601214904922](https://s2.loli.net/2023/06/03/MzNiCwrTW3VkIHe.png)

TUP 功能：规定电话呼叫的建立和释放的信令流程，以及实现这些流程的消息和消息编码。并能支持部分用户补充业务。提供电话呼叫的控制信令，完成电话呼叫续接和控制。

- 处理 SIF 字段中的 CIC、H0H1、信令信息。
- 呼叫信令：

| 消息类型 | 含义                                   |
| -------- | -------------------------------------- |
| IAM      | 初始地址消息                           |
| ACM      | 地址全消息，表示被叫空闲，呼叫建立成功 |
| ANC      | 被叫应答、计费消息                     |
| CLF      | 前向释放                               |
| CBK      | 后向释放                               |
| RLG      | 正常呼叫结束时电路释放监护消息         |
|          |                                        |
| SLB      | 市话忙                                 |
| STB      | 长话忙                                 |
| CGC      | 电路群拥塞                             |
| SEC      | 交换机拥塞                             |

<img src="https://s2.loli.net/2023/06/03/K8nrIwOAQ5zLoxh.png" alt="image-20210618213327736" style="zoom:50%;" />

![image-20230603205320447](https://s2.loli.net/2023/06/03/ruTZ83QDWRG7jgf.png)

**信令消息的传递涉及的协议栈：**

![image-20230603213406538](https://s2.loli.net/2023/06/03/BA9JrUPgqu6WKpM.png)

### 我国的信令网结构

![image-20230603212148477](https://s2.loli.net/2023/06/03/TbWSrMjgpERBPet.png)

### *信令点编码

国内信令点编码：24bits

| HSTP 高级信令转接点 | LSTP 低级信令转接点 | SP 信令点 |
| ------------------- | ------------------- | --------- |
| 8bit                | 8bit                | 8bit      |

国际信令网的信令点编码：14bits（大区和 SP 变为 3bit）

## SIP信令

SIP是一种C/S（客户-服务器）结构的协议。

**基本特点：**

- **应用层**控制协议，独立于底层协议。用于建立、修改和中止 IP 网上的双方或多方多媒体会话。
- 基于文本的消息编码，使用 UTF-8 字符集，易于读取和调试。
- 具有多个层次的可实现性，最小的实现非常简单、最完全的实现能够完成非常多的功能。
- 通过代理、重定向功能支持用户的移动性。
- 可与 RTP/RTCP、SDP、RTSP、DNS 等协议配合。易于实现和扩展

**SIP 系统中各网元（用户代理、代理服务器、注册服务器）作用：**

- 用户代理（User Agent）：终端用户设备，用于创建和管理 SIP 会话的设备。UA 发出消息，代理服务器对消息进行响应。
- 代理服务器：接收 UA 的会话请求并查询 SIP 注册服务器，获取收件方 UA 的地址信息。然后，根据收件方域的位置，将会话邀请转发给收件方 UA 或代理服务器。
- 注册服务器：包含域中所有用户代理的位置的数据库。在 SIP 通信中，注册服务器会检索参与方的 IP 地址和其它相关信息，并将其发送到代理服务器。

**SIP 相关协议：**

- SIP 呼叫准许与建立、SDP 媒体通道协商与建立：基于 TCP 或 UDP
- RTP 媒体流：基于 UDP

**SIP 消息：**

| 消息       | 功能                                             |
| ---------- | ------------------------------------------------ |
| register   | 在注册服务器上注册用户代理 UA。                  |
| invite     | 发起呼叫，并对会话进行描述。                     |
| 100trying  | 正在尝试连接。                                   |
| 180ringing | 正在振铃。                                       |
| 200ok      | 请求成功。                                       |
| ack        | 主叫确认收到被叫发送的对 invite 的确认响应。     |
| bye        | 释放连接，主被叫双方都可以发出。                 |
|            |                                                  |
| 1xx        | 通知服务器或代理正在执行处理，终端应该等待响应。 |
| 2xx        | 成功。                                           |
| 3xx        | 重定向响应，终端应向新地址发送请求。             |
| 4xx        | 请求失败，被拒绝。                               |
| 5xx        | 服务器内部错误造成不能响应。                     |
| 6xx        | 全局错误，未来该用户所有请求都无法响应。         |

SIP 地址与端口：`sip:username@company.com:5060`。

**SDP 媒体协商的重点内容：**SIP 消息体主要是 SDP 会话描述协议，用于描述这次回话的媒体信息。话音流使用 RTP/RTCP 传输。

SIP基本消息流程: 正常呼叫建立与释放过程

- 基本呼叫建立：

<img src="https://s2.loli.net/2023/06/03/wgb5pOqhyATKWnv.png" alt="image-20210620142205094" style="zoom: 33%;" />

- 正常呼叫释放：

![image-20230603213111258](https://s2.loli.net/2023/06/03/evMohyUw2riSVCb.png)

**SIP 消息与TUP对应转换：**

![image-20230603213145511](https://s2.loli.net/2023/06/03/GuFhARWSbMT941q.png)

# 移动交换

## 移动通信的几个概念

入网、鉴权、切换、漫游、位置更新、网络附着

| 概念     | 内容                                                         |
| -------- | ------------------------------------------------------------ |
| 入网     | GSM 中，MS 向 BSC 申请 SDCCH 或 TCH 信道进行通信的过程。GPRS 中，MS 向 SGSN 发送入网附着请求的过程。 |
| 鉴权     | MS 使用网络之前，网络检查其合法性的过程。                    |
| 切换     | 将一个正处于呼叫状态中的 MS 转换到新的业务信道上的过程。通常由 MS 位置移动或小区业务负载均衡触发。 |
| 漫游     | 用户当前位置非本号码的 HLR 服务区。                          |
| 位置更新 | MS 从一个位置区移动到另一个位置区，发现其存储器中的 LAI 位置区标识与接收到的 LAI 发生变化，便执行登记的过程。 |
| 网络附着 | MS 附着在 GPRS 网络上，MS 和 SGSN 中记录该用户的路由信息，建立对于该用户 IMSI 的移动管理上下文（PDP）。 |

## GSM、GPRS的基本网络结构和网元功能

### GSM 网络结构、网元功能：

主要分为 MS、BSS、NSS、OMC 四大部分。

- MS（移动台）：移动客户设备部分，分手持机和车载台。包括移动终端（ME）、手机客户识别卡（SIM）。

- BSS（无线基站子系统）：由 MSC 控制，是与 MS 通信的系统设备。主要完成无线发送接收和无线资源管理等功能。

  包括基站收发信机 BTS、基站控制器 BSC。

  - BTS（基站收发信机）：完成无线传输、无线与有线的转换、无线分集、无线信道加密。
  - BSC（基站控制器）：连接 BTS 与 MSC、为 BTS 和 OMC 的信息交换提供接口，具有控制一个或多个 BTS 的功能。完成无线网路资源的管理、呼叫和通信链路的建立与拆除、本控制区内 MS 越区切换的控制、小区配置数据管理、功率控制等。

- NSS（交换网路子系统）：完成交换功能、完成客户数据、移动性管理、安全性管理所需的数据库功能。

  包括 MSC、HLR、VLR、AUC、EIR。

  - MSC（移动交换中心）：蜂窝通信网络的核心，对位于本 MSC 控制区内的移动用户进行通信控制和管理。完成信道的管理和分配、呼叫的处理和控制、用户位置信息的登记与管理、越区切换和漫游的控制、用户号码和移动设备号码的登记和管理、服务类型的控制、用户鉴权、为系统中连接其他 MSC 和其他公用通信网络（PSTN、ISDN、PDN）提供链路接口。

  - HLR（归属位置寄存器）：存储本地用户位置信息的数据库。每个用户都必须在某个 HLR（相当于该用户的原籍）中登记。登记内容：

    - 永久性参数：ISDN 号码、移动设备号码 IMSI、接入优先级、预定业务类型、保密参数等。
    - 暂时性参数：用户当前所处位置的有关参数。

    HLR 的目的是：

    - 即使用户漫游到该 HLR 服务区外，HLR 也要登记漫游区域传送来的位置信息。
    - 保证呼叫一个未知位置的移动用户时，均可由该移动用户的 HLR 获知它当前处于哪个区域，从而建立通信链路。

  - VLR（访问位置寄存器）：存储来访用户位置信息的数据库。一个 VLR 可以为一个或多个相邻 MSC 服务。

    - 当移动用户漫游到新的 MSC，向对应的 VLR 申请登记。
    - VLR 从该用户的 HLR 查询参数，给用户分配一个新的漫游号码（MSRN），通知其 HLR 修改用户位置信息。为其他用户呼叫此用户提供路由信息。
    - 移动用户离开此 VLR 服务区时，HLR 接收到新的 VLR 发来的消息，通知旧的 VLR 删除此用户的位置信息。

  - AUC（鉴权中心）：可靠地识别用户的身份，只允许有权用户接入网络获得服务。

  - EIR（设备标志寄存器）：存储移动台设备参数的数据库。识别用户的 IMEI，对移动设备进行鉴别和监视，拒绝非法移动台入网。

  - SMS-SC（短信息业务中心）：提供点对点短信服务和广播式公共信息服务。

- 维护操作子系统（OMC）：对整个 GSM 网路内各种部件进行功能监视、状态报告、故障诊断、设备管理。包括系统的自检与报警、备用设备的激活、系统的故障诊断与处理、话务量的统计和计费数据的记录与传递、各种资料的收集分析与显示等。

- GMSC（网关交换中心）：负责移动交换网络与 PSTN 固话网络的互联互通。进行信令控制与话音转发。

![image-20230603214410332](https://s2.loli.net/2023/06/03/3PFWpko5vLIc4h2.png)

### GSM网络信令基本过程（始呼、寻呼、切换）

切换：

- 同一 BSC 内小区间的切换：

![image-20230603213815725](https://s2.loli.net/2023/06/03/Ghdor2mf9AVRXOB.png)

- 同一 MSC 内不同 BSC 的小区间切换：

<img src="https://s2.loli.net/2023/06/03/kYq1c5njitwPV9J.png" alt="image-20210620140436414" style="zoom: 25%;" />

- GSM 越区切换：

![image-20230603213804459](https://s2.loli.net/2023/06/03/bVG6WklED92eTpy.png)

### GPRS 网络结构、网元功能

GSM 一个用户只能分配一个信道。GPRS 按需动态占用资源，速率可达 171.2Kbps。

<img src="https://s2.loli.net/2023/06/03/vT7AbsyJpKEcNgM.png" alt="image-20210620141258785" style="zoom: 33%;" />

组成：

- PCU：在 BSC 中新增的设备，属于分组域。负责移动分组数据的组装和拆解。
- SGSN：功能类似 MSC/VLR。
  - 记录移动台当前位置信息，进行鉴权、移动性管理、路由选择。
  - 在 MS 和 GGSN 之间完成移动分组数据的发送和接收。
- GGSN：网关，功能类似 GMSC。
  - 可以把 GPRS 分组数据包进行协议转换，提供与多种不同数据网络的互联。
  - 为 MS 动态分配 IP 地址，或接入 DHCP 服务器来实现动态分配 IP 地址。

GPRS 系统的电路域与分组域：

- 电路域：（原 GSM 部分）BTS、BSC、MSC/VLR，HLR、AUC 等。
- 分组域：PCU、SGSN、GGSN、BG（？）、骨干网、ISP 网等。

GPRS 分组域中的数据通道：

- BSC（PCU）与 SGSN 之间：BSSGP 协议，采用虚电路透明地传输新型号和数据。
- SGSN 和 GGSN 之间：采用隧道技术，允许多协议包传输。对传输信息负责（不透明），基于 IP 协议栈，在 OSI 传输层使用 UDP。

## 3G

了解3G网络结构演进过程（电路域+分组域->全IP）

## 4G

特点：

- 业务平面与控制平面完全分离化。
- 核心网趋同化、交换功能路由化。
- 网元数目最小化、协议层次最优化。
- 网络扁平化、<u>全 IP 化</u>。

网元结构和功能（了解）：网元分为：UE、eNodeB、MME、S-Gateway、P-Gateway、HSS、IMS。

<img src="https://s2.loli.net/2023/06/03/AjUpuskClzRxf7I.png" alt="image-20210620144946402" style="zoom:33%;" />

- eNodeB：<u>eNodeB 之间可以直接通信</u>。功能：无线资源管理、IP 头压缩和数据流加密、无线接入控制、用户数据向 S-GW 路由、MME 发起的呼叫信息的调度和发送。
- MME 移动管理实体：移动性管理、会话管理、用户及安全与密钥管理、承载控制、信令加密和完整性保护、P-GW/S-GW 选择。
- S-Gateway 服务网关：<u>是 eNodeB 之间切换的锚点</u>。功能：分组路由和转发功能、IP 头压缩、用户平面数据交换、计费信息收集和监听、漫游路由优化与 QoS 保障。
- P-Gateway 分组数据网关：<u>UE 的 IP 地址分配、数据包过滤</u>、分组路由和数据转发等等。
- HSS 归属签约用户服务器：存储用户业务相关的签约信息、4G 位置信息等。
- IMS：略。

![image-20230603214043673](https://s2.loli.net/2023/06/03/9gsOeGcCfHlkbBQ.png)

 ## 5G

业务特点：

- 增强移动宽带（eMBB）：高峰值速率
- 海量机器通信（mMTC）：高连接数密度
- 高可靠低时延通信（uRLLC）

关键技术：

- 高频段高带宽传输：毫米波通信。
- 新型多天线传输：大规模 MIMO。
- 同时同频全双工。
- 多种多址接入方案。
- D2D：Device to Device。
- 微基站。
- 新型网络架构。

用户面与控制面分离，网元->微服务

- 独立组网 (SA)：要新建大量的 5G 基站和核心网
- 非独立组网 (NSA)
  - 利用现有 4G 基站和核心网，增设 5G 基站，快速部署 5G 业务
  - 双连接：手机能同时跟 4G 和 5G 都进行通信

![image-20230603214144358](https://s2.loli.net/2023/06/03/VKykMduaEhNm673.png)

![image-20230603214152027](https://s2.loli.net/2023/06/03/trqSLjCID2ZUFRT.png)

![image-20230603214157295](https://s2.loli.net/2023/06/03/Aly1F3X2oZ69nTW.png)

# 新一代融合网络交换技术

## 软交换的系统结构、四层结构

* 软交换技术特征：

  * 业务处理与呼叫控制分离。（控制与控制不分离）
  * <u>呼叫处理与承载分离。</u>
  * 呼叫控制与承载分离。
* 四层体系结构、各层典型设备：
  * 业务/管理层：<u>AS应用服务器</u>（提供业务执行、管理开发环境）、NMC系统管理中心。
  * 会话控制层：<u>SSC软交换控制器</u>（呼叫控制、资源管理、路由控制、地址解析）、MS媒体服务器。
  * 核心传送层：IP网络。
  * 外围接入层：<u>SG信令网关</u>（连接7号信令网和IP网、信令格式转换）、MG中继媒体网关（连接PSTN与IP网络、实现媒体传输格式转换）、<u>AG接入网关</u>和IAD综合接入设备（连接各类接入网、完成媒体流转换、信令处理等功能）。

![image-20230603214839826](https://s2.loli.net/2023/06/03/5aUQodnr9ljJH6e.png)

![image-20230604220132527](https://s2.loli.net/2023/06/04/g3UzsBdEkcpVPaL.png)

## IMS 特点

大概是软交换的全面升级版。增强了移动性。

- 全 SIP 信令。
- 业务处理与呼叫控制分离。
- 呼叫处理与承载分离。
- <u>**呼叫控制与媒体控制分离。**</u>（控制与控制分离）

## *SDN

与传统IP网络的区别——<u>控制平面、数据转发平面分离</u>。特征：集中控制、开放接口、网络虚拟化。

SDN的核心诉求：让软件应用参与到网络控制中并起到主导作用，而不是让各种固定模式的协议来控制网络。

转发、控制、应用的三层架构：

* 转发层（基础设施层）：由转发设备组成。（流表处理、数据转发）
* 控制层：由SDN控制软件组成，与转发层可通过OpenFlow协议通信。（设备管理和拓扑、流表控制和下发）
* 应用层：不同的应用逻辑通过控制层开放的API管理能力控制设备的报文转发功能。（网络资源统一管理）

南北向接口：

- 北向接口，为应用提供编程接口。暂时没有标准化。
- 南向接口，设备控制信令，控制设备的转发行为。可用标准化OpenFlow协议。

Openflow基本概念：<u>将转发面设备抽象为一个由多级流表（Flow Table）驱动的转发模型。</u>

- 转发面抽象成多级流水线，每个节拍匹配关键字、操作指令集。
- 转发面的行为：根据转发表和报文头决定下一跳及新的报文格式。

流表的作用、与路由表的区别：

* <u>流表是OpenFlow对网络设备的数据转发功能的抽象</u>，表项包括了网络各个层次的配置信息。
* 传统的路由表无法更改、不可编程。

![image-20230603214915724](https://s2.loli.net/2023/06/03/8v7Ya4N6fMUsXcJ.png)

# 抽象题目收集

欢迎来到经典环节。

打*就是完全闻所未闻，并觉得必不会考的东西。

- 问题:交换单元的端口类型有两种，即入线端口和出线端口。（×）

  ![image-20230607180057605](https://raw.githubusercontent.com/mushroom323/notes-imgs/main/image-20230607180057605.png)

  > 如图，还要控制端、状态端等。

- *问题:交换机的接口类型中，属于模拟用户接口是
  - A:Z接口
    B:Q3接口
    C:PCM中继接口
    D:数字中继A接口
  - 答案: 【Z接口】

- 问题:4条低速的2048kbit/s PCM线路复用为一条高速PCM线路后，每帧有多少个时隙

  - A:16
    B:64
    C:128
    D:256

  - 答案: 【128】

    > 低速2048kbit/s的PCM线路就是标准PCM线路，每帧有32个时隙，复用之后即乘以对应线路数即可。

- 问题:PCM中继电路的每个时隙速率为

  - A:64kb/s
    B:2Mb/s
    C:128kb/s
    D:256kb/s

  - 答案: 【64kb/s】

    > 我记得PSTN最高速率好像是56kb/s？PSTN用的不是PCM吗，为啥PCM都64kb/s了，PSTN还是那么低？
    >
    > 还是说PCM只在交换的时候用？
    >
    > ![image-20230607182306715](https://raw.githubusercontent.com/mushroom323/notes-imgs/main/image-20230607182306715.png)
    >
    > 答案是要腾一位用于校验！
    >
    > 给ziang磕头。

- 问题:程控交换设备通过TST网络进行主被叫用户的话音交换，每一个用户的带宽为
  - A:固定速率64kb/s
    B:峰值速率64kb/s
    C:平均速率64kb/s
    D:固定速率8kb/s
  - 答案: 【固定速率64kb/s】

- *问题:程控交换机的运行软件不包括哪些功能
  
  - A:呼叫处理
    B:系统的安全运行与保护
    C:网络管理
    D:机房规划部署
  - 答案: 【机房规划部署】
  
- 问题:以下哪项不属于局数据的是

  - A:呼叫复原方式
    B:禁止呼入权限
    C:本地号码编排计划
    D:出局路由表

  - 答案: 【禁止呼入权限】

    > ![image-20230607183656744](https://raw.githubusercontent.com/mushroom323/notes-imgs/main/image-20230607183656744.png)
    >
    > ![image-20230607183733107](https://raw.githubusercontent.com/mushroom323/notes-imgs/main/image-20230607183733107.png)
    >
    > 复原方式还真是局数据...。

- 问题:每个交换机中都包括局数据和用户数据，在进行固网智能化改造中，为了方便用户业务的提供，会将什么数据进行集中
  - A:用户数据
    B:局数据
    C:系统数据
    D:中继数据
  - 答案: 【用户数据】

- *问题:在会议电话中，为了实现用户A能同时听到用户B、用户C的声音，要求交换设备做到

  - A:交换网络支持多对一的交换，将用户B、用户C的语音直接交换给用户A
    B:交换网络支持一对多的交换，将用户A的语音交换给用户B和用户C
    C:用户B与用户C的PCM语音直接相加后送给用户A
    D:用户B与用户C的PCM语音先变换为线性可加的数据，再相加，再逆变换后送给用户A

  - 答案: 【用户B与用户C的PCM语音先变换为线性可加的数据，再相加，再逆变换后送给用户A】

    > 也就是说会议电话中，交换设备不支持多对一/一对多的交换，而是采用了码分多址的方式来实现同时听到的效果。

- *问题:如果被叫用户开通了呼叫前转业务，可以在通话状态下进行操作，通过拍插簧听二次拨号音，输入第三人的号码，将主叫与第三人接通。关于这个过程描述正确的
  - A:在这个时候拍插簧，是为了重新申请收号器
    B:收号器这个资源不需要申请，拍插簧也无法申请
    C:拍插簧相当于挂机动作
    D:不需要拍插簧，直接拨打第三人的号码就可以
  - 答案: 【在这个时候拍插簧，是为了重新申请收号器】

- 问题:去话分析针对的数据是
  - A:主叫用户数据
    B:被叫用户数据
    C:主叫拨打的电话号码
    D:被叫的当前状态
  - 答案: 【主叫用户数据】

- 问题:遇忙呼叫转移发生在哪个阶段
  - A:去话分析
    B:号码分析
    C:来话分析
    D:需求分析
  - 答案: 【来话分析】
- 问题:下列哪项不属于周期级程序
  - A:摘机检测
    B:DTMF按钮号码识别
    C:挂机检测
    D:话路的驱动
  - 答案: 【话路的驱动】

- 问题:关于电话通信的描述，正确的是

  - A:两个电话机之间实现语音通信，必须经过交换设备
    B:两个电话机之间实现语音通信，可以不经过交换设备
    C:光纤入户的普及提高了上网速度，但家里连接光猫的电话机通话所用电源仍然由电信运营公司提供
    D:采用脉冲式的拨号电路，对脉冲速度没有规定，只要送入脉冲给交换机就可以

  - 答案: 【两个电话机之间实现语音通信，可以不经过交换设备】

    > 两个杯子一根线，总之就是可以不经过交换设备。

- 问题:交换机的系统结构中，描述正确的是
  - A:用户模块中没有控制子系统的部件，只有话路子系统的部件
    B:用户模块与远端用户模块的区别是用户模块配置了数字中继接口
    C:用户级的交换网络要集中话务，所以集中比必须为1：1
    D:控制子系统的中央处理机可以外接磁盘机、磁带机等存储设备
  - 答案: 【控制子系统的中央处理机可以外接磁盘机、磁带机等存储设备】

- 问题:用户电路的基本功能描述正确的有哪些

  - A:在通话时，通过馈电电路提供交流馈电电流
    B:用户电路保证上万伏的高压可以箝位到0V 与 -48V 之间
    C:编译码实现A/D与D/A转换
    D:测试针对的是交换设备内线测试，无法对外线进行测试

  - 答案: 【编译码实现A/D与D/A转换】

    > 馈电提供的是直流馈电电流。

- 问题:描述不正确的是
  - A:故障级的程序由硬件中断触发启动，优先级最高
    B:电话号码的拨打属于外设事件，处理这个事件需要时钟中断程序
    C:用户在营业厅开通呼叫转移业务，需要修改交换机中的用户数据，由交换机中的周期级程序负责修改
    D:交换机A通过中继线连接了新开通的交换机B，两个交换机都要修改相关的局数据，由交换机中的基本级程序负责修改
  - 答案: 【用户在营业厅开通呼叫转移业务，需要修改交换机中的用户数据，由交换机中的周期级程序负责修改】

- 问题:M40交换机的交换单元采用什么技术
  - A:共享总线
    B:共享存储器
    C:共享背板
    D:共享处理器
  - 答案: 【共享存储器】

- 问题:M40交换机中负责从不同线路的帧格式中提出数据净荷的部件是
  - A:路由部件
    B:交换单元
    C:线路卡
    D:路由查找部件
  - 答案: 【线路卡】

- 问题:下面关于B-ISDN业务特点的描述，哪个是**错误**的

  - A:B-ISDN需要同时支持不同速率的业务
    B:B-ISDN需要同时支持实时和非实时的业务
    C:B-ISDN需要同时支持模拟和数字的业务
    D:B-ISDN中不同业务的QoS可以不同

  - 答案: 【B-ISDN需要同时支持模拟和数字的业务】

    > ISDN：综合业务数字网

-  问题:ATM信元结构是
  - A:固定53个字节长度
    B:可变长度的
    C:48个字节
    D:可变长度最大为53个字节
  - 答案: 【固定53个字节长度】

- 问题:在组成信元头的域中，VPI+VCI项构成了ATM的
  - A:流量控制信息
    B:路由选择信息
    C:信头差错控制信息
    D:净荷标识信息
  - 答案: 【路由选择信息】

- 问题:ATM交换机的基本功能不包含下述的哪个功能

  - A:为信元选路
    B:信头翻译与转换
    C:将用户数据分割成信元
    D:VPI/VCI分配
  - 答案: 【将用户数据分割成信元】

- 问题:关于标记交换路径LSP的描述，正确的是

  - A:相同的前转等价类FEC具有相同的LSP
    B:一个LSP对应一个呼叫
    C:LSP由唯一的一个标记label标识
    D:具有相同目的IP地址的分组具有相同的LSP
    E:相同的LSP具有相同的标记
    F:在同一LSP路径上传输的数据分组可以有不同的QoS参数

  - 答案: 【相同的前转等价类FEC具有相同的LSP;相同的LSP具有相同的标记】

    > 在同一LSP路径上传输的数据分组可以有不同的QoS参数（×）

- 问题:MPLS网络中，标记交换路由器LSR对一个打标分组进行标记置换时，可以不依赖FLIB中的哪个信息
  - A:输入端口
    B:输入标记
    C:输出端口
    D:目的IP地址前缀
    E:输出标记
  - 答案: 【目的IP地址前缀】

- 问题:MPLS采用面向连接的交换方式，下面的描述中，哪个是正确的

  - A:MPLS的面向连接和IP网络中的TCP面向连接属于同一概念。
    B:MPLS与ATM相似， 都具有 路由选择与数据转发 分开进行的特点，都需要为每一次通信业务建立一个新的连接。
    C:MPLS交换与ATM交换的相同点是它们都采用面向连接的方式，区别是MPLS是永久连接的，ATM是按需连接的。
    D:MPLS使用LDP协议建立LSP连接。
    E:MPLS中的连接是物理连接，ATM中的连接是虚连接。

  - 答案: 【MPLS使用LDP协议建立LSP连接。】

    > :MPLS与ATM相似， 都具有 路由选择与数据转发 分开进行的特点，都需要为每一次通信业务建立一个新的连接。（×）

- 问题:路由器采用最长匹配原则进行IP包转发，因此，不能达到线速转发。（×）

- 问题:MPLS标记边界路由器LER需要处理IP分组头的IP地址，而标记交换路由器LSR只处理标记部分，不处理IP分组头。（×）

  > 也就是说没把FEC算进IP分组头

- 问题:标记交换路由器LSR只处理打标分组，并进行标记置换，不处理普通IP分组 。（×）

- 问题:局间信令在中继线路上传输，用于协商通话需要的媒体资源。（√）

- 问题:信令就是交换设备之间的呼叫接续协议。（√）

  > “就是”，但是是对的。

- 问题:MTP3是7号信令的信令网功能级，为了路由信令消息，MTP3使用信令点编码来进行消息寻址和路由。（√）
- 问题:交换设备中的呼叫处理与信令处理这两大软件模块最好设计为松耦合，这样在进行信令模块替换时可以做到方便灵活。（√）
- 问题:SIP与七号信令进行转换时，需要将invite消息中SDP的媒体端口号取出，放入七号的IAM消息。（√）
- 问题:随路信令在话路中传送，用户拨打电话银行时输入的帐号密码就是在随路信令里传送的。（×）
- 问题:共路信令提供了高速信令传输通道，用户拨打电话银行时输入的帐号密码在这个通道中传输（×）
- 问题:MTP1是七号信令的数据链路级，它起到了物理层的作用，通常的传输带宽为64kb/s，这是由局间专用的物理线路来提供的（×）
- 问题:双音频的DTMF信号、直流脉冲信号、FSK的来电显示信号和七号系统的IAM信号都属于模拟用户信令（×）
- 问题:TUP信令仅用于支持局间电话呼叫接续，用户的业务是不需要信令进行支持的（×）

- 问题:SIP是IETF制定的IP电话信令协议，只能用于语音通信（×）
- 问题:Sip信令在进行SDP协商时，会确定双方的音视频编码、RTP端口等信息，而接收媒体流的IP地址不用协商（×）

- 问题:GSM系统中，如下的哪个功能不会在MSC执行
  - A:呼叫控制
    B:信道功率控制
    C:切换控制
    D:位置管理
    E:漫游控制
    F:话音编码
  - 答案: 【信道功率控制;
    话音编码】

- 问题:GPRS系统空中接口通过哪种方法实现对变速率数据的传输
  - A:分组交换
    B:动态时隙分配
    C:码分复用
    D:多时隙捆绑
  - 答案: 【多时隙捆绑】

- 问题:GPRS系统中，MS进行数据通信需要建立GTP隧道，GTP隧道建立是在哪个过程中完成的
  - A:移动台开机
    B:移动台attach附着入网
    C:网络发起GPRS寻呼
    D:PDP上下文激活
  - 答案: 【PDP上下文激活】

- 问题:3GPP Release4&5 核心网中， MSC服务器、SGSN、HLR等网元设备之间采用什么方式通信
  - A:ATM信元交换
    B:PCM电路交换
    C:IP交换
    D:CDMA交换
  - 答案: 【IP交换】

- 问题:LTE采用扁平化网络架构，WCDMA网络中原RNC的功能主要由 哪个网元设备来承担
  - A:eNodeB
    B:MME
    C:SGW
    D:PGW
    E:HSS
  - 答案: 【eNodeB】

- 问题:LTE网络中， 移动终端UE的IP地址由哪个网元设备来分配
  - A:eNodeB
    B:MME
    C:SGW
    D:PGW
    E:HSS
  - 答案: 【PGW】

- 问题:LTE网络的一个重要特点是控制平面与用户平面分离，只负责控制信息处理的网元是
  - A:eNodeB
    B:MME
    C:SGW
    D:PGW
  - 答案: 【MME】

- 问题:GSM系统中，移动台MS1呼叫MS2，关于呼叫过程的描述，哪个是不正确的
  - A:MS1与MS2如果在同一个小区，可以直接进行信令交互，建立业务信道
    B:MS1通过接入请求消息，获得其专有信令信道，并在该信道上发送呼叫消息
    C:MS使用不同的信道来传输呼叫控制消息和话音信息
    D:为找到MS2，MSC向全网广播寻呼消息
    E:空闲的MS2接收到寻呼消息，识别出其IMSI码一致后，发送应答响应
  - 答案: 【MS1与MS2如果在同一个小区，可以直接进行信令交互，建立业务信道;
    为找到MS2，MSC向全网广播寻呼消息】

- 问题:GSM系统中，MSRN是在每次呼叫移动用户时，为了使网络再次选择路由，根据HLR的请求，由VLR临时分配给移动用户的一个号码，该号码在接续完成后将释放给其他用户使用。（√）
- 问题:移动终端的IMSI号是移动系统内部的识别号，与用户手机号码MSISDN存在一一对应的关系 。（√）

- 问题:WCDMA是GSM升级版，因此，其空中接口也是基于时分多址的。（×）

- 问题:WCDMA和GPRS只是空中接口标准不同，核心网设备可以互联互通。（√）

- ![image-20230611151828700](https://raw.githubusercontent.com/mushroom323/notes-imgs/main/image-20230611151828700.png)

  > 题都已经这样了.jpg

- 问题:LTE网络用户面上，eNodeB负责将空中接口PDCP格式的用户数据包进行GTP封装，采用隧道方式传送到SGW，进而送到PGW。（√）

- 问题:LTE网络中， 4G用户所有与业务相关的信息(例如相关签约信息及4G位置信息)都存贮在MME中。（×）

  > 还有HSS
