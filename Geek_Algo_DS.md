# 前言

## 如何学习数据结构与算法

### 什么是数据结构？什么是算法？

从广义上讲，数据结构就是指一组数据的存储结构。算法就是操作数据的一组方法。

从狭义上讲，是指某些著名的数据结构和算法，比如队列、栈、堆、二分查找、动态规划等。这些都是前人智慧的结晶，我们可以直接拿来用。我们要讲的这些经典数据结构和算法，都是前人从很多实际操作场景中抽象出来的，经过非常多的求证和检验，可以高效地帮助我们解决很多实际的开发问题。

数据结构是为算法服务的，算法要作用在特定的数据结构之上。

我都会从实际场景出发，不仅教你“是什么”，还会教你“为什么”，并且告诉你遇到同类型问题应该“怎么做”。

### 学习的重点在什么地方？

首先要掌握一个数据结构与算法中最重要的概念（精髓）——**复杂度分析**。

- 如果你只掌握了数据结构和算法的特点、用法，但是没有学会复杂度分析，那就相当于只知道操作口诀，而没掌握心法。只有把心法了然于胸，才能做到无招胜有招！

最常用、最基础的20个数据结构与算法

- 10 个数据结构：数组、链表、栈、队列、散列表、二叉树、堆、跳表、图、Trie 树；
- 10 个算法：递归、排序、二分查找、搜索、哈希算法、贪心算法、分治算法、回溯算法、动态规划、字符串匹配算法。

在学习数据结构和算法的过程中，你也要注意，不要只是死记硬背，不要为了学习而学习，而是<u>要学习它的“来历”“自身的特点”“适合解决的问题”以及“实际的应用场景”</u>

学习数据结构和算法的过程，是非常好的思维训练的过程，所以，千万不要被动地记忆，要多辩证地思考，多问为什么。

### 一些可以让你事半功倍的学习技巧

1. 边学边练，每周花 1~2 小时集中攻关三节课涉及的数据结构和算法，全部写出来。
2. 主动提问、多思考、多互动。在留言区增加自己的留言。
3. 自我激励，每次学习完做一篇学习笔记。
4. 知识需要沉淀，不要想试图一下子掌握所有。沉下心不要浮躁，先把这些基础的数据结构和算法，还有学习方法熟练掌握后，再追求更高层次。

##  复杂度分析

大 O 时间复杂度实际上并不具体表示代码真正的执行时间，而是表示**代码执行时间随数据规模增长的变化趋势**，所以，也叫作**渐进时间复杂度**（asymptotic time complexity），简称**时间复杂度**。

我们通常会忽略掉公式中的常量、低阶、系数，只需要记录一个最大阶的量级就可以了。

### 时间复杂度分析

实际上，不管是以 2 为底、以 3 为底，还是以 10 为底，我们可以把所有对数阶的时间复杂度都记为 O(logn)。为什么呢？我们知道，对数之间是可以互相转换的，log3n 就等于 log32 * log2n，所以 O(log3n) = O(C * log2n)，其中 C=log32 是一个常量。

#### 复杂度分析的4个概念

1. 最坏情况时间复杂度：代码在最理想情况下执行的时间复杂度。
2. 最好情况时间复杂度：代码在最坏情况下执行的时间复杂度。
3. 平均时间复杂度：用代码在所有情况下执行的次数的加权平均值表示。
4. 均摊时间复杂度：在代码执行的所有复杂度情况中绝大部分是低级别的复杂度，个别情况是高级别复杂度且发生具有时序关系时，可以将个别高级别复杂度均摊到低级别复杂度上。基本上均摊结果就等于低级别复杂度。

#### 为什么要引入这4个概念？

1. 同一段代码在不同情况下时间复杂度会出现量级差异，为了更全面，更准确的描述代码的时间复杂度，所以引入这4个概念。
2. 代码复杂度在不同情况下出现量级差别时才需要区别这四种复杂度。大多数情况下，是不需要区别分析它们的。

# 算法与DS

## 数组

数组（Array）是一种线性表数据结构。它用一组<u>连续的内存空间</u>，来存储一组具有相同类型的数据。

### 容器能否完全替代数组

相比于数字，java中的ArrayList封装了数组的很多操作，并支持动态扩容。一旦超过存储容量，扩容时比较耗内存，因为涉及到内存申请和数据搬移。

数组适合的场景：
1）	Java ArrayList 的使用涉及装箱拆箱，有一定的性能损耗，如果特别关注性能（底层开发，如网络框架，性能优化），可以考虑数组

2）	若数据大小事先已知，并且涉及的数据操作非常简单，可以使用数组

3）	表示多维数组时，数组往往更加直观。

### 为什么下标从 0 开始？

如果下标从1开始，a[k] 的内存地址的计算公式：

`a[k]_address = base_address + (k - 1) * type_size`

从 1 开始编号，每次随机访问数组元素都多了一次减法运算，对于 CPU 来说，就是多了一次减法指令。

## 队列



# tips:

不为了做笔记而做笔记

很多时候我们并不是要去死记硬背某个数据结构或者算法，而是要学习它背后的思想和处理技巧，这些东西才是最有价值的