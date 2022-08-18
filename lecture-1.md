# lecture-1

Database : it's a collection of data that's related to gathers in some way.

数据库的出现

* 模型化数据之间的关系
* 优化查找
* 语言无关（有自己的查询语言，SQL语句）
* 并发安全保证
* 安全性的保证

  假设在某条语句执行期间，机器有故障或者程序问题，怎么去推断数据的状态？

一个数据库管理系统能够使应用在数据库中存储或分析数据。

## 关系型数据库

所谓的关系可以用元组(tuple)的形式进行存储

将逻辑层和物理层分开

## 数据模型

* 关系型
* K/V
* 图
* 文档
* Column-family
* Array/Matrix(机器学习相关)

想了解更多关于数据模型，可以看《数据密集型应用》

## 关系型数据模型

* 结构（Structure）: The defintion of realtaions and their contents.
* 完整性（Integrity）: Ensure the databases's contents satisfy constraints
* Manipulation(操控，处理)： **How** to access and modify a database's contents.

NULL : the value is unknown.

Relation = Table, Tuple = record

**Primary keys** : unique attribute or set of attrubutes that can **uniquely identify** a single tuple.(内键)

外键（Foreign keys） : is a way to specify that antrribute from one realation has to exist in at least one tuple in **another realation**.

But realational caculus will come up if you be certain on in detail about query optimization.

### 基本运算符

* select

  Choose a **subset** of the tuples from a relation that **satisfies a selection** predicate（从关系中，挑选出符合查询调节的子集）
* projection

  **Generate a relation** with **tuples** that contains only the specified attributes（通过指明特定属性生成关系）
* union

  Generate a relation that contains all tuples **that appear in either only one or both input realtions**.（并集？）

  下节课会讨论SQL中UNION ALL和关系代数中UNION操作符的区别。
* intersection

  Generate a relation that contains only the tuples that **appear in both of the input relations**.（交集）

* difference  
  Generate a relation that contains only the tuples that **appear in the first and not the second of the input realtions** (R - S).

  可以看作过滤。
* product

  Generate a realtion that contains all possible **combination** of tuples from the input reations .(R x S)

  有时也被叫做笛卡尔积（Cartesian product），它在SQL被称为交叉连接（Cross Join）,暂时没理解，有点类似向量乘向量得到矩阵？比如(n * 1) * (1 *m) = n * m 。

  You never want to do this.一般出现在测试应用程序时，想要得到不同配置的所有不重复组合时。
* join

  Generaate a relation that contains all tuples are a combination of two ruples.

  这种Join被称为自然连接(Natural Join)

我们真正想做的在更高的级别告诉数据库我想要的答案，而不用指定数据库怎么去计算出我的答案。数据库内部隐藏了很多很多的东西，它会不断适应你的数据，可能会根据不同数据使用不同策略。

只讲了概念，具体想要了解应该看课本。
