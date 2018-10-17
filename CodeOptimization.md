```java
// 简单的双重for循环，每次确定一个设备名称，然后遍历整个equipnamelist去确定它的下标
var count:int = 0; // 比较次数
for (var inx:int = 0; inx < acLen;){
	// 设备名称
	var equipName:String = ac.getItemAt(inx)[node];
    for (var i:int=0; i<eqLen; i++){
    	count ++;
        if(Shared.equipnamelist[i] == equipName){
        	equipIdArray.push(Shared.equip_idlist[i]);
            inx ++;
            break;
		}
	}
}
```

```java
// 因为ac和 equipnamelist的设备名称有可能顺序相同，所以尽可能减少比较次数，对一次外循环即可获取到所有设备id的情形有利
var count:int = 0; // 比较次数
for (var inx:int = 0, preInx:int = inx; inx < acLen;){
  // 设备名称  要初始化！！！
  var equipName:String = ac.getItemAt(inx)[node];
  for (var i:int=0; i<eqLen && inx < acLen; i++){
    count ++;
    // 为了减少内存取值次数，增加一个if判断，如果inx没有变化就不再重新获取equipName  对于如此小数量的问题，没必要这么纠结
    if(preInx != inx) equipName = ac.getItemAt(inx)[node];
    if(Shared.equipnamelist[i] == equipName){
      equipIdArray.push(Shared.equip_idlist[i]);
      preInx = inx;
      inx ++;
      /*break;*/ // break要去掉，不然还是从i=0开始，就不能减少比较次数了
    }
  }
}
```

