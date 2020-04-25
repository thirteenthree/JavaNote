### 12.1 String在内存中的存储



#### 12.1.1 方法一创建字符串对象

```Java
String s="abcd";
```

* 改方法创建的字符串存储在方法区的字符串常量区中;

#### 12.1.2 方法二创建字符串对象

```Java
String s=new String("abcd");
```

* 改方法创建的字符串有两个存储空间:
  * 在方法区的字符串常量区创建这个字符串;
  * 同时在堆内存也创建一个字符串对象,指向方法区的字符串地址;

#### 12.1.3 字符串的增删改查

* ~~增~~		拼接字符串

  * ```Java
    String s1 = "abc";
    String s2 = s1+"def";
    ```


* ~~删~~ 	  提取子字符串


  * ```Java
    String s2 = s1.substring(int beginIndex, int endIndex);
    ```

* ~~改~~

* 查

  * ```Java
    String s2 = s1.charAt(int index);
    
    ```

  * 



#### 12.1.4 

```Java
String a=new String("abc");
String b=new String("abc");
```

* 一共创建**三个对象**:方法区一个,堆内存两个;



