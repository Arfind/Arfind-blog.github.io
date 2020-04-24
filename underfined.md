---
title: 汇编
date: 2020-04-21 23:13:00
---

# 汇编基础语法总结

### 一.基本框架

### 二.基本运算

1.加

2.减法

3.乘法

通用寄存器表

4.除法

### 三.逻辑运算

### 四.循环

### 五.栈操作

指针寄存器

### 六.数据移动指令

### 七.比较指令

------

##### 一、基本框架

![](D:\blog\source\_posts\undefined\index\微信图片_20200424213657.png)

##### 二、基本运算

1.加

自增：INC寄存器名

加法：ADD目的寄存器，寄存器名或数值

2.减法

自减：DEC寄存器名

减法：SUB目的寄存器，寄存器名或数值

3.乘法

mul 倍数（寄存器）

![](D:\blog\source\_posts\undefined\index\微信图片_20200424223252.png)

倍数会决定计算结果的存储位置，也会决定被乘数的所在范围：

*当大小为1 byte*： AL * 8 BIT Source =AH  AL

*当大小为2 byte*： AX * 16 BIT Source = DX  AX

*当大小为4 byte:*    EAX  *  32 BIT Source  =  EDX    EAX

4.除法

除法：div除数（分母，寄存器）

其中Quotient是商，Remainder是余数，Divisor是除数

类似乘法，除数也会有类似的作用

​                             16 bit dividend            Quotient      Remainder

*当大小为1 byte*： AX / 8 bit dividend   =     AL      And    AH

​                             32 bit dividend 

*当大小为2 byte*：  DX * AX  /  16 bit dividend   =   AX  And   DX

​                             64 bit dividend

*当大小为4 byte*:    EDX*EAX / 32 bit dividend    =   EAX   And   EDX

##### 三、逻辑运算

语句和加法类似，将运算结果放入operand 1 (操作数1)

| 序号 |  指令   |          格式           |
| :--: | :-----: | :---------------------: |
|  1   |  AND与  | AND operand 1,operand 2 |
|  2   |  OR或   | OR operand 1, operand 2 |
|  3   | XOR异或 | XOR operand 1,operand 2 |
|      |  NOT非  |      NOT operand 1      |

##### 四、循环

；注释

l1 标签（表示这是一个循环）

<loop body>:需要循环的语句

loop l1：循环结束

![](D:\blog\source\_posts\undefined\index\1.png)

例子：

![](D:\blog\source\_posts\undefined\index\循环.png)



##### 五、栈操作

出栈：push 寄存器或数值

入栈：pop目的寄存器

指针寄存器

（记住EBP中的B是Base,代表底部（栈底））

​                                                          pointer registers

​                            31       16   15                 0

|   ESP   |      |   SP   | Stack pointer    |
| :-----: | ---- | :----: | ---------------- |
| **EBP** |      | **BP** | **Base pointer** |

##### 六、数据移动指令

赋值：mov 目的寄存器  寄存器或数值

传地址: lea 目的寄存器   操作数

lea  eax ,  dword   ptr    ss   :[esp]

交换：xchg 操作数  操作数（类似lea)

##### 七、比较指令

相减比较：cmp 目的寄存器   寄存器

相与比较： test 目的寄存器   寄存器