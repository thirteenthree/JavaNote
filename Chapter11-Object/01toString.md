### 11.1 toString

#### 11.1.1 Object中的toString

Object中的toString方法返回:类名@java对象的内存地址经过哈希算法得出的int类型值再转换成十六进制;这个输出结果可以等同看做java对象在堆中的内存地址;

```Java
public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());    
    }
```
* System.out.println(obj)默认调用obj.toString方法;

#### 11.1.2 重写toString 