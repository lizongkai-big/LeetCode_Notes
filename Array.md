Array 数组

1. 声明、创建
2. 初始化数组：分配空间与赋值分步进行、分配空间，同时赋值
3. 访问数组：下标访问、增强型for循环获得形参
4. 获取长度：length
5. 复制数组：System.arraycopy(src, srcPos, dest, destPos, length)

-------------------

java.util.Arrays 是针对数组的工具类，可以进行 排序，查找，复制填充等功能。 

1. copyOfRange(int[] original, int from, int to) 数组复制 返回一个数组
2. sort()
3. binarySearch()
4. fill()
5. equals()
6. toString() 一维数组 -> 字符串
7. deepToString() 二维数组 -> 字符串


两个有序数组的**中位数**，假设两个数组的长度分别是m和n，我们分别找第 (m+n+1) / 2 个，和 (m+n+2) / 2 个，然后求其平均值即可，这对奇偶数均适用。