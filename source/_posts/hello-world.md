---
title: Hello World
---

测试博客非原创
<!--more-->

复习一下课没好好上过的数据结构，唉！要期末考试噜！得刷一波绩点啦！！！数据结构和算法要是想成为`Master`，好难欸！！~

> Q：如何高效率使用这篇总结？  
> A：查看写的所有数据结构的定义，然后戳所有带`-> recommend！`这个标识的链接，嗯！速度就是这样~认真的话，建议复写所有数据结构的实现代码啦

### [](#目录 "目录")目录

1.  [**线性表**](#1)  
    1.1 [顺序表示和实现](#1.1)  
    1.2 [链式表示和实现](#1.2)  
    1.2.1 [`线性链表`](#1.2.1)  
    1.2.2 [`循环链表`](#1.2.2)  
    1.2.3 [`双向链表`](#1.2.3)
    
2.  [**栈和队列**](#2)  
    2.1 [栈](#2.1)  
    2.2 [队列](#2.2)
    
3.  [**数组**](#3)  
    3.1 [数组的顺序表示和实现](#3.1)  
    3.2 [矩阵的压缩存储](#3.2)  
    3.2.1 [`稀疏矩阵`](#3.2.1)
    
4.  [**树**](#4)  
    4.1 [二叉树](#4.1)  
    4.2 [遍历二叉树](#4.2)  
    4.2.1 [`三大遍历的递归实现`](#4.2.1)  
    4.2.2 [`三大遍历的非递归实现`](#4.2.2)  
    4.2.3 [`层次遍历`](#4.2.3)  
    4.3 [树和森林](#4.3)  
    4.3.1 [`数和森林的存储结构`](#4.3.1)  
    4.3.2 [`数和森林的遍历`](#4.3.2)  
    4.4 [赫夫曼树](4.4)
    
5.  [**图**](#5)  
    5.1 [图的定义](#5.1)  
    5.2 [图的存储结构](#5.2)  
    5.2.1 [`邻接表`](#5.2.1)  
    5.2.2 [`十字链表`](#5.2.2)  
    5.3 [图的遍历](#5.3)  
    5.3.1 [`深度优先搜索`](#5.3.1)  
    5.3.2 [`广度优先搜索`](#5.3.2)  
    5.4 [图的连通性](#5.4)  
    5.4.1 [`最小生成树`](#5.4.1)  
    5.5 [拓扑排序](#5.5)  
    5.6 [最短路径](#5.6)  
    5.6.1 [`Dijkstra算法`](#5.6.1)
    
6.  [**查找**](#6)  
    6.1 [静态查找](#6.1)  
    6.1.1 [`顺序查找`](#6.1.1)  
    6.1.2 [`二分查找`](#6.1.2)  
    6.2 [动态查找](#6.2)  
    6.2.1 [`二叉排序树`](#6.2.1)  
    6.3 [哈希表](#6.3)
    
7.  [**内部排序**](#7)  
    7.1 [插入排序](#7.1)  
    7.1.1 [`直接插入排序`](#7.1.1)  
    7.1.2 [`折半插入排序`](#7.1.2)  
    7.1.3 [`希尔排序`](#7.1.3)  
    7.2 [交换排序](#7.2)  
    7.2.1 [`冒泡排序`](#7.2.1)  
    7.2.2 [`快速排序`](#7.2.2)  
    7.3 [选择排序](#7.3)  
    7.3.1 [`简单选择排序`](#7.3.1)  
    7.3.2 [`堆排序`](#7.3.2)  
    7.4 [归并排序](#7.4)

* * *

### 1\. 线性表

> 线性表`Linear_list`是最常用且最简单的一种数据结构。简言之，一个线性表是n个数据元素的有限序列。

#### 1.1 顺序表示和实现

> 线性表的顺序表示`Sequential List`指的是用一组地址连续的储存单元依次储存线性表的数据元素。`顺序储存结构`是一种随机存取的储存结构。通常用`数组`来描述顺序储存结构。

C语言用动态分配的一维数组，来描述线性表：

1  
2  
3  
4  
5  
6  
7  
8  

 #define LIST\_INIT\_SIZE 100 //线性表储存空间的初始分配量  
 #define LISTINCREMENT 10 //线性表的分配量  
typedef int ElemType;  
typedef struct {  
 ElemType *elem;  // 储存空间的基地址  
 int length;  //当前线性表的长度  
 int listsize; //当前分配的储存容量  
}SqList;  

> 更多有关线性表的知识，请戳：
> 
> *   [线性表与13个基本操作的实现](https://blog.csdn.net/bruthyu/article/details/52645510)

#### 1.2 链式表示和实现

> 链式储存结构`Linked List`与顺序储存结构`Sequential List`的不同：顺序储存结构的特点是逻辑关系上两个相邻元素在物理位置上也相同，这样随机存取任意元素很快很直观，缺点是需要移动大量其他元素。而链式结构，它不要求逻辑上相邻的元素在物理位置上相邻，因此它存取元素不需要移动其他元素，但是对于查找元素有心无力。

##### 1.2.1 线性链表

> 可以理解为单向链表`Singly Linked List`，单向链表是非随机存取结构。

一些常用的方法：

*   添加元素（s是指向待添加节点的指针）
    
    1  
    2  
    
    s->next = p->next;  
    p->next = s;  
    
*   删除元素（a,b,c是链表中相连的3个结点，b是待删除的结点，现在p是指向a结点的指针）
    
    1  
    
    p->next = p->next->next;  
    

用结构体实现链表结点：

1  
2  
3  
4  
5  

//线性表的单链表储存结构  
struct Node {  
 int data; //数据域  
 struct Node *next; //指针域  
};  

> 更多链表知识，请戳：
> 
> *   [C语言单向链表的实现](https://blog.csdn.net/21aspnet/article/details/160019)
> *   [链表的基本使用一（构建链表）](https://blog.csdn.net/lan74__/article/details/53819849)
> *   [数据结构：链表(linked-list)](https://blog.csdn.net/juanqinyang/article/details/51351619)

##### 1.2.2 循环链表

1.  循环单链表特点：
    
    链表中最后一个结点的指针域不再是结束标志，而是指向整个链表的第一个结点，从而使链表形成一个环。和单链表相同，循环单链表也有带头结点和不带头结点两种。带头结点的循环单链表实现插入和删除操作较为方便，且更加适用。
    
2.  单链表与循环单链表比较：
    
    循环单链表可以从尾到头，而单链表不能从尾到头。因此处理的数据序列具有环形结构特点时，适合采用循环单链表。
    
3.  带头结点的循环单链表和带头结点的单链表比较：
    
    ① 在初始化函数中，把语句`head->next=NULL`改为`head->next = head`，即形成一个环  
    ② 在其他函数中，循环判断条件`p->next!=NULL`和`p->next->next!=NULL`中的NULL改成头指针`head`。
    

##### 1.2.3 双向链表

1.  双向链表特点：  
    每个节点除了有后继指针域还有一个前驱指针域。
    
2.  双向链表的分类：  
    双向链表有：带头结点和不带头结点的双向链表（但是带头结点的双向链表更为常用）。也有循环和非循环之分，循环结构的双向链表更为常用。因此下面讨论的是带头结点的循环双链表。
    
3.  双向循环链表结点的结构体定义
    
    1  
    2  
    3  
    4  
    5  
    6  
    
    //线性表的双向链表储存结构  
    struct DuLNode {  
     Elemtype data; //数据域  
     struct DuLNode *prior; //前驱结点  
     struct DuLNode *next;  //后继结点  
    }DuLNode， *DuLinklist;  
    
    **备注**：data域、next域、prior域。其中data域是数据域，next域为指向后继结点的指针域，prior域为指向前驱结点的指针域。
    
4.  双向链表的优点：  
    在单链中查找当前结点的后继结点并不困难，可以通过当前结点的next指针进行，但要查找当前结点的前驱结点，就要从头指针head开始重新进行。对于一个要频繁进行当前结点的后继结点和前驱结点的应用来说，使用双向链表很有效。
    
5.  双向循环链表的实现  
    在双向链表中，有如下指针关系：设指针p指向双向循环链表中的第i个位置，则`p->next`指向i+1个结点。`p->next->prior`仍指向第i个结点，即`p->next->prior==p`;同样`p->prior`指向第i-1个结点，`p->prior->next`仍指向第i个结点，即`p->prior->next==p`;双向循环链表关系算法可以方便算法设计。
    

> 更多循环链表和双向链表的知识，请戳：
> 
> *   [数据结构——循环单链表和双向链表](https://blog.csdn.net/xiaofei__/article/details/50984255)
> *   [数据结构 | 双向链表简单实现及图示](http://www.cnblogs.com/hughdong/p/6785391.html) -\> _recommend_！

### 2\. 栈和队列

从数据结构上看，栈和队列也是线性表。不过他们是操作受限的线性表，因此，称它们为限定性的数据结构。

#### 2.1 栈

栈`stack`是限定仅在表尾进行插入和删除的线性表。对于栈，表尾称为`栈顶`，相应地，表头称为`栈底`。不含元素的空表称为`空栈`。栈是一种后进先出（last in first out, LIFO）结构。

栈有两种储存方式，顺序栈和链式栈。

顺序栈的定义：

1  
2  
3  
4  
5  

struct stack {  
 SElemType *base;  
 SElemType *top;  
 int stacksize;  
}SqStack;  

**备注**：`stacksize`指当前可使用的最大容量，`base`表示栈底指针，`base`为NULL时，表明栈结构不存在，其初值指向栈底，即`top = base`可作为栈空的标记。插入元素，top+1；删除元素，top-1。

> 更多栈的知识，请戳：
> 
> *   [\[数据结构\]C语言栈的实现](https://www.cnblogs.com/racaljk/p/7822309.html)
> *   [数据结构图文解析之：栈的简介及C++模板实现](https://www.cnblogs.com/QG-whz/p/5170418.html) -\> _recommend_！

#### 2.2 队列

和栈相反，队列`quene`是一种先进先出（first in first out, FIFO）的线性表，它只允许在表的一端插入，另一端删除。在队列中，允许插入的一端叫做队尾`rear`，允许删除的一端叫做队头`front`。

队列也有两种储存方式，顺序队列和链队列。

链队列的实现：

1  
2  
3  
4  
5  
6  
7  
8  

struct QNode {  
 QElemType data;  
 struct QNode *next;  
}QNode, *QuenePtr;  
struct LinkQuene {  
 QuenePtr front; //队头指针  
 QuenePtr rear; //队尾指针  
}LinkQuene;  

> 更多队列知识，请戳：
> 
> *   [数据结构-队列(queue)](https://blog.csdn.net/juanqinyang/article/details/51354293) -\> _recommend_！

### 3\. 数组

数组和广义表可以看作是线性表的扩展，也算是一种数据结构。

#### 3.1 数组的顺序表示和实现

由于数组一般不做插入或删除操作，因此采用顺序储存结构表示数组是最吼滴！

> 假设每个数据元素占$L$个存储单元，则二维数组$A$中任一元素$aij$的存储位置可由下式确定：$LOC(i, j) = LOC(0, 0) + (b_2*i + j)L$

数组的顺序存储的表示：

1  
2  
3  
4  
5  
6  
7  

 #define MAX\_ARRAY\_DIM 8  
struct array {  
 ElemType *base;  
 int dim;  
 int *bounds;  
 int *constants;  
}Array;  

#### 3.2 矩阵的压缩存储

压缩存储指的是为多个值相同的元只分配一个存储单元；对零元不分配空间。

> 更多压缩存储的知识，请戳：
> 
> *   [对称矩阵的压缩](https://www.cnblogs.com/zhang01010/p/7749339.html)

##### 3.2.1 稀疏矩阵

> 对于那些零元素数目远远多于非零元素数目，并且非零元素的分布没有规律的矩阵称为稀疏矩阵（sparse）。

*   由于非零元素分布没有任何规律，所以在进行压缩存储的时侯需要存储非零元素值的同时还要存储非零元素在矩阵中的位置，即非零元素所在的行号和列号，也就是在存储某个元素比如$aij$的值的同时，还需要存储该元素所在的行号$i$和它的列号$j$，这样就构成了一个三元组$(i,j,aij)$的线性表。

1  
2  
3  
4  
5  
6  
7  
8  
9  

 #define MAXSIZE 12500  
struct triple {  
 int i, j; // 该非零元的行下标和列下标  
 ElemType e;  
}Triple;  
struct tsmatrix {  
 Triple data\[MAXSIZE + 1\]; //非零元三元组  
 int mu, nu, tu; //行数，列数，非零元个数  
}TSMatrix;  

> 更多稀疏矩阵的知识，请戳：
> 
> *   [稀疏矩阵](https://blog.csdn.net/sunhuaqiang1/article/details/51296803)

### 4\. 树

> 树状图是一种数据结构，它是由$n$（$n>=1$）个有限节点组成一个具有层次关系的集合。把它叫做“树”是因为它看起来像一棵倒挂的树，也就是说它是根朝上，而叶朝下的。它具有以下的特点：
> 
> *   每个节点有零个或多个子节点
> *   没有父节点的节点称为根节点
> *   每一个非根节点有且只有一个父节点（除了根节点外，每个子节点可以分为多个不相交的子树）

#### 4.1 二叉树

> 二叉树`Binary Tree`是另一种树型结构，它的特点是每个结点至多有$2$棵子树（即二叉树中不存在度大于$2$的结点），并且，二叉树的子树有左右之分，其次序不能任意颠倒。

二叉树的性质：

*   在二叉树的第$i$层上至多有$2^(i-1)$个结点（$i>=1$）。
*   深度为$k$的二叉树至多有$2^k - 1$个结点（$K>=1$）。
*   对任何一棵二叉树$T$，如果其终端结点数为$n\_0$，度为$2$的结点树为$n\_2$，则$n\_0=n\_2+1$。
*   具有$n$个结点的完全二叉树的深度为|$\\log\_2 n$| + 1。（|$\\log\_2 n$|表示不大于$\\log_2 n$的最大整数）
*   如果对一棵有$n$个结点的完全二叉树（其深度为|$\\log\_2 n$| + 1）的结点按层序编号（从第$1$层到第|$\\log\_2 n$| + $1$层，每层从左到右），则对任一结点$i$（$1 <= i <= n$），有：
    1.  如果$i = 1$，则结点$i$是二叉树的根，无双亲；如果$i > 1$，则其双亲`PARENT(i)`是结点|$i/2$|。
    2.  如果$2i > n$，则结点$i$无左孩子（即结点i为叶子结点）；否则其左孩子`LCHILD(i)`是结点$2$。
    3.  如果$2i + 1 > n$，则结点$i$无右孩子；否则其右孩子`RCHILD(i)`是结点$2i+1$。

二叉树的顺序储存结构（仅适用于完全二叉树）：

1  
2  
3  

\# define MAX\_TREE\_SIZE 100 // 二叉树的最大结点树  
typedef TElemType SqBiTree\[MAX\_TREE\_SIZE\]; // 0号单元存储根节点  
SqBiTree bt;  

二叉树的链式存储结构：

1  
2  
3  
4  

struct BiTree {  
 TElemType data; // 数据域  
 struct BiTree *lchild, *rchild; // 左右孩子指针  
}BiTree, *BiTree;  

> 更多二叉树知识，请戳：
> 
> *   [二叉树总结(一)概念和性质](https://www.cnblogs.com/yeqluofwupheng/p/7428935.html)
> *   [markdown中的数学公式简要](https://blog.csdn.net/wireless_com/article/details/70596155)

#### 4.2 遍历二叉树

> 二叉树是一种非线性结构，是由3个基本单元组成：根节点，左子树和右子树。规定先左后右，有3种基本情况，先序遍历，中序遍历和后序遍历。

##### 4.2.1 三大遍历的递归实现

*   先序遍历（根-左-右）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    
    void preOrder1(BinaryTreeNode* pRoot)   
    {   
     if(pRoot==NULL)   
     return;   
      
     cout<<pRoot->value;   
     if(pRoot->left!=NULL)   
     preOrder1(pRoot->left);   
     if(pRoot->right!=NULL)   
     preOrder1(pRoot->right);   
    }  
    
*   中序遍历（左-根-右）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    
    void inOrder1(BinaryTreeNode* pRoot)   
    {   
     if(pRoot==NULL)   
     return;   
        
     if(pRoot->left!=NULL)   
     inOrder1(pRoot->left);   
     cout<<pRoot->value;   
     if(pRoot->right!=NULL)   
     inOrder1(pRoot->right);   
    }  
    
*   后序遍历（左-右-根）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    
    void postOrder1(BinaryTreeNode* pRoot)   
    {   
     if(pRoot==NULL)   
     return;   
     postOrder1(pRoot->left);   
     postOrder1(pRoot->right);   
     cout<<pRoot->value<<" ";   
    }  
    

##### 4.2.2 三大遍历的非遍历实现

*   先序遍历（根-左-右）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    12  
    13  
    14  
    15  
    16  
    17  
    18  
    19  
    20  
    21  
    22  
    23  
    
    void preOrder2(BinaryTreeNode* pRoot)   
    {   
     stack<BinaryTreeNode*> s;   
     BinaryTreeNode *p=pRoot;   
      
     if(pRoot==NULL)   
     return;   
     while(p!=NULL||!s.empty())   
     {   
     while(p!=NULL)   
     {   
     cout<<p->value<<" ";   
     s.push(p);   
     p=p->left;   
     }   
     if(!s.empty())   
     {   
     p=s.top();   
     s.pop();   
     p=p->right;   
     }   
     }   
    }  
    
*   中序遍历（左-根-右）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    12  
    13  
    14  
    15  
    16  
    17  
    18  
    19  
    20  
    
    void inOrder(BinaryTreeNode* pRoot)   
    {   
     stack<BinaryTreeNode*> s;   
     BinaryTreeNode *p=pRoot;   
     while(p!=NULL||!s.empty())   
     {   
     while(p!=NULL)   
     {   
     s.push(p);   
     p=p->left;   
     }   
     if(!s.empty())   
     {   
     p=s.top();   
     cout<<p->value;   
     s.pop();   
     p=p->right;   
     }   
     }   
    }  
    
*   后序遍历（左-右-根）
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    12  
    13  
    14  
    15  
    16  
    17  
    18  
    19  
    20  
    21  
    22  
    23  
    24  
    25  
    
    void postOrder(BinaryTreeNode* pRoot)   
    {   
     stack<BinaryTreeNode*> s;   
     BinaryTreeNode *cur;   
     BinaryTreeNode *pre=NULL;   
     s.push(pRoot);//根结点入栈   
     while(!s.empty())   
     {   
     cur=s.top();   
     if((cur->left==NULL&&cur->right==NULL)||(pre!=NULL&&(pre==cur->left||pre==cur->right)))   
     {   
     //左孩子和右孩子同时为空，或者当前结点的左孩子或右孩子已经遍历过了   
     cout<<cur->value<<" ";   
     s.pop();   
     pre=cur;   
     }   
     else   
     {   
     if(cur->right!=NULL)   
     s.push(cur->right);   
     if(cur->left!=NULL)   
     s.push(cur->left);   
     }   
     }   
    }  
    

##### 4.2.3 层次遍历

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  

void PrintFromTopToBottom(BinaryTreeNode* pRoot)   
{   
 if(pRoot == NULL)   
 return;   
    
 std::deque<BinaryTreeNode *> dequeTreeNode;   
    
 dequeTreeNode.push_back(pRoot);   
    
 while(dequeTreeNode.size())   
 {   
 BinaryTreeNode *pNode = dequeTreeNode.front();   
 dequeTreeNode.pop_front();   
    
 printf("%d ", pNode->m_nValue);   
    
 if(pNode->m_pLeft)   
 dequeTreeNode.push\_back(pNode->m\_pLeft);   
    
 if(pNode->m_pRight)   
 dequeTreeNode.push\_back(pNode->m\_pRight);   
 }   
}  

> 更多二叉树的知识，请戳：
> 
> *   [二叉树的四种遍历的递归和非递归的实现](https://blog.csdn.net/xiaominkong123/article/details/51567437) -\> _recommend_！
> *   [二叉树三种遍历方式的递归和循环实现](https://blog.csdn.net/lieacui/article/details/52453292)

#### 4.3 树和森林

##### 4.3.1 树的存储结构

> 双亲表示法

1  
2  
3  
4  
5  
6  
7  
8  
9  

 #define MAX\_TREE\_SIZE 100  
typedef struct PTNode { // 结点结构  
 TElemType data; // 数据域  
 int parent; // 双亲位置域  
}PTNode;  
typedef struct { // 树结构  
 PTNode nodes\[MAX\_TREE\_SIZE\];   
 int r, n; // 根的位置和结点数  
}  

缺点：求结点的孩子时需要遍历整个结构。

> 孩子表示法

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  

typedef struct CTNode { // 孩子结点  
 int child;   
 sturct CTNode *next;  
}*ChildPtr;  
typedef struct {  
 TElemType data;  
 ChildPtr firstchild; // 孩子链表头结点  
}CTBox;  
typedef struct {  
 CTBox nodes\[MAX\_TREE\_SIZE\];  
 int n, r; // 结点数的根的位置  
}  

> 孩子兄弟表示法（可以把复杂的树变成二叉树）

1  
2  
3  
4  

typedef struct CSNode {  
 ElemType data;  
 struct CSNode *firstchild, *nextsibling; // 第一个孩子结点和下一个兄弟结点  
}  

##### 4.3.2 树和森林的遍历

当二叉链表作为树的储存结构时，树的**先根遍历**和**后根遍历**类似于二叉树的**先序遍历**和**中序遍历**实现。

森林一般只说**先序遍历**和**中序遍历**，和二叉树的**先序遍历**和**中序遍历**相同。

> 更多树和森林的知识，请戳：
> 
> *   [树的存储结构和代码实现](https://blog.csdn.net/qq_36016407/article/details/55272598)
> *   [树和森林的遍历](https://blog.csdn.net/wangzi11322/article/details/45391157)

#### 4.4 赫夫曼树

> 赫夫曼树`Huffman`，又称最优二叉树，是一类带权路径长度最短的树。树的路径长度为树中所有叶子结点的带权路径长度之和。通常记作$WPL=\\sum_{k=0}^{n}\\omega\_k\\iota\_k$ 。

假设有n个权值，构造一棵有n个叶子结点的二叉树，每个叶子结点带权为$\\omega_i$，则其中带权路径长度$WPL$最小的二叉树称为**赫夫曼树**。

1  
2  
3  
4  

typedef struct {  
 unsigned int weight; // 权重  
 unsigned int parent, lchild, rchild;   
}HTNode, *HuffmanTree; // 动态分配数组存储赫夫曼树  

> 更多赫夫曼树的知识，请戳：
> 
> *   [哈夫曼树](https://blog.csdn.net/wo16fafafa/article/details/52420007)
> *   [基础数据结构-二叉树-赫夫曼树的解码](https://www.cnblogs.com/nathaneko/p/6497982.html)

### 5\. 图

> **图**`Graph`是一种较线性表和树更为复杂的数据结构。在**线性表**中，数据元素之间仅有线性关系，每个数据元素只有一个直接前驱和一个直接后继；在**树**形结构中，数据元素之间有着明显的层次关系，并且每一层上的数据元素可能和下一层的多个元素（即孩子结点）相关，但只和上一层的一个元素（即双亲结点）相关。而在**图**形结构中，结点之间的关系是任意的。

#### 5.1 图的定义

在图中，数据元素称为**顶点**，$V$是顶点的有穷非空集合；$VR$是两个顶点之间的关系集合。

*   若$<v,w>\\epsilon VR$,则$<v,w>$表示从$v$到$w$的一条**弧**`Arc`，且称$v$为**弧尾**`Tail`or**初始点**，$w$为**弧头**`Head`or**终端点**。此时的图称为**有向图**`Digraph`。

$$G\_1 = (V\_1,{A_1})$$

*   若$<v,w>\\epsilon VR$，必有$<w,v>\\epsilon VR$，即$VR$是对称的，则以无序对$(v,w)$代替这两个有序对，表示$v$和$w$之间的一条**边**`Edge`，此时的图称为**无向图**`Undigraph`。

$$G\_2 = (V\_2,{E_2})$$

#### 5.2 图的存储结构

> 图的结构较为复杂，常用的存储结构有**邻接表**，**十字链表**。

##### 5.2.1 邻接表

> **邻接表**`Adjacency List`是图的一种链式存储结构。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  

 #define MAX\_VERTEX\_NUM 20  
typedef struct ArcNode {  
 int adjvex; // 该弧所指向的顶点的位置  
 struct ArcNode *nextarc; // 指向下一条弧的指针  
 InfoType *info; // 该弧相关信息的指针  
}ArcNode;  
typedef struct VNode {  
 VertexType data; // 顶点信息  
 ArcNode *firstarc; //指向第一条依附该顶点的弧的指针  
}VNode, AdjList\[MAX\_VERTEX\_NUM\];  
typedef struct {  
 AdjList vertices;  
 int vexnum, arcnum; //图的当前顶点数和弧数  
 int kind; // 图的种类标志  
}ALGraph;  

##### 5.2.2 十字链表

> **十字链表**`Orthogonal List`是有向图的另一种链式存储结构。可以看作是将有向图的邻接表和逆邻接表结合起来的一种链表。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  

 #define MAX\_VERTEX\_NUM 20  
typedef struct ArcBox {  
 int tailvex, headvex; // 该弧的尾和头顶点的位置  
 struct ArcBox *hlink, *tlink; // 分别为弧头相同和弧尾相同的弧的链域  
 InfoType *info; // 该弧相关的信息的指针  
}ArcBox;  
typedef struct VexNode {  
 VertexType data;  
 ArcBox \*firstin, \*firstout; // 分别指向该顶点的第一条入弧和出弧  
}VexNode;  
typedef struct {  
 VexNode xlist\[MAX\_VERTEX\_NUM\]; // 表头向量  
 int vexnum, arcnum; // 有向图的当前顶点数和弧数  
}OLGraph;  

> 更多关于图的存储的知识，请戳：
> 
> *   [数据结构(16)–图的存储及实现](https://blog.csdn.net/u010366748/article/details/50790324)
> *   [图的存储结构之邻接表(详解)](https://www.cnblogs.com/ECJTUACM-873284962/p/6905416.html)
> *   [图的存储 ( 十字链表 )](https://blog.csdn.net/wr_technology/article/details/51909432) -\> _recommend_！
> *   [十字链表的画法](https://www.cnblogs.com/zyl905487045/p/7815429.html) -\> _recommend_！

#### 5.3 图的遍历

> **图的遍历**`Traversing Graph`指从图中某一顶点出发访遍图中其余顶点，且使每一个顶点仅被访问一次。

##### 5.3.1 深度优先搜索

> **深度优先搜索**`Depth_First Search`遍历类似于树的**先根遍历**。

1  
2  
3  
4  
5  
6  
7  
8  

void DFS(Graph G, int v) {  
 //从第v个顶点出发递归地深度优先遍历图G  
 visited\[v\] = TRUE;  
 visitFunc(v); // 访问第v个顶点  
 for(w = FirstAdjVex(G,v); w >= 0; w = NextAdjVex(G,v,w))  
 if(!visited\[w\])  
 DFS(G,w); // 对v的尚未访问的邻接顶点w递归调用DFS  
}  

##### 5.3.2 广度优先搜索

> **广度优先搜索**`Breadth_First Search`遍历类似于树的**层次遍历**。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  

void BFSTraverse(Graph G, Status(*visit)(int v)) {  
 // 按广度优先非递归遍历图G，使用辅助队列Q和访问标志数组visited  
 for(v = 0; v < G.vexnum; ++v)  
 visited\[v\] = FALSE;  
 InitQuene(Q); // 置空的辅助队列Q  
 for(v = 0; v < G.vexnum; ++v)  
 if(!visited\[v\]) { // v尚未访问  
 visited\[v\] = TRUE;  
 Visit(v);  
 Enquene(Q, v); // v入队列  
 while(!QueneEmpty(Q)) {  
 DeQuene(Q, u); // 队头元素出列并置为0  
 for(w = FirstAdjVex(G, u); w >= 0; w = NextAdjVex(G, u, w))  
 if(!Visited\[w\]) { // w为u的尚未访问的邻接顶点  
 Visited\[w\] = TRUE;  
 Visit(w);  
 EnQuene(Q, W);  
 } // if  
 } //while  
 } // if  
} // BFSTraverse  

遍历图的过程实质上是通过边或弧找邻接点的过程，因此广度优先搜索和深度优先搜索地**时间复杂度**相同。

> 更多关于图的遍历的知识，请戳：
> 
> *   [图的深度优先遍历和广度优先遍历理解](https://www.cnblogs.com/George1994/p/6399889.html)
> *   [数据结构和算法总结（一）：广度优先搜索BFS和深度优先搜索DFS](https://www.cnblogs.com/0kk470/p/7555033.html) -\> _recommend_！

#### 5.4 图的连通性问题

> 对于连通图来说，从任一顶点出发，便可访问图中所有顶点。而对于非连通地图，则需从多个顶点出发进行搜索。

##### 5.4.1 最小生成树

关于图的几个概念定义：

*   连通图：在无向图中，若任意两个顶点vi与vj都有路径相通，则称该无向图为连通图。
*   强连通图：在有向图中，若任意两个顶点vi与vj都有路径相通，则称该有向图为强连通图。
*   连通网：在连通图中，若图的边具有一定的意义，每一条边都对应着一个数，称为权；权代表着连接连个顶点的代价，称这种连通图叫做连通网。
*   生成树：一个连通图的生成树是指一个连通子图，它含有图中全部n个顶点，但只有足以构成一棵树的n-1条边。一颗有n个顶点的生成树有且仅有n-1条边，如果生成树中再添加一条边，则必定成环。
*   最小生成树：在连通网的所有生成树中，所有边的代价和最小的生成树，称为最小生成树。

> **最小生成树**`Minimum Cost Spanning Tree`指构造连通网的最小代价生成树。

*   **Kruskal算法**

> 此算法可以称为“加边法”，初始最小生成树边数为0，每迭代一次就选择一条满足条件的最小代价边，加入到最小生成树的边集合里。

1.  把图中的所有边按代价从小到大排序；
2.  把图中的n个顶点看成独立的n棵树组成的森林；
3.  按权值从小到大选择边，所选的边连接的两个顶点ui,vi,应属于两颗不同的树，则成为最小生成树的一条边，并将这两颗树合并作为一颗树。
4.  重复(3),直到所有顶点都在一颗树内或者有n-1条边为止。

*   **Prim算法**

> 此算法可以称为“加点法”，每次迭代选择代价最小的边对应的点，加入到最小生成树中。算法从某一个顶点s开始，逐渐长大覆盖整个连通网的所有顶点。

1.  图的所有顶点集合为V；初始令集合u={s},v=V−u;
2.  在两个集合u,v能够组成的边中，选择一条代价最小的边(u0,v0)，加入到最小生成树中，并把v0并入到集合u中。
3.  重复上述步骤，直到最小生成树有n-1条边或者n个顶点为止。

由于不断向集合u中加点，所以最小代价边必须同步更新；需要建立一个辅助数组closedge,用来维护集合v中每个顶点与集合u中最小代价边信息：

1  
2  
3  
4  
5  

struct  
{  
 char vertexData   //表示u中顶点信息  
 UINT lowestcost   //最小代价  
}closedge\[vexCounts\]  

> 更多关于最小生成树的知识，请戳：
> 
> *   [算法导论–最小生成树（Kruskal和Prim算法）](https://blog.csdn.net/luoshixian099/article/details/51908175) -\> _recommend_！

#### 5.5 拓扑排序

> **拓扑排序**`Topological Sort`指由某个集合上的一个偏序得到该集合上的一个全序。

拓扑排序的实现步骤:

1.  在有向图中选一个没有前驱的顶点并且输出。
2.  从图中删除该顶点和所有以它为尾的弧（白话就是：删除所有和它有关的边）。
3.  重复上述两步，直至所有顶点输出，或者当前图中不存在无前驱的顶点为止，后者代表我们的有向图是有环的。

因此，也可以通过拓扑排序来判断一个图是否有环。

> 更多关于拓扑排序的知识，请戳：
> 
> *   [数据结构—拓扑排序详解](https://blog.csdn.net/qq_35644234/article/details/60578189)

#### 5.6 最短路径

> **最短路径**指从图中的某个顶点出发到达另外一个顶点的所经过的边的权重和最小的一条路径.

##### 5.6.1 Dijkstra算法

> 算法特点：迪科斯彻算法使用了广度优先搜索解决赋权有向图或者无向图的单源最短路径问题，算法最终得到一个最短路径树。该算法常用于路由算法或者作为其他图算法的一个子模块。

*   算法的思路

1.  Dijkstra算法采用的是一种贪心的策略，声明一个数组dis来保存源点到各个顶点的最短距离和一个保存已经找到了最短路径的顶点的集合：T，初始时，原点 s 的路径权重被赋为 0 （dis\[s\] = 0）。若对于顶点 s 存在能直接到达的边（s,m），则把dis\[m\]设为w（s, m）,同时把所有其他（s不能直接到达的）顶点的路径长度设为无穷大。初始时，集合T只有顶点s。
2.  然后，从dis数组选择最小值，则该值就是源点s到该值对应的顶点的最短路径，并且把该点加入到T中，OK，此时完成一个顶点，
3.  然后，我们需要看看新加入的顶点是否可以到达其他顶点并且看看通过该顶点到达其他点的路径长度是否比源点直接到达短，如果是，那么就替换这些顶点在dis中的值。
4.  然后，又从dis中找出最小值，重复上述动作，直到T中包含了图的所有顶点

> 更多关于最短路径的知识，请戳：
> 
> *   [最短路径问题—Dijkstra算法详解](https://blog.csdn.net/qq_35644234/article/details/60870719)

### 6\. 查找

> **查找**`Search`：根据给定的某个值，在查找表中确定一个其关键字等于给定值的数据元素（或记录）。分类有**静态查找**和**动态查找**。

*   注：静态或者动态都是针对查找表而言的。动态表指查找表中有删除和插入操作的表。

#### 6.1 静态查找

##### 6.1.1 顺序查找

1.  说明：顺序查找适合于存储结构为顺序存储或链接存储的线性表。
2.  基本思想：顺序查找也称为线形查找，属于无序查找算法。从数据结构线形表的一端开始，顺序扫描，依次将扫描到的结点关键字与给定值k相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于k的结点，表示查找失败。
3.  复杂度分析：

*   查找成功的平均查找长度为（假设每个数据元素的概率相等）: $$ASL = 1/n(1+2+3+…+n) = (n+1)/2$$
*   当查找不成功时，需要$n+1$次比较，时间复杂度为$O(n)$；所以，顺序查找的时间复杂度为$O(n)$。

> C++实现源码：

    123456789//顺序查找int SequenceSearch(int a[], int value, int n){    int i;    for(i=0; i<n; i++)        if(a[i]==value)            return i;    return -1;}
    

##### 6.1.2 二分查找（折半查找）

1.  说明：元素必须是**有序**的，如果是无序的则要先进行排序操作。
2.  基本思想：也称为是折半查找，属于**有序查找算法**。用给定值k先与中间结点的关键字比较，中间结点把线形表分成两个子表，若相等则查找成功；若不相等，再根据k与该中间结点关键字的比较结果确定下一步查找哪个子表，这样递归进行，直到查找到或查找结束发现表中没有这样的结点。
3.  折半查找的平均查找长度：$$ASL_{bs} = \\frac{1}{n}\\sum_{i=1}^{n}{j\\times2^{j-1}} = \\frac{n+1}{n}\\log\_2(n+1) - 1 = \\log\_2(n+1) - 1 $$
4.  复杂度分析：最坏情况下，关键词比较次数为$\\log\_2(n+1)$，且期望时间复杂度为$O(log\_2n)$；

*   注：折半查找的前提条件是需要有序表顺序存储，对于静态查找表，一次排序后不再变化，折半查找能得到不错的效率。但对于需要频繁执行插入或删除操作的数据集来说，维护有序的排序会带来不小的工作量，那就不建议使用。——《大话数据结构》

> C++实现源码：

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  

//二分查找（折半查找），非递归版本  
int BinarySearch1(int a\[\], int value, int n)  
{  
 int low, high, mid;  
 low = 0;  
 high = n-1;  
 while(low<=high)  
 {  
 mid = (low+high)/2;  
 if(a\[mid\]==value)  
 return mid;  
 if(a\[mid\]>value)  
 high = mid-1;  
 if(a\[mid\]<value)  
 low = mid+1;  
 }  
 return -1;  
}  
  
//二分查找，递归版本  
int BinarySearch2(int a\[\], int value, int low, int high)  
{  
 int mid = low+(high-low)/2;  
 if(a\[mid\]==value)  
 return mid;  
 if(a\[mid\]>value)  
 return BinarySearch2(a, value, low, mid-1);  
 if(a\[mid\]<value)  
 return BinarySearch2(a, value, mid+1, high);  
}  

> 更多查找算法，请戳：
> 
> *   [数据结构–七大查找算法总结](https://blog.csdn.net/sayhello_world/article/details/77200009)
> *   [【数据结构】静态查找之分块查找](https://blog.csdn.net/u013036274/article/details/49176027)

#### 6.2 动态查找

> 动态查找：当查找表以顺序存储结构存储且需要保持有序时，若对查找表进行插入、删除或排序操作，就必须移动大量的记录，当记录数很多时，这种移动的代价很大。 若查找表无序，则插入删除可无需移动大量记录，但于查找不利。 利用树的形式组织查找表，可以对查找表进行动态高效的查找。

##### 6.2.1 二叉排序树

**二叉排序树**`Binary Sort Tree`的定义为：二叉排序树或者是空树，或者是满足下列性质的二叉树。

1.  若左子树不为空，则左子树上所有结点的值(关键字)都小于根结点的值；
2.  若右子树不为空，则右子树上所有结点的值(关键字)都大于根结点的值；
3.  左、右子树都分别是二叉排序树。

*   二叉排序树性能

1.  二叉排序树查找关键字的比较次数，等于该结点所在的层次数（查找成功）； 若查找不成功，其比较次数最多为树的深度。
2.  对于一棵具有n个结点的树来说，其深度介$log_2(n+1)$与$n$之间。
3.  二叉排序树的形态对于查找效率至关重要，或者说，一棵二叉排序树不一定就能提高查找的速度，而是要看这棵树的形态。

**注**：若按中序遍历一棵二叉排序树，所得到的结点序列是一个递增序列。

> 更多动态查找的知识，请戳：
> 
> *   [数据结构-动态查找](https://www.2cto.com/database/201505/396663.html)
> *   [查找算法总结之二（动态查找表）](https://blog.csdn.net/jerryburning/article/details/46636479)

#### 6.3 哈希表

> 散列表（`Hash table`，也叫**哈希表**），是根据关键码值(Key value)而直接进行访问的数据结构。也就是说，它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫做散列函数，存放记录的数组叫做散列表。给定表M，存在函数f(key)，对任意给定的关键字值key，代入函数后若能得到包含该关键字的记录在表中的地址，则称表M为哈希(Hash）表，函数f(key)为哈希(Hash) 函数。

> 哈希表是一种通过哈希函数将特定的键映射到特定值的一种数据结构，他维护者键和值之间一一对应关系。

1.  键(key)：又称为关键字。唯一的标示要存储的数据，可以是数据本身或者数据的一部分。
2.  槽(slot/bucket)：哈希表中用于保存数据的一个单元，也就是数据真正存放的容器。
3.  哈希函数(hash function)：将键(key)映射(map)到数据应该存放的槽(slot)所在位置的函数。
4.  哈希冲突(hash collision)：哈希函数将两个不同的键映射到同一个索引的情况。

> 更多哈希表的知识，请戳：
> 
> *   [浅谈哈希表(HashTable)](https://www.jianshu.com/p/dbe7a1ea5928) -\> _recommend_！
> *   [程序员常说的「哈希表」是个什么鬼?](http://baijiahao.baidu.com/s?id=1580022096840800840&wfr=spider&for=pc)

### 7\. 内部排序

> **内部排序**指待排序记录存放在计算机随机存储器（如内存）中进行的排序过程。  
> **外部排序**指待排序记录的数量很大，以致于内存一次不能容纳全部记录，在排序过程中尚需对外存进行访问的排序过程。

注：我们常常用到的是**内部排序**。

#### 7.1 插入排序

##### 7.1.1 直接插入排序

*   介绍

**直接插入排序**`Straight Insertion Sort`是基于比较的排序。所谓的基于比较，就是通过比较数组中的元素，看谁大谁小，根据结果来调整元素的位置。

因此，对于这类排序，就有两种基本的操作：①比较操作； ②交换操作

其中，对于交换操作，可以优化成移动操作，即不直接进行两个元素的交换，还是用一个枢轴元素(tmp)将当前元素先保存起来，然后执行移动操作，待确定了最终位置后，再将当前元素放入合适的位置。（下面的插入排序就用到了这个技巧）–因为，交换操作需要三次赋值，而移动操作只需要一次赋值！

有些排序算法，比较次数比较多，而移动次数比较少，而有些则相反。比如，归并排序和快速排序，前者移动次数比较多，而后者比较次数比较多。

*   复杂度分析

插入排序在实现上，通常采用in-place排序（即只需用到$O(1)$的空间复杂度和$O(N^2)$的时间复杂度）），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  

void Insertsort1(int a\[\], int n)   
{   
 int i, j, k;   
 for (i = 1; i < n; i++)   
 {   
 //为a\[i\]在前面的a\[0...i-1\]有序区间中找一个合适的位置   
 for (j = i - 1; j >= 0; j--)   
 if (a\[j\] < a\[i\])   
 break;   
    
 //如找到了一个合适的位置   
 if (j != i - 1)   
 {   
 //将比a\[i\]大的数据向后移   
 int temp = a\[i\];   
 for (k = i - 1; k > j; k--)   
 a\[k + 1\] = a\[k\];   
 //将a\[i\]放到正确位置上   
 a\[k + 1\] = temp;   
 }   
 }   
}  

> 更多直接插入排序的知识，请戳：
> 
> *   [插入排序算法详解及实现](https://blog.csdn.net/llzk_/article/details/51628574)
> *   [白话经典算法系列之二 直接插入排序的三种实现](https://blog.csdn.net/morewindows/article/details/6665714)

##### 7.1.2 折半插入排序

> 插入排序的基本操作是在一个有序表中进行查找和插入。利用“折半查找”的查找操作实现的插入排序，称为**折半插入排序**`Binary Insertion Sort`。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  

void InsertSort(Elemtype A\[\],int n){  
 int i,j,low,high,mid;  
 for(i=2;i<=n;i++){  
 A\[0\]=A\[i\];  
 low=1;  
 high=i-1;//设置折半查找的范围，从1到i-1,A\[0\]用来暂存元素  
 while(low<=high){  
 mid=(low+high)/2;  
 if(A\[mid\].key>A\[0\].key) high=mid-1;//查找左半子表  
 else low=mid+1;//查找右半子表  
 }  
 for(j=i-1;j>=high+1;--j)  
 A\[j+1\]=A\[j\];//统一向后移动元素，空出插入位置  
 A\[high+1\]=A\[0\];//插入操作  
 }  
}  

> 更多折半插入排序的知识，请戳：
> 
> *   [数据结构折半插入排序](https://blog.csdn.net/m0_37316917/article/details/70990523) ->_recommend_！

##### 7.1.3 希尔排序

> **希尔排序**`Shell's Sort`又称最小增量排序，它的基本思想是将整个待排序记录序列分割成若干个子序列分别进行**插入排序**，待整个序列的记录“基本有序”时，再对全体记录进行一次直接插入排序。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  

void ShellSort(int array\[\], int len) // O(n*n)  
{  
 int i = 0;  
 int j = 0;  
 int k = -1;  
 int temp = -1;  
 int gap = len;  
 do {  
 gap = gap / 3 \+ 1;  
 for (i=gap; i<len; i+=gap) {  
 k = i;  
 temp = array\[k\];  
 for (j=i-gap; (j>=0) && (array\[j\]>temp); j-=gap) {  
 array\[j+gap\] = array\[j\];  
 k = j;  
 }  
 array\[k\] = temp;  
 }  
 } while (gap > 1);  
}  

> 更多希尔排序的知识，请戳：
> 
> *   [图解排序算法(二)之希尔排序](http://www.cnblogs.com/chengxiao/p/6104371.html)
> *   [希尔排序详解](https://blog.csdn.net/daiyudong2020/article/details/52445044) ->_recommend_！
> *   [排序五：希尔排序](https://www.cnblogs.com/ronnydm/p/5905715.html) ->_recommend_！

#### 7.2 交换排序

##### 7.2.1 冒泡排序

> 冒泡排序算法的运作如下：（从后往前）
> 
> 1.  比较相邻的元素。如果第一个比第二个大，就交换他们两个。
> 2.  对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。
> 3.  针对所有的元素重复以上的步骤，除了最后一个。
> 4.  持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

*   时间复杂度

冒泡排序最好的时间复杂度为 $O(n)$。  
冒泡排序的最坏时间复杂度为 $O(n^2)$。  
综上，因此冒泡排序总的平均时间复杂度为 $O(n^2)$。

*   算法稳定性

**冒泡排序**`Bubble Sort`就是把小的元素往前调或者把大的元素往后调。比较是相邻的两个元素比较，交换也发生在这两个元素之间。所以，如果两个元素相等，我想你是不会再无聊地把他们俩交换一下的；如果两个相等的元素没有相邻，那么即使通过前面的两两交换把两个相邻起来，这时候也不会交换，所以相同元素的前后顺序并没有改变，所以冒泡排序是一种稳定排序算法。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  

void bubble_sort(T arr\[\], int len)  
{  
 int i, j;  T temp;  
 for (i = 0; i < len - 1; i++)  
 for (j = 0; j < len - 1 \- i; j++)  
 if (arr\[j\] > arr\[j + 1\])  
 {  
 temp = arr\[j\];  
 arr\[j\] = arr\[j + 1\];  
 arr\[j + 1\] = temp;  
 }  
}  

> 更多冒泡排序的知识，请戳：
> 
> *   [白话经典算法系列之一 冒泡排序的三种实现](https://blog.csdn.net/morewindows/article/details/6657829)
> *   [经典排序算法学习笔记一——冒泡排序](https://www.cnblogs.com/crystalmoore/p/5929814.html)

##### 7.2.2 快速排序

> **快速排序**`Quick Sort`是对**冒泡排序**的一种改进。它的基本思想是，通过一趟排序将待排序记录分割成独立的两部分，其中一部分记录的关键字均比另一部分记录的关键字小，继续进行排序以达到整个序列有序。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  

int PartSort1(int\* a,int left,int right)//左右指针法   
{   
 int mid = GetMidIndex(a,left,right);    //此处是对快排的优化，再后面会提到   
 swap(a\[mid\],a\[right\]);   
    
 int key = right;//利用key作为基准值的下标   
    
 while (left < right)   
 {   
 //左指针向右找第一个比key大的数   
 while (left < right && a\[left\] <= a\[key\])   
 {   
 ++left;   
 }   
 //右指针向左扎找第一个比key的数   
 while (left < right && a\[right\] >= a\[key\])   
 {   
 --right;   
 }   
 //交换左右指针所指的值   
 if (a\[left\] != a\[right\])   
 {   
 std::swap(a\[left\],a\[right\]);   
 }   
 }   
 //将key值放到正确位置上   
 swap(a\[left\],a\[key\]);   
    
 return left;   
}  

快速排序的时间复杂度为：$O(nlogn)$

> 更多快速排序的知识，请戳：
> 
> *   [快速排序基本思路（通俗易懂+例子）](https://blog.csdn.net/code_ac/article/details/74158681)
> *   [快速排序](https://blog.csdn.net/payshent/article/details/60879120)
> *   [快速排序基本思路（通俗易懂+例子）](https://blog.csdn.net/code_ac/article/details/74158681) ->_recommend_！
> *   [图解快速排序](https://www.cnblogs.com/MOBIN/p/4681369.html) ->_recommend_！

#### 7.3 选择排序

> **选择排序**`Selection Sort`：每一趟在$n-i+1(i=1,2,3,…,n-1)$个记录中选取关键字最小的记录作为有序序列的第$i$个记录。

##### 7.3.1 简单选择排序

> 一趟简单选择排序的操作是：通过$n-i$次关键字间的比较，从$n-i+1(i=1,2,3,…,n-1)$个记录中选取关键字最小的记录，并和第$i$个记录交换之。

简单选择排序的时间复杂度为$O(n^2)$

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  

void select_sort(int A\[\],int n)  
{  
 register int i,j,min,m;  
 for(i=0;i<n-1;i++)  
 {  
 min=i;//查找最小值  
 for(j=i+1;j<n;j++)  
 {  
 if(A\[min\]>A\[j\])  
 {  
 min=j;  
 }  
 }  
 if(min!=i)  
 {  
 swap(&A\[min\],&A\[i\]);  
    
 }  
 }  
}  

*   稳定性

选择排序是给每个位置选择当前元素最小的，比如给第一个位置选择最小的，在剩余元素里面给第二个元素选择第二小的，依次类推，直到第n-1个元素，第n个元素不用选择了，因为只剩下它一个最大的元素了。那么，在一趟选择，如果一个元素比当前元素小，而该小的元素又出现在一个和当前元素相等的元素后面，那么交换后稳定性就被破坏了。比较拗口，举个例子，序列5 8 5 2 9，我们知道第一遍选择第1个元素5会和2交换，那么原序列中两个5的相对前后顺序就被破坏了，所以选择排序是一个不稳定的排序算法。

> 更多关于选择排序的知识，请戳：
> 
> *   [经典排序算法之选择排序](http://baijiahao.baidu.com/s?id=1586561314836092820&wfr=spider&for=pc)

##### 7.3.2 堆排序

> **堆排序**`Heap Sort`是利用堆这种数据结构而设计的一种排序算法，堆排序是一种选择排序，它的最坏，最好，平均时间复杂度均为$O(nlogn)$，它也是不稳定排序。首先简单了解下堆结构。

堆排序的基本思想是：将待排序序列构造成一个大顶堆，此时，整个序列的最大值就是堆顶的根节点。将其与末尾元素进行交换，此时末尾就为最大值。然后将剩余n-1个元素重新构造成一个堆，这样会得到n个元素的次小值。如此反复执行，便能得到一个有序序列了。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  
45  
46  

void swap(int *a, int *b);  
void adjustHeap(int param1,int j, int inNums\[\]);  
void  HeapSort(int nums, int inNums\[\]);  
//大根堆进行调整  
void adjustHeap(int param1, int j, int inNums\[\])  
{  
 int temp=inNums\[param1\];  
 for (int k=param1*2+1;k<j;k=k*2+1)  
 {  
 //如果右边值大于左边值，指向右边  
 if (k+1<j && inNums\[k\]< inNums\[k+1\])  
 {  
 k++;  
 }  
 //如果子节点大于父节点，将子节点值赋给父节点,并以新的子节点作为父节点（不用进行交换）  
 if (inNums\[k\]>temp)  
 {  
 inNums\[param1\]=inNums\[k\];  
 param1=k;  
 }  
 else  
 break;  
 }  
 //put the value in the final position  
 inNums\[param1\]=temp;  
}  
//堆排序主要算法  
void HeapSort(int nums,int inNums\[\])  
{  
 //1.构建大顶堆  
 for (int i=nums/2-1;i>=0;i--)  
 {  
 //put the value in the final position  
 adjustHeap(i,nums,inNums);  
 }  
 //2.调整堆结构+交换堆顶元素与末尾元素  
 for (int j=nums-1;j>0;j--)  
 {  
 //堆顶元素和末尾元素进行交换  
 int temp=inNums\[0\];  
 inNums\[0\]=inNums\[j\];  
 inNums\[j\]=temp;  
    
 adjustHeap(0,j,inNums);//重新对堆进行调整  
 }  
}  

> 更多堆排序的知识，请戳：
> 
> *   [浅谈堆排序](https://www.jianshu.com/p/938789fde325)
> *   [堆排序详解](https://www.cnblogs.com/0zcl/p/6737944.html) ->_recommend_！
> *   [图解排序算法(三)之堆排序](https://www.cnblogs.com/chengxiao/p/6129630.html)

#### 7.4 归并排序

> **归并排序**`Merging Sort`是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。

1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44  

//将有二个有序数列a\[first...mid\]和a\[mid...last\]合并。   
void mergearray(int a\[\], int first, int mid, int last, int temp\[\])   
{   
 int i = first, j = mid + 1;   
 int m = mid,   n = last;   
 int k = 0;   
    
 while (i <= m && j <= n)   
 {   
 if (a\[i\] <= a\[j\])   
 temp\[k++\] = a\[i++\];   
 else   
 temp\[k++\] = a\[j++\];   
 }   
    
 while (i <= m)   
 temp\[k++\] = a\[i++\];   
    
 while (j <= n)   
 temp\[k++\] = a\[j++\];   
    
 for (i = 0; i < k; i++)   
 a\[first + i\] = temp\[i\];   
}   
void mergesort(int a\[\], int first, int last, int temp\[\])   
{   
 if (first < last)   
 {   
 int mid = (first + last) / 2;   
 mergesort(a, first, mid, temp);    //左边有序   
 mergesort(a, mid + 1, last, temp); //右边有序   
 mergearray(a, first, mid, last, temp); //再将二个有序数列合并   
 }   
}   
    
bool MergeSort(int a\[\], int n)   
{   
 int *p = new int\[n\];   
 if (p == NULL)   
 return false;   
 mergesort(a, 0, n - 1, p);   
 delete\[\] p;   
 return true;   
}  

> *   [白话经典算法系列之五 归并排序的实现](https://blog.csdn.net/morewindows/article/details/6678165/)

### [](#总结 "总结")总结

在数据结构和算法的路上，越走越远！~
