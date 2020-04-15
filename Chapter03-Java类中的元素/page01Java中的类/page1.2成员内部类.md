#### 3.1.2 成员内部类(非静态内部类)
```php
public class OuterClass {
    public void doSome(){
        InnerClass inner=new InnerClass();
        inner.doSome2();
    }
    public static void doSome3(){
        OuterClass out=new OuterClass();
        OuterClass.InnerClass inner=out.new InnerClass();
        inner.doSome2();
    }
    static int a=10;
    class InnerClass{

        {
            System.out.println(a);
        }
        public void doSome2(){
            doSome3();
            System.out.println(a);
        }
    }
}
```
- 成员内部类可以等同看做实例方法.
- 可以用访问控制权限的修饰符修饰.
- 类中不能出现static.
- 调用成员内部类:
    - 在类方法中: 首先实例化外部类名,然后实例化内部类名;
        ```
        OuterClass out=new OuterClass();    //首先实例化外部类名
        OuterClass.InnerClass inner=out.new InnerClass();   //然后实例化内部类名
        inner.doSome2();
        ```
    - 在实例方法中:实例化内部类
        ```
        InnerClass inner=new InnerClass();
        inner.doSome2();
        ```
- 作用域(等同于实例方法):
    * 成员内部类访问外部类的:类变量,实例变量.
    * 成员内部类访问外部类的:类方法,实例方法.
