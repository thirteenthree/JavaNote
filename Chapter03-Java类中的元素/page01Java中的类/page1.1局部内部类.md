#### 3.1.1 局部内部类(定义在成员方法内的类)
```java
public class OuterClass {
    public void doSome(){
        int a=10;
        final int b=10; 
        class InnerClass{           //不能有访问控制修饰符修饰class
                          
            {
                System.out.println(a);
            }
            public  void doSome2(){
                System.out.println(a);
                System.out.println(b);
            }
        }
        InnerClass inner=new InnerClass();
        inner.doSome2();
    }
    public static void main(String[] args){
        OuterClass out=new OuterClass();
        out.doSome();
    }
}
```
* 局部内部类等同于局部变量.
* 不能用访问控制权限修饰符修饰类.
* 局部内部类中不能出现static;
* 局部内部类在使用局部变量的时候:
    - 不能修改变量值;
    - 使用final修饰(不使用final修饰,也能过);