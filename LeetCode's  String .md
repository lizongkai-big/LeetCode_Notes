LeetCode's  String 

1. **length()**

2. toCharArray()

3. charAt()

4. trim()

5. 截取字符串

  1. split(String regex) 
    1. 这个参数并不是一个简单的分割用的字符，而是一个正则表达式
    2. 而"." "|" "*" "+"都是转义字符，必须得加"\\\";
    3. 且regex不像在python里可为空
  2. substring()

6. indexOf() 

7. contains() Returns true if and only if this string contains the specified sequence of char values.

   ```java
   public boolean contains(CharSequence s) {
       return indexOf(s.toString()) > -1;
   }
   ```

8. String VS Char

   1. String s =  "blabla";

   2. Char c = 'x';

   3. ```java
      // Char <--> String
      String str = "abc";
      Char[] charArray = str.toCharArray();
      int length = charArray.length;
      String s1 = new String(charArray);
      String s2 = String.valueOf(charArray);
      ```

   4. ​

   5. ​

   6. ​

9. String VS StringBuilder

   1. String 是静态的，如果要拼接字符串最好用StringBuilder，字符串直接相加也能实现拼接字符串的效果，但实际上底层还是用StringBuilder实现，不适合大量地拼接
   2. StringBuilder 
      1. append(String)
      2. toString()
      3. reverse()

10. String <--> int

  ```java
  int i = Integer.parseInt([String]);
  int i = Integer.parseInt([String], [in radix]);
  int i = Integer.valueof(my_str).intValue();

  String s = String.valueOf(i); // 利用String类提供的工厂方法
  String s = Integer.toString(i);
  String s = "" + i; // java的toString机制
  ```

11. int -> char 

   ```java
   char c = (char)(a + '0');
   int i = int i = Integer.parseInt("" = c);
   ```

   ​





1. 明显后者更简洁

```java
if(rl == 0 && ud == 0)
  return true;
else
  return false;	
```

​	等价于

```java
return rl == 0 && ud ==0;
```

2. 这就不对了，感情i不管等于几，都结束呗

```java
for(int i = 0; i < len; i ++){
  //blabla
  if(i == step)
    break;
  else // 和之后的每个子串相比都相等，则子串个数为subNum可行
    return true;
}
```

​	这也是不对啊，跳出循环的时候，i == str.length()恒成立啊！

```java
for(; i < str.length(); i ++){
  if(pre == str.charAt(i)){
    count ++;
  }
  else{
    // count + pre
    sb.append((count + "") + pre);
    count = 1;
  }
  pre = str.charAt(i);
}
if(i == str.length()){
  sb.append((count + "") + pre);
}
```

3. 以下两块代码等价，目的都是判断字符串s，长度totalLen, 是否可通过步长为step( = totalLen / subNum)的子串的重复构成，如“abcabcabc”可由“abc”重复构成；第二种方法是拿第一个子串和之后的每个子串相比，很麻烦，复杂度为O(n)；而第一种方法从思路上讲，就是简单粗暴，反正你是判断能不能由当前子串构成，好，我就假设你可以，然后就第一个子串之后的部分+第一个子串，如果和字符串本身相等，则可以构成；本质上是Arrays.copyOfRange时间复杂度为O(1)

```java
if(s.equals(s.substring(step, totalLen) + s.substring(0, step)))
  return true;   
```

```java
int i = 0;
for(; i < step; i ++){ // 拿第一个子串和之后的每个子串相比
  char temp = charArr[i];
  int j = 0;
  for(; j < subNum; j ++){ // 第一个子串的第i字符与之后每个子串的第i个字符相比
    if(temp != charArr[i + j * step]) // 不等就说明子串个数为subNum不对，跳出循环
      break;
  }
  if(j != subNum)
    break;
}
if(i == step)// 和之后的每个子串相比都相等，则子串个数为subNum可行
  return true;
```

4. 以前只懂得获取数字低位到高位，要想获取高位到低位，只好先获取整个数字的位数，这样通过移动数组的下标来填充低位（方法二）；相比之下，方法一6得不行！

```java
for(char c:Integer.toString(count).toCharArray())
  chars[write++]=c;
```

```java
// tmp: i 占的位数
int tmp = 0;
int temI = i;
while(temI > 0){
  temI = temI / 10;
  tmp ++;
}
for(int j = 1; i > 0; j ++){
  chars[inx + tmp - j] = (char)(i % 10 + '0');
  i = i / 10;
}
```

5. 截取+拼接字符串 811. Subdomain Visit Count 方法二是靠split分割“.”，然后为了构建domain还要靠StringBuilder拼接，老麻烦了；相比之下，方法一，使用indexOf来判断“.”的存在，然后逐步获取domain，只靠substring截取，不用拼接，6啊

```java
String domain = cp[1];
while (domain.indexOf(".") != -1) {
  int idx = domain.indexOf(".");
  if (!map.containsKey(domain)) {
    map.put(domain, 0);
  }
  map.put(domain, map.get(domain) + freq);
  domain = domain.substring(idx + 1);
}
if (!map.containsKey(domain)) {
  map.put(domain, 0);
}
```

```java
String[] domains = cp[1].split("\\.");
int len = domains.length;
for(int i = len - 1; i >= 0; i --){
  StringBuilder d = new StringBuilder("");
  // 构建一级domain之后的domain
  for(int j = i; j < len; j ++){
    d.append(domains[j]);
    if(j != len - 1)
      d.append(".");
  }
  String key = d.toString();
  if(maps.get(key) == null){
    maps.put(key, times);
  }
  else{
    maps.replace(key, maps.get(key) + times);
  }
}
```

6. 长度不同的两个二进制数字的字符串，如何去相加？无需考虑长度，只要一个while循环即可搞定。

```java
// 确定长的字符串：让a指向长的字符串
int j = lenb - 1;
int i = lena - 1;
// 以a的长度为标准
for(; i >= 0; i--){
  // 短字符串b不可以相加
  if(j < 0 && i >= 0){
    ...
  }
  // 短字符串b还可以相加
  for(; j >= 0; j--){
    ...
  }
}
```

```java
int j = lenb - 1;
int i = lena - 1;
while(i >= 0 || j >= 0){
  if(i >= 0) ...;
  if(j >= 0) ...;   
  i --;
  j --;
}
```

7. 在String Compression中，对于非尾字符，while 与 for循环本身没区别，对于最后一个元素的统计数字，单循环中会处理不到，只好在for循环外进行补救；如何不用补救呢？使用代码2中的嵌套循环即可。本质上是嵌套循环和单循环的区别，不是while和for的优劣差；习惯上是使用代码1，但不要忘了处理最后一个字符。


```java
for(int i = 1; i < chars.length; i ++){
  if(chars[i] == pre){
    count ++;
  }
  else{
    doSomething();
  }
}
// 很容易忘记处理最后一种字符(or something)
doSomething();
```

```java
while(end < len){
  ...
  while( end < len && chars[end] == curr){
    end++;
    ...
  }
  doSomething();
}
```

8. 字符串反转

```java
private void swap(char[] arr, int l, int r) {
  while (l < r) {
    char temp = arr[l];
    arr[l++] = arr[r];
    arr[r--] = temp;
  }
}
```

9. ​


