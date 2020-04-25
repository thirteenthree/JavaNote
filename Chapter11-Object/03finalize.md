### 11.2 Object中的finalize
```Java
//垃圾自动回收
System.gc();
```

* finalize方法每个java对象都有.
* finalize方法不需要程序员去调用,由系统自动调用.
* java对象如果没有更多的引用指向它,则该java对象成为垃圾数据,等待垃圾回收器的回收,垃圾回收器在回收这个java对象之前会自动调用该对象的finalize方法.
