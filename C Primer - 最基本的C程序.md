# 02. C Primer 最基础的C语言

### 第二章 C语言基础

#### 2.1 简单的C程序示例

 文章中写了一个简单的程序

```C
#include<stdio.h>
int main(void){
 int num;
 num=1;
 
 printf(“hello world”);
 
 return 0;
}
```



#### 2.2 示例解析

##### 2.2.1 第一遍： 快速概要

```C
#include<stdio.h>   //预处理指令：包含另一个文件stdio.h, 它是C编辑器软件包的标准部分，它提供键盘的输入和屏幕的输出

//是函数构成了C语言的基本模块
int main(void){     //主函数：总是第一个被调用的函数(void表示没有参数)
 int num; //声明
 num=1;   //赋值
 
 printf("hello world\n"); //‘\n’表示把光标移至下一行
 printf("my favorite number is %d.\n",num); //把num的值镶嵌在双括号括起来一并打印。
 return 0;
}
```



##### 2.2.2 第二遍：程序的细节（重点）

1. 关于预编译 

```C
第一行，就是把stdio.h文件的所有内容都输入改行所在的位置。是指上这是一种"拷贝-粘贴"的过程。

#include是预处理指令，通常C语言会在编译之前对源代码做一些准备工作，即预处理工作。

所有的编译器软件包都会提供这个文件stdio.h，文件包括标准的输入和输出函数。

//关于一直搞不清楚的头文件，库文件，源文件
头文件：头文件包含了编译器创建最终可执行程序用到的信息。说白了就是源文件和库文件的连接器

一般的程序会提供库文件（是预编译好的函数），以及头文件（库文件的接口，一些声明）
    这个时候注意一下，头文件中的声明有变量的声明还有函数的声明。
    切记！！！不能在头文件中实现函数或者变量定义，只能声明。不然就会出现“多次定义”的错误。
    
//为什么会出现多次定义的错误呢？
    因为头文件本质上是把多个源文件或者库文件连接到一起，如果在头文件中定义变量，那就会出现在每个源文件中加一份，这样链接到一起的时候，就会出现多次定义「见图2」。
    
//gcc 的时候不用加入头文件。
```

![image-20221022163431574](C:\Users\Chris Xie\AppData\Roaming\Typora\typora-user-images\image-20221022163431574.png)

如果我把变量定义在头文件里：

![image-20221022163706879](C:\Users\Chris Xie\AppData\Roaming\Typora\typora-user-images\image-20221022163706879.png)



2. 关于main() 函数：唯一的进入程序的选择

```c
int main(){
  //1. int 是返回到哪里 -> 操作系统 (第六章)
  //2. () 括号中可以从外界的命令行接受参数
}
```



3. 关于声明 （重点）

```c
变量的声明就是创造一个名叫num的变量并且指定它的类型，指定类型是为了在内存中分配内存。
注意：数据类型和变量名都有命名规则。
    
C语言一般都将声明和定义分开。
    int doors;
    doors=10;

//旧版本会把声明写在所有的语句前面
//C99 原来额标准是把所有的声明到置于块的顶部, C99之后允许在需要的时候才声明变量。
```



4. 关于赋值 （重点）

```C
在声明的时候，编译器给计算机内存中为num的变量预留了空间，然后把值放在预留的位置。
// 在C99 中，如果用malloc在堆中开辟一个新的块，并没有进行赋值操作，那么默认赋值是随机值
// 在C99中，如果在栈中声明一个变量，但是没有进行赋值，那么默认赋值是0
```



5. 关于printf() 函数

```c
printf()本质上是一个函数，()内部是字符串，相当于打印这个字符串
//当然也也支持\n 等转义字符
//占位符：说白了%d就相当于在打印的时候先把位置占上，之后在补。
    在这一点上，C语言还声明了占位的时候，是什么样的类型。比如%d表示十进制整数。当然也包括小数打印或者十六进制打印。
```



6. return语句

```c
这通常是程序的最后一句话：目的是表明返回的数。
// 如果在main之后没有写return语句，那么会默认为返回0；
```





#### 2.3 简单的结构程序

```
这个部分就不用多说了;
```



#### 2.4 提高程序可读性的技巧

```c
//在起名字的时候，起有意义的名字
//写注释
//空行增加可读性(比如在连续的声明和连续的赋值之后会出现空行)
//每个语句占一行
```





#### 2.7 调试程序

##### 2.7.1 语法错误

##### 2.7.2 语义错误

##### 2.7.3 程序状态 （学会debugger）



#### 2.8 关键字和保留标识符

| auto     | extern   | short    | while          |
| -------- | -------- | -------- | -------------- |
| break    | float    | signed   | _Alignas       |
| case     | for      | sizeof   | _Alignof       |
| char     | goto     | static   | _Atomic        |
| const    | if       | struct   | _Bool          |
| continue | inline   | switch   | _Complex       |
| default  | int      | typedef  | _Generic       |
| do       | long     | union    | _Imaginary     |
| double   | register | unsigned | _Noreturn      |
| else     | restrict | void     | _Static_assert |
| enum     | return   | volatile | _Thread_local  |



#### 2.9 关键概念

#### 2.10 本章小结

#### 2.11 复习题

#### 2.12 编程练习

```c
//1. 打印姓名(训练printf函数)
#include <stdio.h>
int main() {

    //Ma Zhang

    printf("Ma Zhang\n");
    printf("Ma\nZhang\n");
    printf("Ma");
    printf("Zhang");
}

//2. 打印地址和姓名
//3. 把年龄转换成天数
#include <stdio.h>
int main() {

    int age,day;
    scanf("%d",&age);

    day=365*age;
    printf("%d",day);
}


//4.编写一条程序，生成以下的输出
#include <stdio.h>

void jolly();
void deny();

int main() {
  jolly();
  jolly();
  jolly();
  deny();
}

void jolly(){
    printf("For he's a jolly good fellow!\n");
}

void deny(){
    printf("Which nobody can deny\n");
}

//5.同第四题目原理，但是注意，

//6. 写一个程序表示一个数，数的2倍，数的平方
#include <stdio.h>

int main() {
   int toes;

   toes=10;
   printf("toes is %d, 2*toes is %d, toes^2 is %d\n",toes, toes*2,toes*toes);
}
//7.8.都过于简单，省略

```

