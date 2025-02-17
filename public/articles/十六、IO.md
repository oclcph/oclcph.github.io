---
title: I/O系统
abstract: 计组第十六章笔记
category: 计算机组成原理
---

# I/O

**外设：**外围设备，连接输入输出模块

> 不能把外设直接连到系统总线，外设速度和存储器、处理器处理速度不同，字节长度不同

## I/O模块

连接外设、计算机内部系统之间的桥梁，通过系统总线和存储器连接，通过专用数据线和外设连接。

### 功能

1. 处理器通信
   1. 命令译码：通过控制总线传递
   2. 数据：通过数据总线交换
   3. 状态报告：外设速度慢，需要知道I/O模块状态
   4. 地址识别：I/O模块必须识别他所控制的每个外设的唯一地址
2. 设备通信：命令、状态信息、数据
3. 数据缓冲：不同外设数据传送速度不同
4. 控制和定时
5. 检错（设备报告的机械、电路故障或传输过程中数据位的变化）

### 结构

<img src="C:\Users\ocl\AppData\Roaming\Typora\typora-user-images\image-20241225132603981.png" alt="image-20241225132603981" style="zoom:50%;" />

**外部接口类型：**并行接口、串行接口

> 并行接口每次同时传送多位数据，当传输速度和总线长度增加时，总线的时钟频率会受到限制

### I/O操作技术

编程式IO、中断式、直接存储器读取（i/O模块和主存直接交换数据，不需要处理器）

#### 编程式I/O

处理器发送一条I/O命令直到I/O模块执行结束后才继续工作

**I/O命令：**执行I/O操作时处理器发送一个指定具体I/O模块和外设的地址

#### 中断驱动式I/O

**响应优先级**、**处理优先级**

#### DMA

处理器向DMA发送命令后，DMA直接访问主存，传输完成后向处理器发送中断

**内存访问的方法**：

1. CPU停止法，DMA访问主存时cpu不访问主存
2. 周期窃取，DMA和CPU周期性交替访问主存
3. 交替分时访问，将内存时间分成等时，同一时段内CPU和DMA分别访问
