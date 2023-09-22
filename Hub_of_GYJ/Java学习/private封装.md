---
date created: 2023-09-21 19:08
tags:
  - '#封装概念'
  - '#private使用'
date updated: 2023-09-21 19:32
---

## 封装思想

1. _**封装**_   概述是面向对象三大特征之一（<mark style="background: #BBFABBA6;">封装，继承，多态</mark>）       #封装概念

   **对象代表什么，就得封装对应的数据，并提供数据对应的行为**

2. 封装代码实现 将类的某些信息隐藏在类内部，不允许外部程序直接访问，而是<mark style="background: #FFB86CA6;">通过该类提供的方法</mark>来实现对隐藏信息的操作和访问 成员变量private，提供对应的getXxx()/setXxx()方法

---

## private

```
private是一个修饰符，可以用来修饰成员（成员变量，成员方法）
```

- 被private修饰的成员，只能在本类进行访问，针对private修饰的成员变量，如果需要被其他类使用，提供相应的操作
  #private使用
  - 提供“get变量名()”方法，用于获取成员变量的值，方法用public修饰
  - 提供“set变量名(参数)”方法，用于设置成员变量的值，方法用public修饰

- <font color="#e5b9b7">private封装主要是为防止别人随意更改数据</font>

- <font color="#e5b9b7">当用了private后下面必须得用方法</font>

```java
class Student {
    //成员变量
    String name;
    private int age;         //private使用

    //*提供get/set方法
    public void setAge(int a) {      
        if(a<0 || a>120) {
            System.out.println("你给的年龄有误");
        } else {
            age = a;
        }
    }
    public int getAge() {
        return age;
    }
}
public class StudentDemo {
    public static void main(String[] args) {
        //创建对象
        Student s = new Student();
        //给成员变量赋值
        s.name = "林青霞";
        
        s.setAge(30);
        //调用show方法
        s.show();
    }
}
```
