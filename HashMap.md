```java
HashMap<String, Integer> maps = new HashMap<String, Integer>();
maps.put("xx", 1);
maps.get("xx"); // 1
maps.get("yy") == null; // true
maps.containsKey("yy"); // false
maps.replace("xx", 2);
// 遍历 方法一
Iterator iterator = map.keySet().iterator();
while (iterator.hasNext()) {
  String key = (String)iterator.next();
  System.out.println(key + " " + map.get(key));
}
// 方法二
for(Map.Entry entry: maps.entrySet()){
  String k = (entry.getValue() + " ") + entry.getKey();
  System.out.println(k);
}

```

