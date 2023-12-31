---
date created: 2023-09-20 18:37
tags: []
date updated: 2023-09-20 18:37
---

## 定义

类由**属性**和**行为**两部分组成

=======================================
_**实际开发中建议<mark style="background: #BBFABBA6;">一个文件中定义一个类</mark>**_

=========================================

### 定义步骤

> 1. 定义类
> 2. 编写类的成员变量
> 3. 编写类的成员方法

```java
public class 类名 {
    // 成员变量
    变量1的数据类型 变量1；
    变量2的数据类型 变量2;
    …
    // 成员方法
    方法1;
    方法2;	
}
```

_**示例代码：**_  （类里面定义方法）

```java
/*
    手机类：
        类名：
        手机(Phone)

        成员变量：
        品牌(brand)
        价格(price)

        成员方法：
        打电话(call)
        发短信(sendMessage)
 */
public class Phone {
    //成员变量
    String brand;
    int price;

    //成员方法
    public void call() {
        System.out.println("打电话");
    }

    public void sendMessage() {
        System.out.println("发短信");
    }
}
```

#### 创建对象

- 格式：
  - <mark style="background: #FF5582A6;">类名 对象名=new 类名();</mark>
- 调用成员对象的格式：
  - 对象名.成员变量
  - 对象名.成员方法
- _**演示代码**_

```java
/*
    创建对象
        格式：类名 对象名 = new 类名();
        范例：Phone p = new Phone();

    使用对象
        1：使用成员变量
            格式：对象名.变量名
            范例：p.brand
        2：使用成员方法
            格式：对象名.方法名()
            范例：p.call()
 */
public class PhoneDemo {
    public static void main(String[] args) {
        //创建对象
        Phone p = new Phone();

        //使用成员变量
        System.out.println(p.brand);
        System.out.println(p.price);

        p.brand = "小米";
        p.price = 2999;

        System.out.println(p.brand);
        System.out.println(p.price);

        //使用成员方法
        p.call();
        p.sendMessage();
    }
}
```
> [!note] 注
> 
在Java中，每个`.java`文件只能有一个`public`类，且这个类的名称必须与文件名相同。这是Java编译器的要求，以确保源代码的组织结构清晰和一致。

  在一个`.java`文件中，你可以定义多个非`public`类（即默认访问级别的类或者`private`、`protected`类）。这些类可以在同一个包内被访问和使用，但是它们不能被其他包访问（除非它们被声明为`protected`且其他类是它们的子类）。

  所以，你不能在一个`.java`文件中定义多个`public`类，因为这将违反Java编译器的规则。如果你需要定义多个公共类，你应该为每个类创建一个单独的`.java`文件。
