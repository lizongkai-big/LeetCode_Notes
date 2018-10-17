Java 集合类 （动态增长）

1. Collection 存储元素
   1. List必须保持元素特定的顺序 
   2. Set不能有重复元素 
   3. Queue保持一个队列(先进先出)的顺序
2. Map 存储 k-v

list, set, queue, map都是abstract类型，不能被new

1. java提供的List就是一个"线性表接口"，**ArrayList**(基于数组的线性表)、**LinkedList**(基于链的线性表，同时具有双端队列、队列、栈的用法，功能非常强大)是线性表的两种典型实现
2. Queue代表了队列，Deque代表了双端队列(既可以作为队列使用、也可以作为栈使用)
3. 因为数组以一块连续内存来保存所有的数组元素，所以数组在随机访问时性能最好。所以ArrayList的内部以数组作为底层实现的集合在**随机访问**时性能最好。
4. 内部以链表作为底层实现的集合LinkedList在执行**插入、删除**操作时有很好的性能
5. 进行**迭代**操作时，以链表作为底层实现的集合比以数组作为底层实现的集合性能好