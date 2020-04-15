#### 3.1.3 静态内部类
```php
public class OuterClass {
    public void doSome(){
        InnerClass inner=new InnerClass();
        inner.doSome2();

    }
    public static void doSome3(){
        
        OuterClass.InnerClass inner=new OuterClass.InnerClass();
        inner.doSome2();
    }
    static int a=10;
    static class InnerClass{

        {
            System.out.println(a);
        }
        public void doSome2(){

            System.out.println(a);
        }
    }

```

- 静态内部类可以等同看做类方法.

- 不能出现static.
- 调用静态内部类:
    * 类方法和实例方法都可采用以下方法
        - 方法1: 实例化外部类名,实例化内部类名;
        ```
        OuterClass out=new OuterClass();
        OuterClass.InnerClass inner=out.new InnerClass();
        inner.doSome2();
        ```
        - 方法2:实例化内部类名;
        ```
        InnerClass inner=new InnerClass();
        inner.doSome2();
        ```
- 作用域(等同于类方法):
    * 直接访问外部类的类变量.
    * 直接访问外部类的类方法,或实例化静态内部类名访问.