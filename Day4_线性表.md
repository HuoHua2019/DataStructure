# data structure learning_Day4

>  本人学习视频用的是青岛大学-王卓老师的，也在这里献上
>  视频链接：https://www.bilibili.com/video/BV1nJ411V7bd
>  数据结构与算法基础（青岛大学-王卓）


[TOC]

## 线性表

### 1.线性表的定义和特点

**线性表**时具有相同特性的数据元素的一个有限序列

- 线性表：由n(n $\geq$ 0)个数据元素（结点）$a_1,a_2,...a_n$组成的**有限序列**
  - 其中数据元素的个数n定义为表的长度
  - 当n=0时称为**空表**
  - 将非空的线性表(n>0)记作：（$a_1,a_2,...a_n$）
  - 这里的数据元素$a_i(1\leq i\leq n)$只是一个抽象的符号，其具体含义在不同的情况下可以不同

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011164218.png" alt="msedge_o26DWZzsU2" style="zoom:80%;" />

同一线性表中的元素必定具有相同特性，数据元素之间的关系式线性关系

<br>

### 2.线性表的逻辑特征

- 在非空的线性表，有且仅有一个开始结点$a_1$，它没有直接前趋，而仅有一个直接后继$a_2$；
- 有且仅有一个终端结点$a_n$，它没有直接后继，而仅有一个直接前趋$a_{n-1}$；
- 其余的内部结点$a_i(2\leq i\leq n-1)$都有且仅有一个直接前趋$a_{i-1}$和一个直接后继$a_{i+1}$

线性表是一种典型的线性结构

<br>

### 3.线性表的类型定义

抽象数据类型线性表的定义如下“

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011182224.png" alt="msedge_fAc11iE2y1" style="zoom:67%;" />

#### 基本操作

- **InitList(&L)**

  - 操作结果：构造一个空的线性表L

- **DestoryList(&L)**

  - 初始条件：线性表L已经存在
  - 操作结果：销毁线性表L

- **ClearList(&L)**

  - 初始条件：线性表L已经存在
  - 操作结果：将线性表L置为空表

- **ListEmpty(L)**

  - 初始条件：线性表L已经存在
  - 操作结果：若线性表L为空表，则返回TURE；否则返回FALSE

- **ListLength(L)**

  - 初始条件：线性表L已经存在
  - 操作结果：返回线性表L中的数据元素的个数

- **GetElem(L, i, &e)**

  - 初始条件：线性表L已经存在，1 $\leq$ i $\leq$ ListLength(L)
  - 操作结果：用e返回线性表L中第i个数据元素的值

- **LocateElem(L, e, compare())**

  - 初始条件：线性表L已经存在，compare()是数据元素判定函数
  - 操作结果：返回L中第1个与e满足compare()的数据元素的位序。若这样的数据元素不存在则返回值为0

- **PriorElem(L, cur_e, &pre_e)**

  - 初始条件：线性表已经存在
  - 操作结果：若cur_e是L的数据元素且不是第一个，则用pre_e返回它的前驱，否则操作失败，pre_e无意义

- **NextElem(L, cur_e, &next_e)**

  - 初始条件：线性表已经存在
  - 操作结果：若cur_e是L的数据元素且不是第一个，则用next_e返回它的前驱，否则操作失败，next_e无意义

- **ListInsert(&L, i, e)**

  - 初始条件：线性表L已经存在，1 $\leq$ i $\leq$ ListLengeh(L)+1
  - 操作结果：在L的第i个位置之前插入新的数据元素e，L的长度加一

  <div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011184013.png" alt="msedge_DPqY1clCVM" style="zoom:67%;" />

- **ListDelete(&L, i, &e)**

  - 初始条件：线性表L已经存在，1 $\leq$ i $\leq$ ListLengeh(L)
  - 操作结果：删除L的第i个数据元素，并用e返回其值，L的长度减一

  <div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011184415.png" alt="msedge_uJa9a7yKca" style="zoom:67%;" />

- **ListTraverse(&L, visited())**

  - 初始条件：线性表L已经存在
  - 操作结果：依次对线性表中每个元素调用visited()

<br>

### 4.线性表的存储结构

在计算机内，线性表有两种基本存储结构：**顺序存储结构**和**链式存储结构**

顺序存储定义：把逻辑上相邻的数据元素存储在物理上相邻的存储单元中的存储结构

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011190903.png" alt="msedge_LjSntGASHw"  />

线性表的第1个数据元素$a_1$的存储位置，称作线性表的**起始位置**或**基地址**

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011191200.png" alt="msedge_pKuchROOX0" style="zoom:67%;" />

<br>

### 5.顺序表中元素存储位置的计算

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201011191621.png" alt="msedge_jMmlxwAsEG" style="zoom:67%;" />

假设线性表的每个元素需占n个存储单元，则第i+1个数据元素的存储位置和第i个数据元素的存储位置之间满足关系：$LOC(a_{i+1})=LOC(a_i)+n$

由此，所有数据元素的存储位置均可由第一个数据元素的存储位置得到：$LOC(a_i)=LOC(a_1)+(i-1)*n$，运算数量级是O(1)，这种存取叫做随机存取

<br>

### 6.线性表顺序存储表示

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012124859.png" alt="msedge_y3ktmT9HuT" style="zoom:67%;" />

顺序表的特点：以物理位置相邻表示逻辑关系。任一元素均可以随机存取。

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012125057.png" alt="msedge_fewil5phlm" style="zoom:67%;" />用一维数组表示顺序表

线性表长可变（删除）但数组长度不可动态定义<img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012125328.png" alt="msedge_OlbDQDOH9t" style="zoom:67%;" />

因而用一变量表示顺序表的长度属性

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012125507.png" alt="msedge_IE2aGFmQO4" style="zoom: 67%;" />

<br>

#### 多项式的顺序存储结构类型定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012125928.png" alt="msedge_yFuRNGVDD3" style="zoom:67%;" />

<br>

#### 图书表的熟悉怒存储结构类型定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012131413.png" alt="msedge_6wmBzvtQRO" style="zoom: 80%;" />

<br>

### 7.类C语言有关操作

#### （1）元素类型说明

1）顺序表类型定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012130448.png" alt="msedge_W1OGpMHwgs" style="zoom:67%;" />

2）数组定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012171013.png" alt="msedge_GUVbvUehZp"  style="zoom:67%;"/>


对于数组动态分配空间：

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012171310.png" alt="msedge_GUVbvUehZp" style="zoom:67%;" />

<br>

#### （2）C语言的内存动态分配

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012181357.png" alt="msedge_n71EXOAiLx" style="zoom:80%;" />

<br>

#### （3）C++的动态存储分配

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012183258.png" alt="msedge_A0Yl1epx7N" style="zoom: 80%;" />

