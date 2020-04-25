### 13.2 Collection中常用的方法

* 没有使用"泛型"之前,Collection中可以存储Object的所有子类
* 使用"泛型"之后,Collection只能存储某个具体类型



#### 13.2.1 集合的增删改查

* 创建集合对象

  * ```Java
    Collection c = new ArrayList();
    //Collection是接口,不能直接new Collection();
    ```

* 增

  * ```Java
    boolean add(Object e);
    ```

  * 

* 删

  * ```Java
    void clear();	//删除集合所有元素;
    ```

  * ```Java
    boolean remove(Object o);//删除集合某个元素
    //调用contains方法;
    ```
  ```
    
  
    
  * 
  ```

* 改

  * 

* 查

  * ```Java
    int size();`//获取集合元素个数
    ```

  * ```Java
    boolean contains(Object o);	//判断是否包涵某个元素
    //底层使用equals();
    ```

    

  * 

#### 13.2.1 集合迭代方式

```Java
//获取集合迭代器;
Iterator it = c.iterator();

//返回迭代的下一个元素
it.next();

//判断迭代下一个是否有元素;
it.hasNext();
```



 #### 13.2.2 增强for方式



```Java
for(元素类型 变量名 : 数组或集合){

}
```

