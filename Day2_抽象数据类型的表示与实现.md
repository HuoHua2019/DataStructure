# data structure learning_Day2

>  本人学习视频用的是青岛大学-王卓老师的，也在这里献上
>  视频链接：https://www.bilibili.com/video/BV1nJ411V7bd
>  数据结构与算法基础（青岛大学-王卓）


[TOC]

## 抽象数据类型的表示与实现

一个问题抽象为一个抽象数据类型后，仅是形式上的抽象定义，还没有达到问题解决的目的，要实现这个目标，就要把抽象的变成具体的，即抽象数据类型在计算机上实现，变为一个能用的具体的数据类型。

<img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201007200405.png" alt="msedge_8JbVqU8dDB" style="zoom:67%;" />

<br>

### 抽象数据类型如何实现

- 抽象数据类型可以通过固有的数据类型（如整形、实型、字符型等）来表示和实现
  - 即利用处理器中已存在的数据类型来说明新的数据结构，用已经实现的操作来组合新的操作

<br>

#### 用C语言真正实现抽象数据类型的定义

例如：抽象数据类型“复数”的实现

```C
typedef struct
{
	float realpart;  /* 实部 */
    float imagpart;  /* 虚部 */
} Complex            /* 定义复数抽象类型 */

void assign(Complex *A, float real, float imag);  /* 赋值 */
void add(Complex *A, float real, float imag);  /* A + B */
void minus(Complex *A, float real, float imag);  /* A - B */
void multiply(Complex *A, float real, float imag);  /* A * B */
void divide(Complex *A, float real, float imag);  /* A / B */

void assign(Complex *A, float real, float imag)
{
    A->realpart = real;
    A->imagpart = imag;
}

void add(Complex *C, float A, float B)  /* C = A + B */
{
    C->realpart = A.realpart + B.realpart;  /* 实部相加 */
    C->imagpart = A.imagpart + B.imagpart;  /* 虚部相加 */
}
......
```

<br>

*另外关于视频末尾的代码实现，下面是我的方案，望抛砖引玉*

[Day2_代码实现](Day2_代码实现.md)

