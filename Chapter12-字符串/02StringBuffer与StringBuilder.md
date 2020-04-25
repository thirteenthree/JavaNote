### 12.2 StringBuffer与StringBuilder



#### 12.2.1 StringBuffer默认构造方法

```Java
StringBuffer stringBuffer = new String Buffer();
```

#### 12.2.2 StringBuilder默认构造方法

```Java
StringBuilder stringBuilder = new String Builder();
```



#### 12.2.3 String与StringBuffer,StringBuilder区别

* String,StringBuffer,StringBuilder底层都是byte[]数组,但是String的byte[]被**final**修饰;
* String的对象不可变;
* StringBuffer与StringBuilder动态可变的,默认负载因子(容量)**16**;
* StringBuffer是**线程安全**的;