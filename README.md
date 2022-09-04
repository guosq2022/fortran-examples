# fortran examples

## usage

### download

命令行中输入

```bash
git clone git@github.com:Pjer-zhang/fortran-examples.git
```

或者直接在网页上下载zip程序包

### usage tip

对于依赖module的程序在程序内写use $(module_name)，编译的时候需要再次编译模块文件，命令如下

```bash
gfortran $(module_name).f90 main.f90
```

例如

```bash
gfortran ../subroutines/typedef.f90 ../subroutines/integrate.f90 hw_9_1.f90
```

###usage
新增Makefile之后，可以批量编译，上一步完成之后可以在project的根目录上输入

```bash
make
```

默认不加参数的情况下是编译已经写入makefile里的所有文件

当然也可以只编译某一次作业，可以在make后面加参数

```bash
make hw23 
```

编译作业hw_2_3.f90，在makefile里已经解决了依赖关系，所以在用make编译执行编译命令的时候不用再考虑module之间的依赖关系

### 关于python中的fortran

可以把fortran程序编译成链接库，在python中使用import $(module_name)引用之后使用，bash中使用f2py命令进行编译

```bash
f2py -c -m $(module_name).py

```

一个小demo：

```python
#/usr/bin/env python

import numpy as np
import inte  #fortran compiled module
x=np.arange(2,3,0.01)
fx=np.sin(x)*np.exp(x)
print inte.simp_inte(fx,2,3) #inte 里的 simpson 积分函数

```

## files

### compile control

- Makefile  管理编译命令的文件

### homework

- hw_2_3.f90 逻辑运算符运算
- hw_2_4.f90 二元一次方程求解
- hw_3_1.f90 分段函数求值
- hw_3_2.f90 条件选择
- hw_3_4.f90 goto语句循环
- hw_4_1.f90 数列函数求值 (use module)
- hw_4_2.f90 泰勒展开求sin (use module)
- hw_5_1.f90 成绩分段统计
- hw_5_2.f90 矩阵操作
- hw_6_0.f90 辗转相除
- hw_6_1.f90 三维向量叉乘
- hw_6_2.f90 平方序列求和
- hw_6_3.f90 e指数函数泰勒展开
- hw_6_4.f90 素数判断 素数因素分解
- hw_6_5.f90 求水仙数
- hw_7_0.f90 不定方程求整数解（勾股数）
- hw_8_2.f90 文件中顺序插入
- hw_9_1.f90 数值积分(use module)
- hw_9_2.f90 函数求零点(use module)
- hw_9_3.f90 拉格朗日插值(use module)
- hw_10_.f90 hash表散列搜索
- matrix.txt 矩阵操作（5.2）的数据文件
- insert.txt 顺序插入（8.2）的数据文件

### python bridge

- inte_lib_py.f90  适用于python调用的积分常用函数
- integrate.py     使用python调用fortran编译的链接库（demo）

### subroutines(modules)

- interp.f90        插值函数（拉格朗日插值）
- integrate.f90     积分常用函数（函数模块）
- typedef.f90       定义类型和常数 （定义模块）
- zerosolve.f90     函数求零点模块（函数模块）
- sortreal.f90      排序模块（希尔排序，选择排序）

![](https://github.com/Pjer-zhang/fortran-examples/blob/master/image/web.png)

[My profile](http://home.ustc.edu.cn/~pjer1316)
[My blog](http://pjer.blog.ustc.edu.cn)
