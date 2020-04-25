### 11.2 equals方法

#### 11.2.1 Object中的equals

```Java
public boolean equals(Object obj) {
        return (this == obj);
    }

```

* Object中的equals方法 "==" 两边如果是引用类型,则比较的是两个引用对象的**内存地址**;



#### 11.2.2 重写equals

```Java

public boolean equals(Object obj){
        
        if(this==obj) return true;
        
        if(obj instanceof YourClass){
            YourClass s = (YourClass)obj;
            /*
            自定义两者相等的条件,其中YourClass为自己定义的类,
             */
        }
        
        return false;
    }
```