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

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119161543.png" alt="img" style="zoom: 67%;float:left;" />


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

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119160620.png" alt="img" style="zoom:67%;float:left;" />


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

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119160655.png" alt="img" style="zoom:67%;float:left;" />

- **ListDelete(&L, i, &e)**

  - 初始条件：线性表L已经存在，1 $\leq$ i $\leq$ ListLengeh(L)
  - 操作结果：删除L的第i个数据元素，并用e返回其值，L的长度减一

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119160729.png" alt="img" style="zoom:67%;float:left;" />

- **ListTraverse(&L, visited())**

  - 初始条件：线性表L已经存在
  - 操作结果：依次对线性表中每个元素调用visited()

<br>

### 4.线性表的存储结构

在计算机内，线性表有两种基本存储结构：**顺序存储结构**和**链式存储结构**

顺序存储定义：把逻辑上相邻的数据元素存储在物理上相邻的存储单元中的存储结构

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119160746.png" alt="img" style="zoom:67%;float:left;" />


线性表的第1个数据元素$a_1$的存储位置，称作线性表的**起始位置**或**基地址**

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119161259.png" alt="image-20210119161258096" style="zoom:50%;float:left;" />

<br>

### 5.顺序表中元素存储位置的计算

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119161010.png" alt="img" style="zoom:67%;float:left;" />


假设线性表的每个元素需占n个存储单元，则第i+1个数据元素的存储位置和第i个数据元素的存储位置之间满足关系：$LOC(a_{i+1})=LOC(a_i)+n$

由此，所有数据元素的存储位置均可由第一个数据元素的存储位置得到：$LOC(a_i)=LOC(a_1)+(i-1)*n$，运算数量级是O(1)，这种存取叫做随机存取

<br>

### 6.线性表顺序存储表示 

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119161337.png" alt="img" style="zoom:67%;float:left;" />


顺序表的特点：以物理位置相邻表示逻辑关系。任一元素均可以随机存取。

**用一维数组表示顺序表：**

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119161427.png" alt="img" style="zoom:67%;float:left;" />

线性表长可变（删除）但数组长度不可动态定义

<img src="https://github.com/HuoHua2019/Img/blob/master/img/20201011191200.png?raw=true" alt="msedge_OlbDQDOH9t" style="zoom:67%;float:left;" />

因而用一变量表示顺序表的长度属性

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162220.png" alt="image-20210119162219208" style="zoom:67%;float:left;" />

<br>

#### 多项式的顺序存储结构类型定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012125928.png" alt="msedge_yFuRNGVDD3" style="zoom:67%;" />
<br>

#### 图书表的顺序存储结构类型定义

<div align="left"><img src="https://cdn.jsdelivr.net/gh/Huohua2019/Img/img/20201012131413.png" alt="msedge_6wmBzvtQRO" style="zoom: 80%;" />

<br>

### 7.类C语言有关操作

#### （1）元素类型说明

1）顺序表类型定义

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162330.png" alt="img" style="zoom:67%;float:left;" />

2）数组定义

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162405.png" alt="img" style="zoom:67%;float:left;" />

对于数组动态分配空间：

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162448.png" alt="img" style="zoom:67%;float:left;" />

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119163254.png" alt="image-20210119163253070" style="zoom:67%;float:left;" />

<br>

#### （2）C语言的内存动态分配

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162516.png" alt="img" style="zoom:67%;float:left;" />

对于上图的 **ElemType**可以是类型也可以是变量

<br>

#### *（3）C++的动态存储分配

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119162623.png" alt="img" style="zoom:67%;float:left;" />

<br>

#### *（4）C++中的参数传递

- 函数调用时传送给形参表的实参必须与形参三个一致
  - 类型、个数、顺序
- 参数传递有两种方式
  - 传值方式（参数为整形、实型、字符型等）
  - 传地址
    - 参数为指针变量
    - 参数为引用类型
    - 参数为数组名

<br>

**1）传值方式**

- 把实参的值传送给函数局部工作区相应的副本中，函数使用这个副本执行必要的功能。函数修改的是副本的值，实参的值不变

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119164721.png" alt="image-20210119164719726" style="zoom:67%;float:left;" />

**2）传地址方式**

**--指针变量作参数**

- 形参变化影响实参

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119165817.png" alt="image-20210119165816425" style="zoom:67%;float:left;" />

  改变了a,b地址所对应的值，即改变了a,b的值

- *形参变化不影响实参*

  ![image-20210119170100205](https://gitee.com/Huohua2020/Img/raw/master/img/20210119170101.png)

  仅交换了m,n所指向的内容，并不会改变a,b的值

**--数组名作参数**

- 传递的是数组的首地址

- 对形参数组所做的任何改变都将反映到实参数组中

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119193156.png" alt="image-20210119193155083" style="zoom:67%;float:left;" />

<br>

**--引用类型作参数**

什么时引用？

引用：它用来给一个对象提供一个替代的名字。

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119195345.png" alt="image-20210119195344252" style="zoom:67%;float:left;" />

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119195716.png" alt="image-20210119195715284" style="zoom:67%;float:left;" />

（1）传递引用给函数与传递指针的效果是一样的，**形参变化实参也发生变化**。

（2）引用类型作形参，在内存中并没有产生实参的副本，它**直接对实参操作**；而一般变量作参数，形参与实参就占用不同的存储单元，所以**形参变量的值是实参变量的副本**。因此，当**参数传递的数据量较大**时，用引用比用一般变量传递参数的时间和空间效率都好。

（3）指针参数虽然也能达到与使用引用的效果，但在被调函数中需要重复使用“*指针变量名”的形式进行运算，这很容易产生错误且程序的阅读性较差；另一方面，在主调函数的调用点处，必须用变量的地址作为实参。

<br>

### 8.线性表的顺序实现

![image-20210119200945099](https://gitee.com/Huohua2020/Img/raw/master/img/20210119200946.png)

 <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119201154.png" alt="image-20210119201153312" style="zoom:50%;float:left;" />

















<br>

#### （1）顺序表基本操作的实现

1. 线性表L的初始化（参数用引用）

```c++
Status InitList_Sq(SqList &L) {		//构造一个空的顺序表L
	L.elem = new ElemType[MAXSIZE];	//为顺序表分配空间
	if (!L.elem) exit(OVERFLOW);		//存储分配失败
	L.length = 0;										//空表长度为0
	return OK;
}
```

2. 销毁线性表L

```c++
void DestroyList(SqList &L) {
	if(L.elem) delete L.elem;		//释放存储空间
}
```

3. 清空线性表L

```c++
void ClearList(SqList &L) {
	L.length = 0;								//将线性表的长度置为0
}
```

4. 求线性的长度

```c++
int GetLength(SqList L) {
return (L.length);
}
```

5. 判断线性表L是否为空

```c++
int IsEmpty(SqList L) {
	if (L.length == 0) return 1;
	else return 0;
}
```

6. 顺序表的取值（根据位置i获取相应位置数据元素的内容）

```c++
int GetElem(SqList L, int i, ElemType &e) {
	if (i<1 || i>L.length) return ERROR;
		//判断i值是否合理，若不合理，返回 ERROR e= Elem[i-1];
	e = L.elem[i-1];	//第i-1的单元存储着第i个数据
	return oK;
}
```

7. **顺序表的查找**

- 在线性表中查找与指定值e归同的数据元素的位置
- 从表的一端开始，逐个进行记录的关键字和给定值的比较。找到，返回该元素的位置序号，未找到，返回0。

```c++
int LocateElem(SqList L, ElemType e) {
//在线性表L中查找值为e的数据元素，返回其序号（是第几个元素）
	for（i=0; i<L.length; i++)
		if (L.elem[i] == e) return i+1;	//查找成功，返回序号
		return0;	//查找失败，返回0
}
```

顺序表的查找算法分析：

平均查找长度ASL(Average Search Length)：

- ​	为确定记录在表中的位置，需要与给定值进行比较的关键字的个数的期望值叫做查找算法的平均查找长度。

  对含有n个记录的表，查找成功时：
  $$
  ASL=\sum_{i=1}^{n}P_iC_i\\
  C_i：找到第i个记录需比较的次数。\\
  P_i：第i个记录杯查找的概率
  $$

8. **顺序表的插入**

```c++
Status ListInsert_Sq(SqList &L, init i, ElemType e) {
	if (i < 1 || i > L.length+1) return ERROR;	//i值不合法
	if (L.length == MAXSIZE) return ERROR;	//当前存储空间已满
	for (j = L.length-1; j >= i-1; j--)
		L.elem[j+1] = L.elem[j];	//插入位置及之后的元素后移
	L.elem[i-1] = e;						//将新元素e放入第i个位置
	L.length++;									//表长增1
	return OK;
}
```

9. **顺序表的删除**

```c++
Status ListDelete_Sq(SqList &L, init i) {
	if (i < 1 || i > L.length) return ERROR;	//i值不合法
	if (L.length == MAXSIZE) return ERROR;	//当前存储空间已满
	for (j = i; j<= L.length-1; j++)
		L.elem[j-1] = L.elem[j];	//插入位置及之后的元素后移
	L.length--;									//表长增1
	return OK;
}
```

<br>

### 9.线性表的链式表示方法

- 链式存储结构
  - 结点在存储器中的位置是任意的，即逻辑上相邻的数据元素在物理上不一定相邻
- 线性表的链式表示又称为**非顺序映像**或**链式映像**。
- 用一组**物理位置任意的存储单元**来存放线性表的数据元素。
- 这组存储单元既可以是**连续**的，也可以是**不连续**的，甚至是零散分布在内存中的任意位置上的。
- 链表中元素的**逻辑次序和物理次序不一定相同**。

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119222502.png" alt="image-20210119222500320" style="zoom:67%;float=left;" />

各结点由两个域组成：

**数据域**：存储元素数值数据

**指针域**：存储直接后继结点的存储位置

- 与链式存储有关的术语

1. 结点：数据元素的存储映像。由数据域和指针域两部分组成
2. 链表：n个结点由指针链组成一个链表，它是线性表的链式存储映像，称为线性表的链式存储结构

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223129.png" alt="image-20210119223128251" style="zoom: 50%;" />

3. 单链表、双链表、循环链表：

   - 结点只有一个指针域的链表，称为单链表或线性链表

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223338.png" alt="image-20210119223337219" style="zoom: 67%;" />

   - 结点有两个指针域的链表，称为双链表

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223402.png" alt="image-20210119223401378" style="zoom: 67%;" />

   - 首尾相接的链表称为循环链表

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223426.png" alt="image-20210119223425041" style="zoom:67%;" />

4. 头指针、头结点和首元结点

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223558.png" alt="image-20210119223555809" style="zoom:67%;" />

   头指针：是指向链表中第一个结点的指针

   首元结点：是指链表中存储第一个数据元素的结点

   头结点：是在链表的首元结点之前附设的一个结点；

   - 前面的例子中的链表的存储结构示意图有以下两种形式

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119223814.png" alt="image-20210119223813504" style="zoom:50%;" />



- 讨论1：如何表示空表？
  - 无头结点时，**头指针为空**时表示空表

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119225737.png" alt="image-20210119225735581" style="zoom:67%;float:left;" />

  - 有头结点时，**当头结点的指针域为空**时表示空表

  <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210119225823.png" alt="image-20210119225820715" style="zoom:67%;float:left;" />



- 讨论2：在链表中设置头节点有什么好处？


1. 便于首元结点的处理

首元结点的地址保存在头结点的指针域中，所以在链表的第一个位置上的操作和其它位置一致，无需进行特殊处理；

2. 便于空表和非空表的统一处理

无论链表是否为空，头指针都是指向头结点的非空指针，因此空表和非空表的处理也就统一了。



- 讨论3：头结点的数据域内装的是什么？

  头结点的数据域可以为空，也可存放线性表长度等附加信息，但**此结点不能计入链表长度值**。



- 链表（链式存储结构）的特点

（1）结点在存储器中的位置是任意的，即逻辑上相邻的数据元素在物理上不一定相临。

（2）访问时只能通过头指针进入链表，并通过每个结点的指针域依次向后顺序扫描余结点，所以寻找第一个结点和最后一个结点所花费的时间不等，这种存取元素的存取方法被称为顺序存取法。 

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120122736.png" alt="image-20210120122727400" style="zoom:67%;" />

<br>

### 10.单链表的定义和表示

**带头结点的单链表**

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120122921.png" alt="image-20210120122919456" style="zoom:80%;float:left;" />

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120123006.png" alt="image-20210120123005796" style="zoom:67%;float:left;" />

单链表是由表头唯一确定，因此单链表可以用头指针的名字来命名若头指针名是L，则把链表称为表L



- 单链表的存储结构

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120123130.png" alt="image-20210120123128891" style="zoom:67%;float:left;" />

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120123436.png" alt="image-20210120123435041" style="zoom:80%;float:left;" />

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120124113.png" alt="image-20210120124109189" style="zoom:67%;float:left;" />



例如，存储学生学号、姓名、成绩的单链表结点类型定义如下：

```c++
typedef struct student {
	char num[8];						//数据域
	char name[8];						//数据域
	int score;							//数据域
	struct student *next;		//指针域
}Lnode, *LinkList;
```

<img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120124458.png" alt="image-20210120124457915" style="zoom:50%;float:left" />

为了统一链表的操作，通常这样定义：

```c++
typedef struct {
	char num[8];						//数据域
	char name[8];						//数据域
	int score;							//数据域
}ElemType;

typedef struct student {
	ElemType data;					//数据域
	struct student *next;		//指针域
}Lnode, *LinkList;
```

<br>

### 11.单链表基本操作的实现

1. 单链表的初始化
   - 即构造一个空表

```c++
Status InitList_L(LinkList &L) {
	L=new LNode;	//或L = (LinkList)malloc(sizeof(LNode));
	L->next = NULL;
  return OK;
}
```



2. 判断链表是否为空

```c++
Status ListEmpty(LinkList L) {	//若L为空表，则返回1，否则返回0
	if(L->next)		//非空
		return 0;
  else
  	return 1; 
}
```



3. 单链表的销毁：链表了销毁后不存在

   算法思路：从头指针开始，一次释放所有结点

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120125824.png" alt="image-20210120125823535" style="zoom:67%;float:left;" />

```c++
Status DestroyList_L(LinkList &L) {
  Lnode *p;			//或LinkList p;
  while (L) {
    p = L;
    L = L->next;
    delete p;		//或free(p);
  }
  return OK;
}
```



4. 清空链表

   算法思路：依次释放所有结点，并将头结点指针域设置为空

   <img src="https://gitee.com/Huohua2020/Img/raw/master/img/20210120130448.png" alt="image-20210120130447807" style="zoom:67%;float:left;" />

```c++
Status ClearList(LinkList &L){		//将L重置为空表
	Lnode *p, *q;		//或LinkList p, q;
	p = L->next;
	while (p){			//没到表尾
		q = p->next;
		delete p;
		p = q;
	}
	L->next = NULL;		//头结点指针域为空
	return OK;
}
```

