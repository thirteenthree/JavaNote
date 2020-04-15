### 5.2 访问控制修饰符


访问控制修饰符 |本类|同包|子类|其他包
  :-:   |:-:|:-: |:-: |:-:
public      |Y     |Y     |Y     |Y
protected   |Y     |Y     |Y     |N
default     |Y     |Y     |N     |N
private     |Y     |N     |N      |N

* 范围从大到小排序:public > protected > 默认 > private
* 访问控制权限修饰符可以修饰什么?
    - 属性(4个都能用)
    - 方法(4个都能用)
    - 类(public和默认能用,其它不行)
    - 接口(public和默认能用,其它不行)