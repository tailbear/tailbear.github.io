

# 代码整洁之道读书笔记

## 第1章 代码整洁的重要性

勒布朗（LeBlanc）法则：稍后等于永不（Later equals never）。

代码混乱的代价：代码的不规范随着项目的推进，生产力随时间的推移快速降低。

![image-20200727092536544](C:\Users\xiongliang\AppData\Roaming\Typora\typora-user-images\image-20200727092536544.png)



简单代码的重要顺序：1.能通过所有测试；2.没有重复代码；3.体现系统中的全部设计理念；4.包括尽量少的实体，比如类、方法、函数等。

例子：例如“在集合中查找某物”。不管是雇员记录数据库还是名-值对哈希表，或者某类条目的数组，我们都会发现自己想要从集合中找到某一特定条目。一旦出现这种情况，我通常会把实现手段封装到更抽象的方法或类中。

### 自我总结：通过访谈名人的方式，介绍了代码整洁的意义。

## 第二章 有意义的命名

1.名副其实（体现本意）

2.类名（名称或名称短语）

3.方法名（动词或动词短语）

4.别使用无意义或意义模糊的命名



## 第三章 函数

函数应该短小，一个函数20行封顶，每行最多150个字符。函数的缩进层级不该多于1-2层。

用异常代替返回错误码。

如错误码形式：

```java
if (deletePage(page) == E_OK) {
if (registry.deleteReference(page.name) == E_OK) {
if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
logger.log("page deleted");
} else {
logger.log("configKey not deleted");
}
} else {
logger.log("deleteReference from registry failed");
}
} else {
logger.log("delete failed");
return E_ERROR;
}
```

异常形式：

```java
try {
deletePage(page);
registry.deleteReference(page.name);
configKeys.deleteKey(page.name.makeKey());
}
catch (Exception e) {
logger.log(e.getMessage());
}
```

### 结构化编程

结构化编程规则：Dijkstra认为，每个函数、函数中的每个代码块都应该有一个入口、一个出口。遵循这些规则，即：每个函数中只该有一个return语句，循环中不能有break或continue语句，而且永永远远不能有任何goto语
句。



### 自我总结：

1.函数的第一规则：要短小（20行）。

2.if，else，while等语句内只有一行。

3.函数只做一件事（每个函数一个抽象层级）。

4.switch通过多态重构。

5.函数名称使用描述性的语言。

6.函数的参数最好控制在2个以内。

7.避免重复，导致代码臃肿，难以修改。

8.编写函数需要打磨，如同写文章。



## 第四章：注释

“别给糟糕的代码加注释——重新写吧。”——Brian W. Kernighan与P. J. Plaugher

1.唯一真正好的注释是你想办法不去写的注释。

好的注释包含：

- 提供信息。
- 解释意图。
- 阐述晦涩难明的参数或返回值。
- 警告某些操作会带来的风险。
- TODO注释用来提示暂未完成的工作。



2.坏的注释：坏注释都是糟糕的代码的支撑或借口，或者对错误决策的修正

- 能用函数或变量就别用注释

  

## 第五章 格式

### 向报纸学习

1.从上往下读，从左往右读

2.源文件在最顶端给出高层次的概念和算法，细节往下逐次展开，直到最底层的函数和细节



### 垂直格式

**1.变量声明。**变量声明尽可能地靠近其使用的位置。但在类中，应该统一放在顶部位置。

**2.相关函数。**若某个函数调用了另外一个，就应该把它们放到一起，而且调用者应该尽可能放在被调用者上面。

**3.相关概念。**概念相关的代码应该放到一起。相关性越强，彼此之间的距离越短。



### 横向格式

注意缩进

