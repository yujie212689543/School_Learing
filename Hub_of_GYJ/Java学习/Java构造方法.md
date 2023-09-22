---
date created: 2023-09-21 18:47
tags:
  - "#类访问修饰符为默认"
  - "#构造函数初始化"
date updated: 2023-09-21 19:27
---

## 构造方法概述

构造方法是一种特殊的方法

- 作用：<mark style="background: #BBFABBA6;">创建对象 Student stu = **new Student();**</mark>
- 格式：
  public class 类名{
  ​    修饰符 类名( 参数 ) {
  ​ }
  }
- _功能_：主要是<mark style="background: #FFB86CA6;"><mark style="background: #FF5582A6;">完成对象数据的初始化</mark></mark>

_**示例代码**_
_定义类_

```java
class Student {                       #类访问修饰符为默认
    private String name;
    private int age;
    //无参构造函数
    public Student() {
    }
    //有参构造函数
    public Student(String name) {
        this.name = name;
    }
```

定义对象

```java
 public static void main(String[] args) {
        //创建对象
        Student s1 = new Student();
        
        //public Student(String name)
        Student s2 = new Student("林青霞");
```

---

<mark style="background: #FF5582A6;">_**注意**_</mark>

1. 当你创建了有参构造函数时，无参构造函数必须也要创建
2. 重要功能
   可以使用带参构造，为成员变量进行<mark style="background: #BBFABBA6;">初始化</mark>

```java
class Student {  
    private String name;  
    private int age;  
  
    public Student() {}  
  
    public Student(String name) {  
        this.name = name;  
    }  
  
    public Student(int age) {  
        this.age = age;  
    }  
  
    public Student(String name,int age) {  
        this.name = name;  
        this.age = age;  
    }  
  
    public void show() {  
        System.out.println(name + "," + age);  
    }  
}  
  
public class StudentDemo {  
    public static void main(String[] args) {  
        //public Student(String name,int age)  
        Student s4 = new Student("林青霞",30);  
        s4.show();  
    }  
}
```
```
在你的代码中，`Student s4 = new Student("林青霞",30);` 这行代码是在创建一个新的 `Student` 对象 `s4`。这里 `"林青霞"` 和 `30` 是传递给 `Student` 类构造函数的参数。
 在 `Student` 类中，你定义了一个构造函数 `public Student(String name,int age)`，它接受两个参数：一个 `String` 类型的 `name` 和一个 `int` 类型的 `age`。当你使用 `new Student("林青霞",30)` 创建对象时，“林青霞” 和 30 这两个参数就会传递给这个构造函数，并分别赋值给 `this.name` 和 `this.age`。   
```
#构造函数初始化 [[this关键字的使用.jpg]]
