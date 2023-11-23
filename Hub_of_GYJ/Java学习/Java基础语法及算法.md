---
date created: 2023-09-20 18:36
tags:
  - this关键字
  - 字符串比较
  - static静态变量
---

## IDEA中写Java

---

**格式化代码 Ctrl+Shift+ ,**
**生成JavaBean：Alt+Fn+Insert**
**自动生成左边的生成变量：Ctrl +Alt +V**  
**传递参数提示：Ctrl+P**  
**批量修改:Shift+F6** 

---

_创建键盘录入_

```java
Scanner sc = new Scanner(System.in);//创建键盘录入对象  
System.out.println("请输入一数字");  
int i = sc.nextInt();  
System.out.println(i);
```

---

_**数组的静态初始化和动态初始化**_

```java
int[] arr=new int[]{0};//数组的静态初始化(完整模式)  
int[] arr1={0};//简写模式  
int[] arr3=new int[数组长度];//数组的动态初始化  
arr.length;    //数组长度（直接调用）  
arr.fori;      //idea快速遍历数组
```

---

**动态数组输入数据**

```java
int[] arr=new int[5];        // 动态数组初始化输入数据  
    Scanner sc = new Scanner(System.in);//创建键盘录入对象  
    for (int i = 0; i < arr.length; i++) {  
        arr[i]=sc.nextInt();  
    } 
	 for (int i = 0; i < arr.length; i++) {  
        System.out.print(arr[i]+" ");  
}
```

---

**生成10个1~100之间的随机数

```java
Random r=new Random();  
int number= r.nextInt(100)+1;
```

---

算法：随机排列数组中元素

```java
int[] arr = {1, 2, 3, 4, 5};  
Random r = new Random();  
int index = r.nextInt(arr.length)+1;  
for (int i = 0; i < arr.length; i++) {  
    int temp;  
    temp = arr[i];  
    arr[i] = index;  
    index = temp;  
    System.out.print(arr[i]+" ");
```

---

## this 关键字的使用

- <mark style="background: #BBFABBA6;">成员变量</mark>和<mark style="background: #BBFABBA6;">局部变量</mark>
  - _**默认采用就近原则 （无this）**_
- **代码示例**
  - (区分了成员变量和局部变量) #this关键字

![](/Pictures/this关键字的使用.jpg)

---

### **字符串查找**  

在Java中，= =运算符用于比较两个对象的引用是否相等，也就是它们是否指向同一个对象1。而<mark style="background: #FFB86CA6;">equals()方法</mark>用于比较两个字符串的内容是否相等。 #字符串比较
[[String 类、StringBuilder类]]
_示例代码_

```java
public static void main(String[] args) {  
    Scanner sc = new Scanner(System.in);  
    String[] arr = {"张三", "张三丰", "张无忌", "王二麻子", "张富贵"};  
    String name = sc.next();  
    for (int i = 0; i < arr.length; i++) { 
         //字符串比较 （如下）
        if (arr[i].equals(name)) {  
            System.out.println(name + "在数组的第" + (i + 1) + "个位置");  
            break;  
        }  
    }  
}
```
```ad-note
title: 用法
比较字符串中的内容是否完全相等：boolen restult=s1.equals(s2)
比较字符串中的内容是否相等，忽略大小写：boolen result=s1.equalsIgnoreCase(s2)
```
=================================================================
## *Static关键字*  #static静态变量
### 静态变量及其访问  

**定义**
有static修饰成员变量，说明这个成员变量是属于类的，这个成员变量称为**类变量**或者**静态成员变量**。 直接用 类名访问即可。因为类只有一个，所以静态成员变量在内存区域中也只存在一份。所有的对象都可以共享这个变量。（<font color="#c3d69b">static修饰就是默认值</font>）

**定义格式**
```java
修饰符 static 数据类型 变量名 = 初始值；
```  

**举例**
```java
public class Student {
    public static String teacherName="hanli";//属于类，只有一份
    // .....
}
```   

```java
public static void  main(String[] args){
    System.out.println(Student.teacherName); // hanli
    Student.teacherName = "南宫婉";
    System.out.println(Student.teacherName); // 南宫婉
}
```   

###   静态方法及其访问   
**定义**  
与静态成员变量一样，静态方法也是直接通过**类名.方法名称**即可访问。  
**举例**

```java
public class Student{
    public static void study(){
        System.out.println("凡人修仙传");   
    }
}
```   
-----------------------
