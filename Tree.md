### Tree

1.  不能对空节点取其左右节点  但如何避免这种繁琐的判断？使用 ?=  Mine **VS** God 

```java
// 不能对空节点取其左右节点            
if(t1 == null){
  res.left = mergeTrees(null, t2.left);
  res.right = mergeTrees(null, t2.right);    
}
else if(t2 == null){
  res.left = mergeTrees(t1.left, null);
  res.right = mergeTrees(t1.right, null);
}
else{
  res.left = mergeTrees(t1.left, t2.left);
  res.right = mergeTrees(t1.right, t2.right);
}
```

```java
res.left = mergeTrees(t1 == null ? null : t1.left, t2 == null ? null : t2.left);
res.right = mergeTrees(t1 == null ? null : t1.right, t2 == null ? null : t2.right);
```

2. 1. 不需要那么详细的判断
   2. 不那么详细地判断，处理起来倒是更方便！

```java
TreeNode res;
if(t1 == null && t2 == null){
  res = null;
}
else if(t1 == null || t2 == null){
  res = t1 == null ? t2 : t1;
}
else{
  TreeNode node = new TreeNode(t1.val + t2.val);
  res = node;
}
if(res != null){
  // 如何避免这种繁琐的判断？1. 使用?=  2. 更高超的方法：从函数结构上改变
  res.left = mergeTrees(t1 == null ? null : t1.left, t2 == null ? null : t2.left);
  res.right = mergeTrees(t1 == null ? null : t1.right, t2 == null ? null : t2.right);
}
return res;
```

```java
if(t1 == null)
  return t2;
if(t2 == null)
  return t1;
TreeNode res = new TreeNode(t1.val + t2.val);
res.left = mergeTrees(t1.left, t2.left);
res.right = mergeTrees(t1.right, t2.right);
return res;
```

3. 萨芬的

```java

```











