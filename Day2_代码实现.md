# data structure learning_Day2 代码实现

>  本人学习视频用的是青岛大学-王卓老师的，也在这里献上
>  视频链接：https://www.bilibili.com/video/BV1nJ411V7bd
>  数据结构与算法基础（青岛大学-王卓）


[TOC]

实现复数运算：
$$
z=\frac{(8+6i)*(4+3i)}{(8+6i)*(4+3i)}
$$


```C
#include<stdio.h>
#include<stdlib.h>

//z=(8+6i)(4+3i)/((8+6i)+(4+3i))

typedef struct
{
	float realpart;  /* 实部 */
    float imagpart;  /* 虚部 */
} Complex;           /* 定义复数抽象类型 */


void assign(Complex *A, float real, float imag);  /* 赋值 */
void add(Complex *C, Complex A, Complex B);  /* A + B */
void minus(Complex *C, Complex A, Complex B);  /* A - B */
void multiply(Complex *C, Complex A, Complex B);  /* A * B */
void divide(Complex *C, Complex A, Complex B);  /* A / B */

void main()
{
    Complex z1, z2, z3, z4, z;
    assign(&z1, 8.0, 6.0);
    assign(&z2, 4.0, 3.0);
    multiply(&z3, z1, z2);
    add(&z4, z1, z2);
    divide(&z, z3, z4);
    if (z.realpart == 0 && z.imagpart != 0) printf("%.1fi\n",z.imagpart);
    else if (z.imagpart == 0) printf("%.1f\n",z.realpart);
    else if (z.imagpart > 0) printf("%.1f+%.1fi\n", z.realpart, z.imagpart);
    else if (z.imagpart < 0) printf("%.1f%.1fi\n", z.realpart, z.imagpart);
}

void assign(Complex *A, float real, float imag)
{
    A->realpart = real;
    A->imagpart = imag;
}

void add(Complex *C, Complex A, Complex B)  /* C = A + B */
{
    C->realpart = A.realpart + B.realpart;  /* 实部相加 */
    C->imagpart = A.imagpart + B.imagpart;  /* 虚部相加 */
}

void minus(Complex *C, Complex A, Complex B)
{
    C->realpart = A.realpart - B.realpart;  /* 实部相减 */
    C->imagpart = A.imagpart - B.imagpart;  /* 虚部相减 */
}

void multiply(Complex *C, Complex A, Complex B)
{
    C->realpart = A.realpart * B.realpart - A.imagpart * B.imagpart;
    C->imagpart = A.imagpart * B.realpart + A.realpart * B.imagpart;
}

void divide(Complex *C, Complex A, Complex B)
{
    float deno = B.realpart * B.realpart + B.imagpart * B.imagpart;
    if (deno != 0)
    {
        C->realpart = (A.realpart * B.realpart + A.imagpart * B.imagpart) / deno;
        C->imagpart = (A.imagpart * B.realpart - A.realpart * B.imagpart) / deno;
    }
    else
    {
        printf("Mathenmatical Error!");
        exit(0);
    }
}
```

