---
date created: 2023-09-26 17:36
tags:
  - "#字符串比较"
  - "#equals方法使用"
  - 遍历字符串
  - StringBuilder使用方法
  - StringJoiner使用方法
date updated: 2023-09-26 17:37
---

### 1.String类概述

​ String 类代表字符串，Java 程序中的所有字符串文字（例如“abc”）都被实现为此类的实例。也就是说，Java 程序中所有的双引号字符串，都是 String 类的对象。String 类在 java.lang 包下，所以使用的时候不需要导包！

### 2.String类的特点

- <mark style="background: #BBFABBA6;">字符串不可变</mark>，它们的值在创建后不能被更改
- 虽然 String 的值是不可变的，但是它们可以被共享
- 字符串效果上相当于字符数组( char[] )，但是底层原理是字节数组( byte[] )
- 示例代码

```java
public class StringDemo01 {
    public static void main(String[] args) {
        //public String()：创建一个空白字符串对象，不含有任何内容
        String s1 = new String();
        System.out.println("s1:" + s1);

        //public String(char[] chs)：根据字符数组的内容，来创建字符串对象
        char[] chs = {'a', 'b', 'c'};
        String s2 = new String(chs);
        System.out.println("s2:" + s2);

        //public String(byte[] bys)：根据字节数组的内容，来创建字符串对象
        byte[] bys = {97, 98, 99};
        String s3 = new String(bys);
        System.out.println("s3:" + s3);

        //String s = “abc”;	直接赋值的方式创建字符串对象，内容就是abc
        String s4 = "abc";
        System.out.println("s4:" + s4);
    }
}
```

*运行结果
s1:
s2:abc
s3:abc
s4:abc  *

---

### 3.创建字符串对象两种方式的区别

- 通过<font color="#f79646">构造方法</font>创建

  ​ 通过 new 创建的字符串对象，每一次 new 都会申请一个内存空间，<mark style="background: #BBFABBA6;">虽然内容相同，但是地址值不同</mark>

- 直接<font color="#4f81bd">赋值方式</font>创建

  ​ 以“”方式给出的字符串，只要字符序列相同(顺序和大小写)，无论在程序代码中出现几次，JVM 都只会建立一个 String 对象，并在字符串池中维护

---

### 4.字符串的比较    #字符串比较

#### 4.1    == 号的作用

- 比较<font color="#d99694">基本数据</font>类型：比较的是<mark style="background: #3BA9FFA6;">具体的值</mark>
- 比较<font color="#d99694">引用数据</font>类型：比较的是<mark style="background: #BBFABBA6;">对象地址值</mark>   

*例1*  
```java
String s1 = "abc";  
String s2 = "a";  
String s3 = s2 + "bc";  
System.out.println(s1 == s3);
```  
*运行结果  
false*   
**注：主要看String是否有拼接变量，如果有变量实际上就是new出来一个堆空间，s1,s3地址不同**    

*例2*  
```java
String s1 = "abc";  
String s3 = "a" + "bc";  
System.out.println(s1 == s3);
```  
*运行结果 
True*   

-------


#### 4.2 equals方法的作用    #equals方法使用

- 方法介绍

  ```java
  public boolean equals(String s)     比较两个字符串内容是否相同、区分大小写

  public boolean equalsIgnoreCase(0)  比较两个字符串内容是否相同、不区分大小写
  ```
- 示例代码

  ```java
  public class StringDemo02 {
      public static void main(String[] args) {
          //构造方法的方式得到对象
          char[] chs = {'a', 'b', 'c'};
          String s1 = new String(chs);
          String s2 = new String(chs);

          //直接赋值的方式得到对象
          String s3 = "abc";
          String s4 = "abc";

          //比较字符串对象地址是否相同
          System.out.println(s1 == s2);
          System.out.println(s1 == s3);
          System.out.println(s3 == s4);
          System.out.println("--------");

          //比较字符串内容是否相同
          System.out.println(s1.equals(s2));
          System.out.println(s1.equals(s3));
          System.out.println(s3.equalsIgnoreCase(s4));
      }
  }
  ```

---

#### 4.3 遍历字符串  #遍历字符串

_**案例需求**_
​ 键盘录入一个字符串，使用程序实现在控制台遍历该字符串

_示例代码_

```java
public static void main(String[] args) {  
    Scanner sc = new Scanner(System.in);  
    String s = sc.next();  
    for (int i = 0; i < s.length(); i++) {  
        **char c = s.charAt(i);**  
        System.out.println(c);  
    }
}
```

---

### 5.StringBuilder #StringBuilder使用方法

_StringBuilder 可以<font color="#95b3d7">看成是一个容器，创建之后里面的内容是可变的</font>。
当我们在拼接字符串和反转字符串的时候会使用到_

_示例代码_

```java
public class StringBuilderDemo3 {
    public static void main(String[] args) {
        //1.创建对象
        StringBuilder sb = new StringBuilder("abc");

        //2.添加元素
        sb.append(1);
        sb.append(2.3);
        sb.append(true);

        //反转
        sb.reverse();

        //获取长度
        int len = sb.length();
        System.out.println(len);

        //打印对象不是地址值而是属性值。
        System.out.println(sb);
    }
}
```

```java
public class StringBuilderDemo4 {
    public static void main(String[] args) {
        //1.创建对象
        StringBuilder sb = new StringBuilder();

        //2.添加字符串
        sb.append("aaa").append("bbb").append("ccc").append("ddd");

        System.out.println(sb);//aaabbbcccddd

        //3.再把StringBuilder变回字符串
        String str = sb.toString();
        System.out.println(str);//aaabbbcccddd

    }
}
```

**判断是否对称字符串**

```java
 //2.反转键盘录入的字符串
	String result = new StringBuilder().append(str).reverse().toString();
```

_拼接字符串_

```java
 public static String arrToString(int[] arr){
        StringBuilder sb = new StringBuilder();
        sb.append("[");

        for (int i = 0; i < arr.length; i++) {
            if(i == arr.length - 1){
                sb.append(arr[i]);
            }else{
                sb.append(arr[i]).append(", ");
            }
        }
        sb.append("]");

        return sb.toString();
    }
```

---

### 6. StringJoiner #StringJoiner使用方法

- StringJoiner跟StringBuilder一样，也可以看成是一个容器，创建之后里面的内容是可变的。
- 作用：提高字符串的操作效率，而且代码编写特别简洁，但是目前市场上很少有人用。

_示例代码_

```java
//1.创建一个对象，并指定中间的间隔符号
StringJoiner sj = new StringJoiner("---");
//2.添加元素
sj.add("aaa").add("bbb").add("ccc");
//3.打印结果
System.out.println(sj);//aaa---bbb---ccc
```

```java
//1.创建对象
StringJoiner sj = new StringJoiner(", ","[","]");
//2.添加元素
sj.add("aaa").add("bbb").add("ccc");
int len = sj.length();
System.out.println(len);//15
//3.打印
System.out.println(sj);//[aaa, bbb, ccc]
String str = sj.toString();
System.out.println(str);//[aaa, bbb, ccc]
```

---

## 关于字符串的小扩展：

1. 字符串存储的内存原理

   String s = “abc”；直接赋值

   特点：

   ​ 此时字符串abc是存在字符串常量池中的。

   ​ 先检查字符串常量池中有没有字符串abc，如果有，不会创建新的，而是直接复用。如果没有abc，才会创建一个新的。

   所以，直接赋值的方式，代码简单，而且节约内存。

2. new出来的字符串

   看到new关键字，一定是在堆里面开辟了一个小空间。

   String s1 = new String（“abc”）；

   String s2 = “abc”；

   s1记录的是new出来的，在堆里面的地址值。

   s2是直接赋值的，所以记录的是字符串常量池中的地址值。

3. == 号比较的到底是什么？

   如果比较的是基本数据类型：比的是具体的数值是否相等。

   如果比较的是引用数据类型：比的是地址值是否相等。

   结论：== 只能用于比较基本数据类型。不能比较引用数据类型。
